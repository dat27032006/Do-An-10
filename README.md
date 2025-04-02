using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace Cach2
{
    public partial class Form1 : Form
    {
        private TextBox txtInput;
        private Button btnCopy;
        private Button btnPaste;
        private ListBox lstClipboard;
        private Stack<string> clipboardStack = new Stack<string>();
        public Form1()
        {
            InitializeComponent();
        }

        private void Form1_Load(object sender, EventArgs e)
        {
            clipboardStack.Clear();
            this.Activate(); // Đảm bảo form có focus
            this.Focus();
        }

        // Sự kiện Copy
        private void btnCopy_Click(object sender, EventArgs e)
        {
            string text = txtInput.Text.Trim();
            if (!string.IsNullOrEmpty(text))
            {
                clipboardStack.Push(text);
                lstClipboard.Items.Insert(0, text);
                txtInput.Clear();
            }
            else
            {
                MessageBox.Show("Vui lòng nhập văn bản để copy!", "Thông báo", MessageBoxButtons.OK, MessageBoxIcon.Warning);
            }
        }

        // Sự kiện Paste
        private void btnPaste_Click(object sender, EventArgs e)
        {
            if (clipboardStack.Count > 0)
            {
                string text = clipboardStack.Pop();
                txtInput.Text = text;
                lstClipboard.Items.RemoveAt(0);
            }
            else
            {
                MessageBox.Show("Clipboard trống!", "Thông báo", MessageBoxButtons.OK, MessageBoxIcon.Warning);
            }
        }
         
        [STAThread]
        public static void Main()
        {
            Application.EnableVisualStyles();
            Application.SetCompatibleTextRenderingDefault(false);
            Application.Run(new Form1());
        }
    }
}

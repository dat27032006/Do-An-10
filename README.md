Form1.cs
using System;
using System.Collections.Generic;
using System.Windows.Forms;

namespace thử
{
    public partial class Form1 : Form
    {

        private Stack<string> clipboardStack = new Stack<string>();
        public Form1()
        {
            InitializeComponent();
        }
        public void Form1_Load(object sender,EventArgs e)
        {
            clipboardStack.Clear();          
        }

        private void btnCopy(object sender, EventArgs e)
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

        private void btnPaste(object sender, EventArgs e)
        {
            if (clipboardStack.Count > 0)
            { 
                string text = clipboardStack.Pop();
                txtInput.Text = text;
                lstClipboard.Items.RemoveAt(0);
            }
        }
    }
}

Form1.Designer.cs

namespace Cach2
{
    partial class Form1
    {
        /// <summary>
        /// Required designer variable.
        /// </summary>
        private System.ComponentModel.IContainer components = null;

        /// <summary>
        /// Clean up any resources being used.
        /// </summary>
        /// <param name="disposing">true if managed resources should be disposed; otherwise, false.</param>
        protected override void Dispose(bool disposing)
        {
            if (disposing && (components != null))
            {
                components.Dispose();
            }
            base.Dispose(disposing);
        }

        #region Windows Form Designer generated code

        /// <summary>
        /// Required method for Designer support - do not modify
        /// the contents of this method with the code editor.
        /// </summary>
        private void InitializeComponent()
        {
            this.lstClipboard = new System.Windows.Forms.ListBox();
            this.txtInput = new System.Windows.Forms.TextBox();
            this.button1 = new System.Windows.Forms.Button();
            this.button2 = new System.Windows.Forms.Button();
            this.SuspendLayout();
            // 
            // lstClipboard
            // 
            this.lstClipboard.FormattingEnabled = true;
            this.lstClipboard.ItemHeight = 20;
            this.lstClipboard.Location = new System.Drawing.Point(13, 133);
            this.lstClipboard.Name = "lstClipboard";
            this.lstClipboard.Size = new System.Drawing.Size(457, 184);
            this.lstClipboard.TabIndex = 0;
            // 
            // txtInput
            // 
            this.txtInput.Location = new System.Drawing.Point(12, 25);
            this.txtInput.Name = "txtInput";
            this.txtInput.Size = new System.Drawing.Size(456, 26);
            this.txtInput.TabIndex = 1;
            // 
            // button1
            // 
            this.button1.Location = new System.Drawing.Point(13, 75);
            this.button1.Name = "button1";
            this.button1.Size = new System.Drawing.Size(125, 43);
            this.button1.TabIndex = 2;
            this.button1.Text = "Copy";
            this.button1.UseVisualStyleBackColor = true;
            this.button1.Click += new System.EventHandler(this.btnCopy);
            // 
            // button2
            // 
            this.button2.Location = new System.Drawing.Point(180, 75);
            this.button2.Name = "button2";
            this.button2.Size = new System.Drawing.Size(125, 43);
            this.button2.TabIndex = 3;
            this.button2.Text = "Paste";
            this.button2.UseVisualStyleBackColor = true;
            this.button2.Click += new System.EventHandler(this.btnPaste);
            // 
            // Form1
            // 
            this.AutoScaleDimensions = new System.Drawing.SizeF(9F, 20F);
            this.AutoScaleMode = System.Windows.Forms.AutoScaleMode.Font;
            this.ClientSize = new System.Drawing.Size(481, 334);
            this.Controls.Add(this.button2);
            this.Controls.Add(this.button1);
            this.Controls.Add(this.txtInput);
            this.Controls.Add(this.lstClipboard);
            this.Name = "Form1";
            this.Text = "Form1";
            this.ResumeLayout(false);
            this.PerformLayout();

        }

        #endregion

        private System.Windows.Forms.ListBox lstClipboard;
        private System.Windows.Forms.TextBox txtInput;
        private System.Windows.Forms.Button button1;
        private System.Windows.Forms.Button button2;
    }
}

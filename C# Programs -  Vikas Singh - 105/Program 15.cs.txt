// 15. Implement the concept of file handling to read XML file and display all the values in a read only Form.
using System;
using System.Windows.Forms;
using System.Xml;

public class XMLReaderForm : Form
{
    TextBox txtRegNo, txtName, txtAge, txtClass;
    
    public XMLReaderForm()
    {
        this.Text = "Student Details (Read-Only)";
        this.Size = new System.Drawing.Size(300, 250);

        Label lblRegNo = new Label() { Text = "Reg No:", Top = 20, Left = 20 };
        txtRegNo = new TextBox() { Top = 20, Left = 100, ReadOnly = true };

        Label lblName = new Label() { Text = "Name:", Top = 50, Left = 20 };
        txtName = new TextBox() { Top = 50, Left = 100, ReadOnly = true };

        Label lblAge = new Label() { Text = "Age:", Top = 80, Left = 20 };
        txtAge = new TextBox() { Top = 80, Left = 100, ReadOnly = true };

        Label lblClass = new Label() { Text = "Class:", Top = 110, Left = 20 };
        txtClass = new TextBox() { Top = 110, Left = 100, ReadOnly = true };

        this.Controls.Add(lblRegNo);
        this.Controls.Add(txtRegNo);
        this.Controls.Add(lblName);
        this.Controls.Add(txtName);
        this.Controls.Add(lblAge);
        this.Controls.Add(txtAge);
        this.Controls.Add(lblClass);
        this.Controls.Add(txtClass);

        LoadDataFromXML();
    }

    private void LoadDataFromXML()
    {
        XmlDocument doc = new XmlDocument();
        doc.Load("data.xml");

        txtRegNo.Text = doc.SelectSingleNode("Student/RegNo").InnerText;
        txtName.Text = doc.SelectSingleNode("Student/Name").InnerText;
        txtAge.Text = doc.SelectSingleNode("Student/Age").InnerText;
        txtClass.Text = doc.SelectSingleNode("Student/Class").InnerText;
    }

    [STAThread]
    static void Main()
    {
        Application.Run(new XMLReaderForm());
    }
}

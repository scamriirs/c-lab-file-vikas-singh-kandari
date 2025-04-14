// 14. Create a windows form with registration number, name, age, class and other details. 
using System;
using System.Windows.Forms;

public class RegistrationForm : Form
{
    TextBox txtRegNo, txtName, txtAge, txtClass;
    Button btnRegister;

    public RegistrationForm()
    {
        this.Text = "Student Registration Form";
        this.Size = new System.Drawing.Size(350, 300);

        Label lblRegNo = new Label() { Text = "Registration No:", Top = 20, Left = 20 };
        txtRegNo = new TextBox() { Top = 20, Left = 150 };

        Label lblName = new Label() { Text = "Name:", Top = 50, Left = 20 };
        txtName = new TextBox() { Top = 50, Left = 150 };

        Label lblAge = new Label() { Text = "Age:", Top = 80, Left = 20 };
        txtAge = new TextBox() { Top = 80, Left = 150 };

        Label lblClass = new Label() { Text = "Class:", Top = 110, Left = 20 };
        txtClass = new TextBox() { Top = 110, Left = 150 };

        btnRegister = new Button() { Text = "Register", Top = 150, Left = 150 };
        btnRegister.Click += new EventHandler(RegisterStudent);

        this.Controls.Add(lblRegNo);
        this.Controls.Add(txtRegNo);
        this.Controls.Add(lblName);
        this.Controls.Add(txtName);
        this.Controls.Add(lblAge);
        this.Controls.Add(txtAge);
        this.Controls.Add(lblClass);
        this.Controls.Add(txtClass);
        this.Controls.Add(btnRegister);
    }

    private void RegisterStudent(object sender, EventArgs e)
    {
        MessageBox.Show($"Registered Successfully\nReg No: {txtRegNo.Text}\nName: {txtName.Text}\nAge: {txtAge.Text}\nClass: {txtClass.Text}", "Success");
    }

    [STAThread]
    static void Main()
    {
        Application.Run(new RegistrationForm());
    }
}

# Administracia
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Data.SqlClient;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Администрация
{
    public partial class Авторизация : Form
    {
        public Авторизация()
        {
            InitializeComponent();
        }

        private void Button1_Click(object sender, EventArgs e)
        {
            if (comboBox1.SelectedIndex == 0)
            {
                SqlConnection con = new SqlConnection(@"Data Source=LAPTOP-C3OCCNTR;Initial Catalog=Administracia;Integrated Security=True");
                SqlDataAdapter sda = new SqlDataAdapter("Select * From Sotrudnik where id='" + textBox1.Text + "'and Parol='" + textBox2.Text + "'", con);
                DataTable dt = new DataTable();
                sda.Fill(dt);
                
                    if (dt.Rows.Count == 1)
                {
                    MessageBox.Show("Вы успешно авторизировались");
                    ПрофильСотрудника профильСотрудника = new ПрофильСотрудника();
                    профильСотрудника.textBox1.Text = this.dataGridView2.CurrentRow.Cells[0].Value.ToString();
                    профильСотрудника.textBox2.Text = this.dataGridView2.CurrentRow.Cells[1].Value.ToString();
                    профильСотрудника.textBox3.Text = this.dataGridView2.CurrentRow.Cells[2].Value.ToString();
                    профильСотрудника.textBox4.Text = this.dataGridView2.CurrentRow.Cells[3].Value.ToString();
                    профильСотрудника.textBox5.Text = this.dataGridView2.CurrentRow.Cells[4].Value.ToString();
                    профильСотрудника.textBox6.Text = this.dataGridView2.CurrentRow.Cells[5].Value.ToString();
                    профильСотрудника.Show();
                    this.Hide();
                    профильСотрудника.Show();
                    this.Hide();
                }
                else{
                    MessageBox.Show(string.Format("{0}\n{1}", "Ошибка входа", "Попробуйте снова!"), "Авторизация");
                }
            }
            if (comboBox1.SelectedIndex == 1)
            {
                SqlConnection con = new SqlConnection(@"Data Source=LAPTOP-C3OCCNTR;Initial Catalog=Administracia;Integrated Security=True");
                SqlDataAdapter sda = new SqlDataAdapter("Select * From Rol where id='" + textBox1.Text + "'and Parol='" + textBox2.Text + "'", con);
                DataTable dt = new DataTable();
                sda.Fill(dt);
                if (dt.Rows.Count == 1)
                {
                    MessageBox.Show("Вы успешно авторизировались");
                    Профиль профиль = new Профиль();
                    профиль.textBox4.Text = this.dataGridView1.CurrentRow.Cells[0].Value.ToString();
                    профиль.textBox1.Text = this.dataGridView1.CurrentRow.Cells[1].Value.ToString();
                    профиль.textBox2.Text = this.dataGridView1.CurrentRow.Cells[2].Value.ToString();
                    профиль.textBox3.Text = this.dataGridView1.CurrentRow.Cells[3].Value.ToString();
                    профиль.textBox6.Text = this.dataGridView1.CurrentRow.Cells[4].Value.ToString();
                    профиль.textBox7.Text = this.dataGridView1.CurrentRow.Cells[5].Value.ToString();
                    профиль.Show();
                    this.Hide();
                }
                else
                {
                    MessageBox.Show(string.Format("{0}\n{1}", "Ошибка входа", "Попробуйте снова!"), "Авторизация");
                }
            }
            if (comboBox1.SelectedIndex == 2)
            {
                SqlConnection con = new SqlConnection(@"Data Source=LAPTOP-C3OCCNTR;Initial Catalog=Administracia;Integrated Security=True");
                SqlDataAdapter sda = new SqlDataAdapter("Select * From Rol where id='" + textBox1.Text + "'and Parol='" + textBox2.Text + "'", con);
                DataTable dt = new DataTable();
                sda.Fill(dt);
                if (dt.Rows.Count == 1)
                {
                    MessageBox.Show("Вы успешно авторизировались");
                    ПрофильСотрудника профильСотрудника = new ПрофильСотрудника();
                    профильСотрудника.textBox1.Text = this.dataGridView1.CurrentRow.Cells[0].Value.ToString();
                    профильСотрудника.textBox2.Text = this.dataGridView1.CurrentRow.Cells[1].Value.ToString();
                    профильСотрудника.textBox3.Text = this.dataGridView1.CurrentRow.Cells[2].Value.ToString();
                    профильСотрудника.textBox4.Text = this.dataGridView1.CurrentRow.Cells[3].Value.ToString();
                    профильСотрудника.textBox5.Text = this.dataGridView1.CurrentRow.Cells[4].Value.ToString();
                    профильСотрудника.textBox6.Text = this.dataGridView1.CurrentRow.Cells[5].Value.ToString();
                    профильСотрудника.Show();
                    this.Hide();
                }
            }
        }

            private void Button2_Click(object sender, EventArgs e)
            {
                Главная form1 = new Главная();
                form1.Show();
                this.Hide();
            }

        private void Авторизация_Load(object sender, EventArgs e)
        {
            // TODO: данная строка кода позволяет загрузить данные в таблицу "administraciaDataSet3.Sotrudnik". При необходимости она может быть перемещена или удалена.
            this.sotrudnikTableAdapter.Fill(this.administraciaDataSet3.Sotrudnik);
            // TODO: данная строка кода позволяет загрузить данные в таблицу "administraciaDataSet3.Grahdan". При необходимости она может быть перемещена или удалена.
            this.grahdanTableAdapter.Fill(this.administraciaDataSet3.Grahdan);

            
        }

        private void button3_Click(object sender, EventArgs e)
        {
            textBox2.Enabled = false;
            textBox4.Enabled = false;
            button1.Enabled = false;
        }

        private void pictureBox2_Click(object sender, EventArgs e)
        {

            Random rnd = new Random();
            Text = String.Empty;
            string ALF = "7@ABFGcdsw";
            for (int i = 0; i < 8; ++i)
                Text += ALF[rnd.Next(ALF.Length)];
            MessageBox.Show(Text);

        }
    }
}


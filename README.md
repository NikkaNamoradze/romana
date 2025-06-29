დავალება 1
image.png

image.png


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace WinFormsApp1
{
    internal class Klasi
    {
        private int cvladi;

        public int Tviseba{
            get { return cvladi; }
            set{
                if (value % 15 == 0 && value > 555)
                {
                    cvladi = value;
                }
            }
        }
    }
}


namespace WinFormsApp1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            Klasi klasi = new Klasi();

            klasi.Tviseba = int.Parse(textBox1.Text);

            label1.Text = klasi.Tviseba.ToString();


        }
    }
}





დავალება 2

image.png

using System.Data;
using System.Data.SqlClient;

namespace WinFormsApp2
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void dataGridView1_CellContentClick(object sender, DataGridViewCellEventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {

            SqlConnection con_shekveta = new SqlConnection("server=BTU403-15;database=Shekveta;uid=sa;pwd=1");
            con_shekveta.Open();

            SqlDataAdapter adapter = new SqlDataAdapter("SELECT * FROM Shemkveti", con_shekveta);

            DataSet dataSet = new DataSet();

            adapter.Fill(dataSet, "Shemkveti");

            con_shekveta.Close();

            DataView filtered = new DataView(dataSet.Tables["Shemkveti"]);
            filtered.RowFilter = "qalaqi = 'ზუგდიდი' AND iuridiuli_fizikuri = 'ორდინარული'";

            dataGridView1.DataSource = filtered;



        }
    }
}


დავალება 3
image.png


using System.Data.SqlClient;

namespace WinFormsApp3
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {

            SqlConnection conn = new SqlConnection("server=BTU403-15;database=Shekveta;uid=sa;pwd=1");
            conn.Open();

            SqlCommand comm_1 = conn.CreateCommand();
            comm_1.CommandText = "SELECT SUM(tanxa) FROM Xelshekruleba where shesruleba = 'არა' && visi_mizezit = 'შემსრულებლის' ";
            object countResult = comm_1.ExecuteScalar();
            label1.Text = countResult.ToString();

            conn.Close();
        
        }
    }
}


დავალება 4
image.png

namespace WinFormsApp4
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }


        private void button1_Click(object sender, EventArgs e)
        {

            int[] masivi = new int[20000];

            Random random = new Random();

            for (int i = 0; i < masivi.Length; i++)
            {
                masivi[i] = random.Next(0,60000);
            }

            var shedegi = from cvladi in masivi where cvladi > 25000 select cvladi;

           label1.Text = shedegi.Average().ToString();


        }
    }
}

დავალება 1
image.png
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace WinFormsApp5
{
    internal class Class1
    {
        private int cvladi;

        public int Tviseba
        {
            get
            {
                return cvladi;
            }
            set {
                if(value % 6 == 0 && value > 36)
                {
                    cvladi = value;
                }
            }
        }

    }
}

private void button1_Click(object sender, EventArgs e)
{

    Class1 class1 = new Class1();

    class1.Tviseba = int.Parse(textBox1.Text);

    label1.Text = class1.Tviseba.ToString();

}

დავალება 2
image.png

private void button3_Click(object sender, EventArgs e)
{
    SqlConnection conn = new SqlConnection("server=BTU-20; database=Shekveta; uid=sa; pwd=1");

    conn.Open();

    SqlDataAdapter adapter = new SqlDataAdapter("SELECT * FROM Personali", conn);

    DataSet ds = new DataSet();
    adapter.Fill(ds, "Personali");

    object minXelfasi = ds.Tables["Personali"].Compute("Min(xelfasi)", "ganyofileba = 'სამედიცინო'");
}

დავალება 3
image.png

private void button4_Click(object sender, EventArgs e)
{

    SqlConnection conn = new SqlConnection("server=BTU-20; database=Shekveta; uid=sa; pwd=1");

    conn.Open();

    SqlCommand command = conn.CreateCommand();
    command.CommandText = "UPDATE Personali SET xelfasi = xelfasi * 1.2 WHERE qalaqi = 'ბათუმი'";

    command.ExecuteNonQuery();
}


დავალება 4
image.png

private void button2_Click(object sender, EventArgs e)
{
    int[] masivi = new int[15000];

    Random random = new Random();

    for (int i = 0; i < masivi.Length; i++)
    {
        masivi[i] = random.Next(0, 55001);
    }
    var shedegi = (from cvladi in masivi where cvladi > 20000 select cvladi).Sum();

    label2.Text = shedegi.ToString();

}


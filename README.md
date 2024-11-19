# Lab-7
using System;
using System.Windows.Forms;

namespace CalculatorApp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private double Add(double a, double b) => a + b;
        private double Subtract(double a, double b) => a - b;
        private double Multiply(double a, double b) => a * b;
        private double Divide(double a, double b) => b != 0 ? a / b : 0;

        private void buttonCalculate_Click(object sender, EventArgs e)
        {
            double num1 = double.Parse(textBoxNum1.Text);
            double num2 = double.Parse(textBoxNum2.Text);
            string operation = comboBoxOperation.SelectedItem.ToString();
            double result = 0;

            switch (operation)
            {
                case "Add":
                    result = Add(num1, num2);
                    break;
                case "Subtract":
                    result = Subtract(num1, num2);
                    break;
                case "Multiply":
                    result = Multiply(num1, num2);
                    break;
                case "Divide":
                    result = Divide(num1, num2);
                    break;
            }

            labelResult.Text = $"Result: {result}";
        }
    }
}


//another code of calculter
// This example includes multiple buttons for addition, subtraction, multiplication, and division.
using System;
using System.Windows.Forms;

namespace SimpleGUICalculator
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void buttonAdd_Click(object sender, EventArgs e)
        {
            double num1 = double.Parse(textBoxNum1.Text);
            double num2 = double.Parse(textBoxNum2.Text);
            labelResult.Text = $"Result: {num1 + num2}";
        }

        private void buttonSubtract_Click(object sender, EventArgs e)
        {
            double num1 = double.Parse(textBoxNum1.Text);
            double num2 = double.Parse(textBoxNum2.Text);
            labelResult.Text = $"Result: {num1 - num2}";
        }

        private void buttonMultiply_Click(object sender, EventArgs e)
        {
            double num1 = double.Parse(textBoxNum1.Text);
            double num2 = double.Parse(textBoxNum2.Text);
            labelResult.Text = $"Result: {num1 * num2}";
        }

        private void buttonDivide_Click(object sender, EventArgs e)
        {
            double num1 = double.Parse(textBoxNum1.Text);
            double num2 = double.Parse(textBoxNum2.Text);
            labelResult.Text = num2 != 0 ? $"Result: {num1 / num2}" : "Error: Division by zero";
        }
    }
}



Square of First 10 Numbers
using System;
using System.Windows.Forms;

namespace SquareApp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void buttonCalculateSquares_Click(object sender, EventArgs e)
        {
            string result = "Squares of numbers 1 to 10:\n";
            for (int i = 1; i <= 10; i++)
            {
                result += $"Square of {i}: {i * i}\n";
            }
            labelSquares.Text = result;
        }
    }
}

Fahrenheit to Celsius Converter
using System;
using System.Windows.Forms;

namespace FahrenheitToCelsius
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void buttonConvert_Click(object sender, EventArgs e)
        {
            double fahrenheit = double.Parse(textBoxFahrenheit.Text);
            double celsius = (fahrenheit - 32) * 5 / 9;
            labelCelsius.Text = $"Celsius: {celsius}";
        }
    }
}


Factorial Calculator
using System;
using System.Windows.Forms;

namespace FactorialApp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private long Factorial(int n)
        {
            if (n <= 1) return 1;
            return n * Factorial(n - 1);
        }

        private void buttonCalculateFactorial_Click(object sender, EventArgs e)
        {
            int number = int.Parse(textBoxNumber.Text);
            long result = Factorial(number);
            labelResult.Text = $"Factorial: {result}";
        }
    }
}


 Countdown Timer
 using System;
using System.Windows.Forms;
using System.Threading.Tasks;

namespace CountdownApp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private async void buttonStartCountdown_Click(object sender, EventArgs e)
        {
            int seconds = int.Parse(textBoxSeconds.Text);
            for (int i = seconds; i >= 0; i--)
            {
                labelCountdown.Text = $"Time left: {i} seconds";
                await Task.Delay(1000);
            }
            MessageBox.Show("Time's up!");
        }
    }
}


 GUI Wall Clock
 using System;
using System.Windows.Forms;

namespace WallClockApp
{
    public partial class Form1 : Form
    {
        private Timer timer;

        public Form1()
        {
            InitializeComponent();
            timer = new Timer();
            timer.Interval = 1000; // 1 second
            timer.Tick += Timer_Tick;
            timer.Start();
        }

        private void Timer_Tick(object sender, EventArgs e)
        {
            labelDateTime.Text = DateTime.Now.ToString("F"); // Full date/time pattern
        }
    }
}


Photo Viewer
using System;
using System.IO;
using System.Linq;
using System.Windows.Forms;

namespace PhotoViewerApp
{
    public partial class Form1 : Form
    {
        private string[] imageFiles;
        private int currentIndex = 0;

        public Form1()
        {
            InitializeComponent();
        }

        private void buttonBrowse_Click(object sender, EventArgs e)
        {
            using (FolderBrowserDialog folderDialog = new FolderBrowserDialog())
            {
                if (folderDialog.ShowDialog() == DialogResult.OK)
                {
                    string folderPath = folderDialog.SelectedPath;
                    imageFiles = Directory.GetFiles(folderPath, "*.jpg")
                        .Concat(Directory.GetFiles(folderPath, "*.png"))
                        .ToArray();

                    if (imageFiles.Length > 0)
                    {
                        currentIndex = 0;
                        ShowImage();
                    }
                    else
                    {
                        MessageBox.Show("No images found in the selected folder.");
                    }
                }
            }
        }

        private void buttonNext_Click(object sender, EventArgs e)
        {
            if (imageFiles != null && imageFiles.Length > 0)
            {
                currentIndex = (currentIndex + 1) % imageFiles.Length;
                ShowImage();
            }
        }

        private void ShowImage()
        {
            pictureBox.ImageLocation = imageFiles[currentIndex];
        }
    }
}


TextBox Character Limit
using System;
using System.Windows.Forms;

namespace CharacterLimitApp
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            textBoxInput.MaxLength = 160; // Set the character limit
        }

        private void textBoxInput_TextChanged(object sender, EventArgs e)
        {
            labelCharacterCount.Text = $"{textBoxInput.Text.Length}/160 characters";
        }
    }
}


---
```

  _____ _ _        ____                              _
 |  ___(_) | ___  |  _ \ _ __ ___   ___ ___  ___ ___(_)_ __   __ _
 | |_  | | |/ _ \ | |_) | '__/ _ \ / __/ _ \/ __/ __| | '_ \ / _` |
 |  _| | | |  __/ |  __/| | | (_) | (_|  __/\__ \__ \ | | | | (_| |
 |_|   |_|_|\___| |_|   |_|  \___/ \___\___||___/___/_|_| |_|\__, |
                                                |___/
```

---

```cpp
#include <iostream>
#include <fstream>
#include <conio.h>
#include <string>
using namespace std;

class Person
{
public:
    string FirstName;
    string LastName;
    string ID;
    Person();
    void getInforamtion();
    void SaveData(const string &filePath);
};

Person::Person()
{
    FirstName = "0";
    LastName = "0";
    ID = "0";
}

void Person::getInforamtion()
{
    cout << "Enter The First Name  " << endl;
    getline(cin, FirstName);
    cout << "Enter The Last Name " << endl;
    getline(cin, LastName);
    cout << "Enter The Id " << endl;
    getline(cin, ID);
}
void Person::SaveData(const string &filePath)
{
    ofstream OutFile(filePath);
    if (!OutFile.is_open())
    {
        cerr << "Cant Open File " << endl;
    }
    OutFile << "Enter The First Name " << FirstName << endl;
    OutFile << "Enter The Last Name " << LastName << endl;
    OutFile << "Enter The Id " << ID << endl;
    OutFile.close();
}

int main()
{
    Person New_Person;
    New_Person.getInforamtion();
    New_Person.SaveData("D:\\test.txt");
    return 0;
}

```

---
```cpp
#include <iostream>
#include <fstream>
#include <conio.h>
using namespace std;
void main() {
    char ch;
    fstream file;
    char filename[20];
    cout << "Enter the name of the file: " << flush;
    cin >> filename;
    file.open(filename, ios::in);
    while (true) {
        file >> ch;
        if (file.fail())
            break;
        cout << ch;
    }
    file.close();
    _getch();
}
```

---

```cpp
#include <iostream>
#include <fstream>
#include <conio.h>
using namespace std;
void WriteToFile(const string &PathFile)
{
    ofstream outputFile(PathFile, ios::out);
    if (!outputFile.is_open())
        cerr << "Erro To Open File " << PathFile << endl;
        return;
    string write;
    while (true)
    {
        getline(cin, write);
        outputFile << write << endl;
    }
    outputFile.close();
    cout << "Data Has Been Write " << endl;
}
//-----------
void ReadFromFile(const string &PathFile)
{
    ifstream inputfile(PathFile, ios::in);
    if (!inputfile.is_open())
        cerr << "Error Can Not Opent The File" << PathFile;
    string line;
    while (getline(cin,line))
    {
        cout << line << endl;
    }
}
//--------
int main()
{
    string pathfile = "PathFile.txt";
    WriteToFile(pathfile);
    ReadFromFile(pathfile);
    _getch();
}
```

---
```cpp
#include <iostream>
#include <fstream>
#include <cstring>
using namespace std;

struct clientData
{
    int acctNum;
    char FirstName[20];
    char LastName[20];
};

int main()
{
    clientData client;
    fstream file("D:\Hunters.dat", ios::in | ios::out | ios::binary);

    if (!file.is_open())
        cerr << "File Can Not Open" << endl;

    else
    {
        while (true)
        {
            char action;
            cout << "Enter 'W' to Write, 'R' to Read, 'q' to Exit: " << endl;
            cin >> action;
            if (action == 'q')
                break;

            if (action == 'w')
            {
                cout << "Enter Account Number from (1 => 100): ";
                cin >> client.acctNum;
                cout << "Enter First Name: ";
                cin >> client.FirstName;
                cout << "Enter Last Name: ";
                cin >> client.LastName;
                file.seekp((client.acctNum - 1) * sizeof(clientData), ios::beg);
                file.write(reinterpret_cast<const char *>(&client), sizeof(clientData));
            }

            else if (action == 'r')
            {
                cout << "Enter Account number to Read (1 => 100): ";
                int Id;
                cin >> Id;
                file.seekg((Id - 1) * sizeof(clientData), ios::beg);
                file.read(reinterpret_cast<char *>(&client), sizeof(clientData));
                cout << "First Name: " << client.FirstName << endl;
                cout << "Last Name: " << client.LastName << endl;
                cout << "Balance: " << client.balance << endl;
            }
        }
    }
}

```

---
```cs
// Image Show
  private void button1_Click(object sender, EventArgs e)
        {
            openFileDialog1.Filter = "Image Files (*.bmp; *.png; *.jpg)| *.bmp; *.png; *.jpg";
            if (openFileDialog1.ShowDialog()==DialogResult.OK)
            {
                pictureBox1.Image = Image.FromFile(openFileDialog1.FileName);
            }
        }

        // Save Data
        private void button2_Click(object sender, EventArgs e)
        {
            DataRow r = ds.Tables["t1"].NewRow();
            r["id"] = int.Parse(textBox1.Text);
            r["name"] = textBox2.Text;
            MemoryStream ms = new MemoryStream();
            pictureBox1.Image.Save(ms,ImageFormat.Bmp);
            byte[] arr = ms.ToArray();
            r["images"] = arr;
            ds.Tables["t1"].Rows.Add(r);
            da.Update(ds, "t1");
            clear();
        }

		// FUNCTION Clear all information
        void clear()
        {
            textBox1.Clear();
            textBox2.Clear();
            pictureBox1.Image.Dispose();

        }
		//View button
        private void button3_Click(object sender, EventArgs e)
        {
            foreach (DataRow r in ds.Tables["t1"].Rows)
            {
                if (Convert.ToInt32(r["id"])==int.Parse(textBox1.Text))
                {
                    textBox2.Text = Convert.ToString(r["name"]);
                    byte[] arr = (byte[])(r["images"]);
                    MemoryStream ms = new MemoryStream(arr);
                    Bitmap x = new Bitmap(ms);
                    pictureBox1.Image = x;

                }
            }
        }
		// View Full Button
        private void button4_Click(object sender, EventArgs e)
        {
            dataGridView1.DataSource = ds.Tables["t1"];
        }
		// To Exit The Program
        private void button5_Click(object sender, EventArgs e)
        {
            System.Environment.Exit(0);
        }
    }
}

```

---
```cs
using System;

namespace Root
{
    class Program
    {
        // دالة هاشينج بسيطة
        static int SimpleHash(string s, string[] arr)
        {
            int index = 0;
            foreach (char c in s)
            {
                index += (int)c;
            }
            return index % arr.Length;
        }

        // دالة هاشينج محسنة
        static int BetterHash(string s, string[] arr)
        {
            int index = 0;
            foreach (char c in s)
            {
                index = (index * 37) + (int)c;
            }
            index %= arr.Length;
            if (index < 0)
            {
                index += arr.Length;
            }
            return index;
        }

        static void Main(string[] args)
        {
            string[] arr = {"Sung Jin-Woo","Thomas Andre"};

            string testString = "example";

            int simpleHashIndex = SimpleHash(testString, arr);
            int betterHashIndex = BetterHash(testString, arr);

            Console.WriteLine($"Simple hash index for \"{testString}\": {simpleHashIndex}");
            Console.WriteLine($"Better hash index for \"{testString}\": {betterHashIndex}");
        }
    }
}

```

---
###### Q.1.Write a program used to list contents of a file using C++ stream.
---
###### Q.2. Write a program that contains two functions: the first is used to write data into a sequential file, and the second is used to read data from a file using a C++ stream.
---
###### Q.3.Write a C# Console Application that defines a function to calculate a hash index of a string using a custom hash algorithm.
---
###### Q.4.Create a C# WinForms application that allows the user to load and display an image in a `PictureBox`.
---
###### Q.6.Create a C# WinForms form that allows the user to enter `ID`, `Name`, and upload an image.
---
###### Q.7.Write a C# WinForms application that allows the user to search for a record by ID.
---
###### Q.8.A C++ application for storing client data that reads and writes data at a specified location using `seekg` and `seekp`.
---

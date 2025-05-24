# PRACTICAL 11
```cpp
#include <iostream>
#include <fstream>
using namespace std;

class Student {
public:
    int rollNo;
    char name[50];
    char studentClass[20];
    int year;
    float totalMarks;

    void input() {
        cout << "Enter Roll No: ";
        cin >> rollNo;
        cout << "Enter Name: ";
        cin.ignore();
        cin.getline(name, 50);
        cout << "Enter Class: ";
        cin.getline(studentClass, 20);
        cout << "Enter Year: ";
        cin >> year;
        cout << "Enter Total Marks: ";
        cin >> totalMarks;
    }

    void display() {
        cout << "\nRoll No: " << rollNo;
        cout << "\nName: " << name;
        cout << "\nClass: " << studentClass;
        cout << "\nYear: " << year;
        cout << "\nTotal Marks: " << totalMarks << "\n";
    }
};

int main() {
    Student s[5];

    // Write to file
    ofstream fout("students.dat", ios::binary);
    for (int i = 0; i < 5; i++) {
        cout << "\nEnter details for student " << i + 1 << ":\n";
        s[i].input();
        fout.write((char*)&s[i], sizeof(s[i]));
    }
    fout.close();

    // Read from file
    ifstream fin("students.dat", ios::binary);
    cout << "\nStored Student Records:\n";
    for (int i = 0; i < 5; i++) {
        fin.read((char*)&s[i], sizeof(s[i]));
        s[i].display();
    }
    fin.close();

    return 0;
}

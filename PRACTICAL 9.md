# PRACTICAL 9
```CPP
#include <iostream>   
using namespace std; 

class Person { 
protected: 
   string name; 
   int age; 

public: 
   void input() { 
      cout << "Enter name and age: "; 
      cin >> name >> age; 
   }
   void display() { 
      cout << "Name: "<< name << ", Age: " << age << endl; 
   } 
}; 

class Student public Person { 
   string course; 

public: 
   void input() { 
      Person::input(); 
      cout << "Enter course: ";
      cin >> course; 
   } 
   void display() { 
      Person::display(); 
      cout << "Course: " << course << endl; 
   } 
}; 

class Employee public Person { 
   int salary;  
public: 
   void input() {
      Person::input(); 
      cout << "Enter salary: ";  
      cin >> salary; 
   }
   void display() { 
      Person::display(); 
      cout << "Salary: " << salary << endl;
   }
};

int main() { 
   Student s; 
   Employee e; 

   cout << "Enter student details:\n"; 
   s.input(); 

   cout << "Enter employee details:\n"; 
   e.input();
   
   cout << "\nStudent Details:\n"; 
   s.display();
   
   cout << "\nEmployee Details:\n"; 
   e.display();
   
   return 0; 
}

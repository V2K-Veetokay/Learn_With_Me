---
weight: 301
---

# Inheritance - Constructor

``` C++
#include <iostream>
#include <string>

using namespace std;

class Student {
    int roll;
    string name;
public:
    Student(int r, const string& n) : roll(r), name(n) {}

    virtual void display() {
        cout << "Student Result" << endl
             << "Name: " << name << endl
             << "Roll No. " << roll << endl;
    }
};

class Result : public Student {
    int marks;
public:
    Result(int r, const string& n, int m) : Student(r, n), marks(m) {}

    void show() {
        display();
        cout << "student marks: " << marks << endl << endl;
    }
};

int main() {
    Student s(12, "Monty");
    Result r(13, "shonty", 88);
    r.show();
    s.display();
    return 0;
}
```

## Output
```
Student Result
Name: shonty
Roll No. 13
student marks: 88

Student Result
Name: Monty
Roll No. 12
```
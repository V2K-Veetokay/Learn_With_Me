---
weight: 30
---

# Assignment


## Q-1: Employee BasicPay
Create a class Employee with basicpay as data member. Use constructors and destructor along with display() to display valuers of Employee object and calcGrossSal() method to find out the gross amount from the given formula grosssal= basicpay + DA + HRA where DA & HRA can be calculated as follows: - If basicpay is greater than or equal to 8000 DA is 20% of Basic Pay & HRA is 25% of Basic Pay, otherwise DA is 15% of Basic Pay & HRA is 20% of basicpay. Define calcTax() method to calculate the income tax of an employee using rate of tax is 20% of grosssal if it is less than 90000 otherwise tax is 25% of grosssal.

``` C++
#include<iostream>

using namespace std;

class Employee{
    unsigned int basicpay;
    public:
        Employee(){basicpay = 0;}
        Employee(unsigned int a){basicpay = a;}
        Employee(Employee &a){basicpay = a.basicpay;}
        ~Employee(){cout<<"Distroctor called"<<endl;}

        double calcGrossSal(){
            double DA, HRA;

            if (basicpay>=8000){
	            DA = 20.0; HRA = 25.0;
            } else {
		        DA = 15.0; HRA = 20.0;
            }
            DA = (DA*100.0)/basicpay;
            HRA = (HRA*100.0)/basicpay;

            return basicpay + DA + HRA;
        }

        double calcTax(){
            float taxRate;
            calcGrossSal()<90000 ? taxRate = 20.0 : taxRate = 25.0;
            return (calcGrossSal()*taxRate)/100.0;
        }

        void display(){
            cout<<"Basic Pay: "<<basicpay<<endl;
            cout<<"Gross Sale: "<<calcGrossSal()<<endl;
            cout<<"Tax: "<<calcTax()<<endl;
        }
};

int main(){
    Employee a(10000);
    a.display();
}
```

### Output
```
Basic Pay: 10000
Gross Sale: 10000.5
Tax: 2000.09
Distroctor called
```


## Q-2: Point 
 Write a program that uses a class called Point to model a point. Define three points, and have the user input values to two of them using getInfo() method. Then set the third point equal to the sum of the other two, and display the value of the new point using findSum() and show() methods of the class.

``` C++
#include<iostream>

using namespace std;

class Point{
    int a, b;
    public:
        Point(){a=b = 0;}
        Point(int a, int b){
            this->a = a;
            this->b = b;
        }
        Point(Point &a){
            this->a = a.a;
            this->b = a.b;
        }
        ~Point(){cout<<"Distroctor called"<<endl;}

        Point findSum(Point x){
            return Point(this->a+x.a, this->b+x.b);
        }

        void show(){
            cout<<a<<","<<b<<endl;
        }
};

int main(){
    int a, b;

    cout<<"First point: ";
    cin>>a>>b;
    Point a1(a,b);

    cout<<"\nSecond point: ";
    cin>>a>>b;
    Point a2(a,b);

    Point j = a1.findSum(a2);
    j.show();
}
```

### Output
```
First point: 
Second point: Distroctor called
6,8
Distroctor called
Distroctor called
Distroctor called
```


## Q-3: Matrix Multiplication
Write a program for Multiplication of the two matrixes and store it in another matrix. Display the new matrix using three functions one for input, second for multiplication with array as argument and display for output.

``` C++
#include <iostream>
using namespace std;

const int ROWS = 3;
const int COLS = 3;

template <typename T>
void input(T mat[ROWS][COLS], int r, int c) {
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            cin >> mat[i][j];
        }
    }
}

template <typename T>
void multiply(T a[ROWS][COLS], T b[ROWS][COLS], T result[ROWS][COLS], int r, int c) {
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            result[i][j] = 0;
            for (int k = 0; k < c; k++) {
                result[i][j] += a[i][k] * b[k][j];
            }
        }
    }
}

template <typename T>
void display(T mat[ROWS][COLS], int r, int c) {
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            cout << mat[i][j] << " ";
        }
        cout << endl;
    }
}

int main() {
    int A[ROWS][COLS], B[ROWS][COLS], C[ROWS][COLS];

    cout << "Enter first matrix (3x3):\n";
    input(A, ROWS, COLS);

    cout << "Enter second matrix (3x3):\n";
    input(B, ROWS, COLS);

    multiply(A, B, C, ROWS, COLS);

    cout << "Resultant matrix:\n";
    display(C, ROWS, COLS);

    return 0;
}
```

### Output
```
Enter first matrix (3x3):
Enter second matrix (3x3):
Resultant matrix:
12 9 6 
66 54 42 
120 99 78
```
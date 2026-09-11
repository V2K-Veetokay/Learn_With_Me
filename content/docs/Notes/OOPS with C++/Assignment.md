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
First point: 2 3

Second point: 4 5
Distroctor called
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
0 1 2 3 4 5 6 7 8
Enter second matrix (3x3):
9 8 7 6 5 4 3 2 1
Resultant matrix:
12 9 6 
66 54 42 
120 99 78
```


## Q-4: Phone Number
A phone number, such as (91) 120-4370000, can be thought of as having three parts: the country code (91), city code (120) and the number (4370000). Write a program that uses a class Phone to store these three parts of a phone number separately. Create two objects of type phone. Initialize one, and have the user input a number for the other one. Then display both numbers.

``` C++
#include<iostream>

using namespace std;

class Phone{
		int countryCode, cityCode, number;
	public:
		Phone(int x, int y, int z){
			countryCode = x;
			cityCode = y;
			number = z;
		}
		void display(){
			cout<<'('<<countryCode<<')'<<' '<<cityCode<<'-'<<number<<endl;
		}
};

int main(){
	Phone n1(91, 120, 4370000);
	
	int x,y,z;
	cout<<"Enter Phone No.: (Ex: 91 321 3249532)"<<endl;
	cin>>x>>y>>z;
	Phone n2(x, y, z);
	
	cout<<endl;
	n1.display();
	n2.display();
	
	return 0;
}
```

### Output
```
Enter Phone No.: (Ex: 91 321 3249532)
65 375 1451687

(91) 120-4370000
(65) 375-3451687
```


## Q-5:
Create two classes DistanceMks and DistanceCgs which store the value of distances. DistanceMks stores distances in metres and centimeters and DistanceCgs in feet and inches. Write a program that can read values for the class objects and add one object of DistanceMks with another object of DistanceCgs. Use a friend function to carry out the addition operation.

``` C++

```

### Output
```

```


## Q-6:
Create a class Sphere with radius as data member. Use constructor and destructor along with methods tp find volume and surface area of the sphere object.

``` C++

```

### Output
```

```


## Q-7:
Create a class Rational which represents a numerical value by two double values- numerator & denominator. Include the following public member Functions: constructor with no arguments (default), constructor with two arguments, reduce( ) that reduces the rational number by eliminating the highest common factor between the numerator and denominator, and findSum() to add two rational number.

``` C++

```

### Output
```

```


## Q-8: Square
Create a class Square with side as data member. Define constructors and destructor along with methods to find area, perimeter and cost of painting of the Square object.

``` C++
#include<iostream>

using namespace std;

template<class T>
class Square{
		T side;
	public:
		Square(T s){side = s;}
		~Square(){}
		
		T area(){
			return side*side;
		}
		
		T perimeter(){
			return 4*side;
		}
		
		double cost(T c){
			return side*side*c;	
		}
		
		void show(){
			cout<<"Area: "<<area()<<endl;
			cout<<"Perimeter: "<<perimeter()<<endl;
			cout<<"Cost: "<<cost(2)<<endl;
		}
};

int main(){
	Square s1(5.5);
	s1.show();
	
	return 0;
}
```

### Output
```
Area: 30.25
Perimeter: 22
Cost: 60.5
```


## Q-9: TollBooth
Imagine a tollbooth with a class called TollBooth. The two data items are a type unsigned int to hold the total number of cars, and a type double to hold the total amount of money collected. A constructor initializes both these to 0. A member function called payingCar ( ) increments the car total and adds 0.50 to the cash total. Another function, called nopayCar ( ), increments the car total but adds nothing to the cash total. Finally, a member function called display() displays the two totals. This program should allow the user to push one key to count a paying car, and another to count a nonpaying car.

``` C++
#include<iostream>

using namespace std;

class TollBooth{
		unsigned totalCar;
		double totalAmount;
	public:
		TollBooth(){totalCar=0; totalAmount=0.0;}
		
		void payingCar(){
			totalCar++;
			totalAmount+=0.50;
		}
		
		void nopayCar(){
			totalCar++;
		}
		
		void display(){
			cout<<"Total Cars: "<<totalCar<<endl;
			cout<<"Total Amount: "<<totalAmount<<endl;
		}
};

int main(){
	TollBooth t1;
	
	t1.payingCar();
	t1.payingCar();
	t1.payingCar();
	t1.payingCar();
	t1.payingCar();
	
	t1.nopayCar();
	t1.nopayCar();
	t1.nopayCar();
	
	t1.display();
	return 0;
}
```

### Output
```
Total Cars: 8
Total Amount: 2.5
```


## Q-10: Time
Write a program to create a class Time with hours and minutes as data members. Use constructors to initialize data members and a show() method to display values. Use findSum() and findDiff() methods to find the sum and differences of two Time objects and display the values.

``` C++
#include <iostream>

using namespace std;

class Time {
	int hours, minutes;
public:
	Time(int h, int m): hours(h), minutes(m){}
	
	Time findSum(Time t){
		return Time(hours+t.hours, minutes+t.minutes);
	}
	
	Time findDiff(Time t){
		return Time(hours-t.hours, minutes-t.minutes);
	}
	
	void display() {
		cout << hours << ':' << minutes << endl;
	}
}; 

int main() {
	Time t1(2, 20);
	Time t2(3, 30);
	Time t3 = t1.findSum(t2);
	Time t4 = t2.findDiff(t1);
	
	t1.display();
	t2.display();
	t3.display();
	t4.display();
	return 0;
}
```

### Output
```
2:20
3:30
5:50
1:10
```


## Q-11: Distance
Create a class Distance with km and meter as data members. Use constructors to initialize data members and display() method to display the values. Use findSum() and findDiff() methods to find the sum and differences of two Distance objects and display their values.

``` C++
#include <iostream>

using namespace std;

class Distance {
	int km, m;
public:
	Distance(int kilometer, int meter): km(kilometer), m(meter){}
	
	Distance findSum(Distance d){
		return Distance(km+d.km, m+d.m);
	}
	
	Distance findDiff(Distance d){
		return Distance(km-d.km, m-d.m);
	}
	
	void display() {
		cout << km << "km" <<' '<< m << 'm' << endl;
	}
}; 

int main() {
	Distance d1(2, 20);
	Distance d2(3, 30);
	Distance d3 = d1.findSum(d2);
	Distance d4 = d2.findDiff(d1);
	
	d1.display();
	d2.display();
	d3.display();
	d4.display();
	return 0;
}
```

### Output
```
2km 20m
3km 30m
5km 50m
1km 10m
```


## Q-12: Birth Date - Age
Create a class BirthDate with day, month and year as data members. Use constructors and destructors in the class along with showDateOfBirth() method to display birthdate of a person. Find the age of the person as of today.

``` C++
#include <iostream>
using namespace std;

const int currentYear = 2026;
const int currentMonth = 9;
const int currentDay = 11;

int daysInMonth(int month, int year) {
	if (month == 2) {
        if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0))
            return 29;
        return 28;
    }
    switch (month) {
        case 1: case 3: case 5: case 7: case 8: case 10: case 12:
            return 31;
        case 4: case 6: case 9: case 11:
            return 30;
        default:
            return 30;
    }
}

class BirthDate {
    int day, month, year;

public:
    BirthDate(int day, int month, int year)
        : day(day), month(month), year(year) {}

    ~BirthDate() {}

    void showDateOfBirth() {
        cout << day << '/' << month << '/' << year << endl;
    }

    BirthDate age() const {
        if (currentYear < year ||
            (currentYear == year && currentMonth < month) ||
            (currentYear == year && currentMonth == month && currentDay < day)) {
            cout << "Incorrect DOB" << endl;
            return BirthDate(0, 0, 0);
        }

        int ageYears = currentYear - year;
        int ageMonths = currentMonth - month;
        int ageDays = currentDay - day;

        if (ageDays < 0) {
            ageMonths--;
            int prevMonth = currentMonth - 1;
            int prevMonthYear = currentYear;
            if (prevMonth == 0) {
                prevMonth = 12;
                prevMonthYear--;
            }
            ageDays += daysInMonth(prevMonth, prevMonthYear);
        }

        if (ageMonths < 0) {
            ageYears--;
            ageMonths += 12;
        }

        return BirthDate(ageDays, ageMonths, ageYears);
    }

    void showAge() {
        cout << year << " years, " << month << " months, " << day << " days" << endl;
    }
};

int main() {
    BirthDate b1(2, 4, 2020);
    b1.showDateOfBirth();

    BirthDate age = b1.age();
    age.showAge();

    return 0;
}
```

### Output
```
2/4/2020
6 years, 5 months, 9 days
```


## Q-13:
Create a class Vector with hor and ver as data members. Use constructors and destructor along with showVector() method to display a Vector object and findLength() method to find the length of the vector in the class. Define findSum() to find the sum of Vector objects and display the values.

``` C++

```

### Output
```

```


## Q-14:
Create a class Student with roll, percentage, age as data members. Use constructors and destructor along with showStudent() method to display values of the Student object and showGrade() on the basis of percentage of marks of the Student object in the class.

``` C++

```

### Output
```

```


## Q-15:
Create a class Rectangle with length and breadth as data members. Use constructors and destructor along with methods to calculate area and perimeter of the rectangle. Define costPaint() in the Rectangle class to find the cost of paint per unit area entered by the user at run time. Use default argument for the cost of paint per unit area if user did not enter the cost.

``` C++

```

### Output
```

```


## Q-16:
Create a class Sphere with radius as data member. Use constructor and destructor along with methods to find volume and surface area of the sphere object.

``` C++

```

### Output
```

```


## Q-17:
Create a class Point with x and y as data members. Use constructors and destructor along with methods to display values of the Point objects and to find the gradient of a line passing through the two Point objects.

``` C++

```

### Output
```

```


## Q-18:
Create a class Student with marks for three subjects phy, chem, and math. Use constructors and destructor along with methods to display values and to find sum of marks and percentage of marks. Also display grade on the basis of percentage of marks of the student.

``` C++

```

### Output
```

```


## Q-19:
Create a class Temperature with degcelcius as data member in degree celcius. Use constructors and destructor along with methods for displaying values and convert to the data member from Celcius to Fahrenheit.

``` C++

```

### Output
```

```


## Q-20:
Create class Product with pid, price and quantity as data members. Use constructor and destructor along with methods to display values of a Product object and to find the total invoice value of ordering number of quantities of a particular product. Use default method argument for the quantity of product.

``` C++

```

### Output
```

```


## Q-21:
Create a class Complex with real and imaginary as data members. Use constructors and destructor along with methods to display values of the complex numbers. Define findSum() and findDiff() methods to find the sum and differences of the two complex objects.

``` C++

```

### Output
```

```


## Q-22:
Create a class Line with gradient and intercept as data members. Use constructors and destructor along with show() method to display the equation of line. Define method checkLines() to test whether two lines are perpendicular or parallel.

``` C++

```

### Output
```

```


## Q-23:
Create a class Vector with x and y as data members. Use constructors and destructor along with show() method to display values. Define dotProduct() and findSum() methods to find scaler product and sum of two vectors respectively.

``` C++

```

### Output
```

```


## Q-24:
Create a class Complex with real and imaginary as data members. Use constructors and destructor along with display() method to show values of the complex numbers. Define findMod() methods to find the modulus of complex number object.

``` C++

```

### Output
```

```


## Q-25:
Create a class Vector with hor and ver as data members. Use constructors and destructor along with showVector() method to display a Vector object and findUnit() method to find the length of the unit vector along the Vector object in the class.

``` C++

```

### Output
```

```


## Q-26:
Create a class Customer with custid, productid, price, quantity as data members. Use constructors and destructor along with display() method to display values of the data members. Define calcInvoice() method to generate invoice for a customer on purchasing products.

``` C++

```

### Output
```

```

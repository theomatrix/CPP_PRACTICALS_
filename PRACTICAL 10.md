# PRACTICAL 10
```CPP
#include <iostream>
#include <cmath>
using namespace std;

class Triangle {
public:
    double a, b, c;

    Triangle(double x, double y, double z) {
        a = x;
        b = y;
        c = z;
    }

    // Area using Heron's formula
    double area() {
        double s = (a + b + c) / 2;
        return sqrt(s * (s - a) * (s - b) * (s - c));
    }

    // Area using base and height
    double area(double base, double height) {
        return 0.5 * base * height;
    }
};

int main() {
    double x, y, z;
    cout << "Enter three sides of the triangle: ";
    cin >> x >> y >> z;

    Triangle t(x, y, z);

    cout << "Area using Heron's formula: " << t.area() << endl;

    double base, height;
    cout << "Enter base and height for right-angled triangle area: ";
    cin >> base >> height;

    cout << "Area using base and height: " << t.area(base, height) << endl;

    return 0;
}


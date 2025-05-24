# PRACTICAL 1 
```CPP
#include <iostream>
#include <cmath>
using namespace std;

double seriesSum(int n) {
    double sum = 1.0; 

    if (n >= 2) {
        sum -= 1.0 / pow(2, 2); // subtract second term
    }

    for (int i = 3; i <= n; i++) {
        sum += 1.0 / pow(2, i); 
    }

    return sum;
}

int main() {
    int n;
    cout << "Enter the number of terms: ";
    cin >> n;
    cout << "Sum of series: " << seriesSum(n) << endl;
    return 0;
}

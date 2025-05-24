# PRACTICAL 7
```cpp

    #include <iostream>
    using namespace std;

    int gcdRecursive(int a, int b) {
       if (b == 0)
         return a;
       return gcdRecursive(b, a % b);
    }

    int gcdIterative(int a, int b) {
       while (b != 0) {
          int temp = b;
          b = a % b;
          a = temp;
    }
    return a;
    }

    int main() {
       int num1, num2;
       cout << "Enter two numbers: ";
       cin >> num1 >> num2;

    cout << "GCD (Recursion): " << gcdRecursive(num1, num2) << endl;
    cout << "GCD (Iteration): " << gcdIterative(num1, num2) << endl;
    
    return 0;
    }

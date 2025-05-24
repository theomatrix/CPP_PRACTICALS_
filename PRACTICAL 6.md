# PRACTICAL 6

```CPP
 #include <iostream>
    using namespace std;

    int binarySearchRecursive(int arr[], int left, int right, int key) {
        if (left <= right) {
            int mid = left + (right - left) / 2;
        if (arr[mid] == key)
            return mid;
        else if (arr[mid] < key)
            return binarySearchRecursive(arr, mid + 1, right, key);
        else
            return binarySearchRecursive(arr, left, mid - 1, key);
    }
       return -1;
    }

    int binarySearchIterative(int arr[], int size, int key) {
           int left = 0, right = size - 1;
           while (left <= right) {
                int mid = left + (right - left) / 2;
           if (arr[mid] == key)
              return mid;
          else if (arr[mid] < key)
              left = mid + 1;
          else
            right = mid - 1;
    }
      return -1;
    }

    int main() {
         int size, key;
         cout << "Enter size of array: ";
         cin >> size;
         int arr[size];
         cout << "Enter sorted array elements: ";
         for (int i = 0; i < size; i++)
              cin >> arr[i];

    cout << "Enter element to search: ";
    cin >> key;

    int recursiveResult = binarySearchRecursive(arr, 0, size - 1, key);
    int iterativeResult = binarySearchIterative(arr, size, key);

    if (recursiveResult != -1)
        cout << "Element found at index (recursion): " << recursiveResult << endl;
    else
        cout << "Element not found (recursion)" << endl;

    if (iterativeResult != -1)
        cout << "Element found at index (iteration): " << iterativeResult << endl;
    else
        cout << "Element not found (iteration)" << endl;
    
       return 0;
    }

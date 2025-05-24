# PRACTICAL 4 
```cpp
#include <iostream>
using namespace std;

// a. Show address of each character in string
void showAddresses(char* str) {
    cout << "Char : Address\n";
    while (*str) {
        cout << *str << " : " << (void*)str << "\n";
        str++;
    }
}

// b. Concatenate two strings (assuming enough space in destination)
void concatenate(char* dest, char* src) {
    while (*dest) dest++; // move to end of dest
    while (*src) {
        *dest = *src;
        dest++;
        src++;
    }
    *dest = '\0';
}

// c. Compare two strings
int compareStrings(char* s1, char* s2) {
    while (*s1 && *s2 && *s1 == *s2) {
        s1++;
        s2++;
    }
    return (*s1 - *s2);
}

// d. Calculate length of string using pointers
int length(char* str) {
    int len = 0;
    while (*str++) len++;
    return len;
}

// e. Convert lowercase to uppercase
void toUppercase(char* str) {
    while (*str) {
        if (*str >= 'a' && *str <= 'z')
            *str = *str - ('a' - 'A');
        str++;
    }
}

// f. Reverse the string
void reverseString(char* str) {
    int len = length(str);
    char *start = str;
    char *end = str + len - 1;
    while (start < end) {
        char temp = *start;
        *start = *end;
        *end = temp;
        start++;
        end--;
    }
}

// g. Insert a string into another at specified position
void insertString(char* dest, char* src, int pos) {
    int lenDest = length(dest);
    int lenSrc = length(src);

    if (pos > lenDest) pos = lenDest; // clamp pos

    // Move the part after pos forward to make space
    for (int i = lenDest; i >= pos; i--) {
        dest[i + lenSrc] = dest[i];
    }

    // Copy src into dest at pos
    for (int i = 0; i < lenSrc; i++) {
        dest[pos + i] = src[i];
    }
}

int main() {
    char str1[200], str2[100];
    int choice, pos;

    cout << "Enter first string (max 199 chars): ";
    cin.getline(str1, 200);

    do {
        cout << "\nMenu:\n";
        cout << "1. Show address of each character in string\n";
        cout << "2. Concatenate another string\n";
        cout << "3. Compare with another string\n";
        cout << "4. Calculate length of the string\n";
        cout << "5. Convert to uppercase\n";
        cout << "6. Reverse the string\n";
        cout << "7. Insert string at position\n";
        cout << "8. Exit\n";
        cout << "Enter choice: ";
        cin >> choice;
        cin.ignore(); // clear newline from buffer

        switch (choice) {
            case 1:
                showAddresses(str1);
                break;

            case 2:
                cout << "Enter string to concatenate: ";
                cin.getline(str2, 100);
                concatenate(str1, str2);
                cout << "After concatenation: " << str1 << endl;
                break;

            case 3:
                cout << "Enter string to compare: ";
                cin.getline(str2, 100);
                {
                    int res = compareStrings(str1, str2);
                    if (res == 0) cout << "Strings are equal\n";
                    else if (res > 0) cout << "First string is greater\n";
                    else cout << "Second string is greater\n";
                }
                break;

            case 4:
                cout << "Length of string: " << length(str1) << endl;
                break;

            case 5:
                toUppercase(str1);
                cout << "Uppercase string: " << str1 << endl;
                break;

            case 6:
                reverseString(str1);
                cout << "Reversed string: " << str1 << endl;
                break;

            case 7:
                cout << "Enter string to insert: ";
                cin.getline(str2, 100);
                cout << "Enter position to insert (0-based index): ";
                cin >> pos;
                cin.ignore();
                insertString(str1, str2, pos);
                cout << "After insertion: " << str1 << endl;
                break;

            case 8:
                cout << "Exiting...\n";
                break;

            default:
                cout << "Invalid choice. Try again.\n";
        }

    } while (choice != 8);

    return 0;
}

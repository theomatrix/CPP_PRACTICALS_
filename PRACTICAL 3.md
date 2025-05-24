# PRACTICAL 3
```cpp
#include <iostream>
#include <cctype>
using namespace std;

int main(int argc, char* argv[]) {
    int freq[26] = {0}; 

    // Loop through command line arguments (skip argv[0])
    for (int i = 1; i < argc; i++) {
        for (int j = 0; argv[i][j] != '\0'; j++) {
            char ch = tolower(argv[i][j]);
            if (ch >= 'a' && ch <= 'z') {
                freq[ch - 'a']++;
            }
        }
    }

    cout << "Alphabet Frequency Table:\n";
    for (int i = 0; i < 26; i++) {
        if (freq[i] > 0) {
            cout << char('a' + i) << " : " << freq[i] << endl;
        }
    }

    return 0;
}

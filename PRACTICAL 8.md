# PRACTICAL 8 
```cpp
#include <iostream>
#include <stdexcept>
using namespace std;

class Matrix {
private:
    int rows, cols;
    int** data;

public:
    // Constructor
    Matrix(int r = 0, int c = 0) : rows(r), cols(c) {
        data = new int*[rows];
        for (int i = 0; i < rows; i++)
            data[i] = new int[cols]{0};
    }

    // Destructor
    ~Matrix() {
        for (int i = 0; i < rows; i++)
            delete[] data[i];
        delete[] data;
    }

    // Input matrix
    void input() {
        cout << "Enter elements (" << rows << "x" << cols << "):\n";
        for (int i = 0; i < rows; i++)
            for (int j = 0; j < cols; j++)
                cin >> data[i][j];
    }

    // Display matrix
    void display() const {
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++)
                cout << data[i][j] << " ";
            cout << "\n";
        }
    }

    // Sum of matrices
    Matrix add(const Matrix& other) const {
        if (rows != other.rows || cols != other.cols)
            throw invalid_argument("Matrices must be of same dimensions to add.");
        
        Matrix result(rows, cols);
        for (int i = 0; i < rows; i++)
            for (int j = 0; j < cols; j++)
                result.data[i][j] = data[i][j] + other.data[i][j];
        return result;
    }

    // Product of matrices
    Matrix multiply(const Matrix& other) const {
        if (cols != other.rows)
            throw invalid_argument("Incompatible matrices for multiplication.");
        
        Matrix result(rows, other.cols);
        for (int i = 0; i < rows; i++)
            for (int j = 0; j < other.cols; j++)
                for (int k = 0; k < cols; k++)
                    result.data[i][j] += data[i][k] * other.data[k][j];
        return result;
    }

    // Transpose
    Matrix transpose() const {
        Matrix result(cols, rows);
        for (int i = 0; i < rows; i++)
            for (int j = 0; j < cols; j++)
                result.data[j][i] = data[i][j];
        return result;
    }

    // Getters
    int getRows() const { return rows; }
    int getCols() const { return cols; }
};

// Main menu
int main() {
    int choice;

    do {
        cout << "\nMatrix Operations Menu:\n";
        cout << "1. Sum of two matrices\n";
        cout << "2. Product of two matrices\n";
        cout << "3. Transpose of a matrix\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1: {
                int r1, c1, r2, c2;
                cout << "Enter rows and cols of Matrix A: ";
                cin >> r1 >> c1;
                Matrix A(r1, c1);
                A.input();

                cout << "Enter rows and cols of Matrix B: ";
                cin >> r2 >> c2;
                Matrix B(r2, c2);
                B.input();

                try {
                    Matrix result = A.add(B);
                    cout << "Result of addition:\n";
                    result.display();
                } catch (const exception& e) {
                    cerr << "Error: " << e.what() << "\n";
                }
                break;
            }

            case 2: {
                int r1, c1, r2, c2;
                cout << "Enter rows and cols of Matrix A: ";
                cin >> r1 >> c1;
                Matrix A(r1, c1);
                A.input();

                cout << "Enter rows and cols of Matrix B: ";
                cin >> r2 >> c2;
                Matrix B(r2, c2);
                B.input();

                try {
                    Matrix result = A.multiply(B);
                    cout << "Result of multiplication:\n";
                    result.display();
                } catch (const exception& e) {
                    cerr << "Error: " << e.what() << "\n";
                }
                break;
            }

            case 3: {
                int r, c;
                cout << "Enter rows and cols of the Matrix: ";
                cin >> r >> c;
                Matrix M(r, c);
                M.input();

                Matrix T = M.transpose();
                cout << "Transpose:\n";
                T.display();
                break;
            }

            case 4:
                cout << "Program exited.\n";
                break;

            default:
                cout << "Invalid choice! Please try again.\n";
        }

    } while (choice != 4);

    return 0;
}

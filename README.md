#include <iostream>
using namespace std;

struct Triplet {
    int row;
    int col;
    int value;
};

void readSparseMatrix(Triplet sparse[], int &numNonZero) {
    cout << "Enter number of rows, columns, and non-zero elements: ";
    cin >> sparse[0].row >> sparse[0].col >> numNonZero;
    sparse[0].value = numNonZero;

    cout << "Enter row, column, and value for each non-zero element:\n";
    for (int i = 1; i <= numNonZero; i++) {
        cin >> sparse[i].row >> sparse[i].col >> sparse[i].value;
    }
}

void displaySparseMatrix(Triplet sparse[]) {
    int n = sparse[0].value;
    cout << "Row Col Value\n";
    for (int i = 0; i <= n; i++) {
        cout << sparse[i].row << "   " << sparse[i].col << "   " << sparse[i].value << endl;
    }
}

void transposeSparseMatrix(Triplet original[], Triplet transposed[]) {
    int rows = original[0].row;
    int cols = original[0].col;
    int num = original[0].value;

    transposed[0].row = cols;
    transposed[0].col = rows;
    transposed[0].value = num;

    int k = 1;
    for (int col = 0; col < cols; col++) {
        for (int i = 1; i <= num; i++) {
            if (original[i].col == col) {
                transposed[k].row = original[i].col;
                transposed[k].col = original[i].row;
                transposed[k].value = original[i].value;
                k++;
            }
        }
    }
}

int main() {
    Triplet sparse[100], transposed[100];
    int numNonZero;
    readSparseMatrix(sparse, numNonZero);
    cout << "\nOriginal Sparse Matrix:\n";
    displaySparseMatrix(sparse);
     transposeSparseMatrix(sparse, transposed);
    cout << "\nTransposed Sparse Matrix:\n";
    displaySparseMatrix(transposed);

return 0;
}

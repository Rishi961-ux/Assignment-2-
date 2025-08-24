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

void addSparseMatrices(Triplet a[], Triplet b[], Triplet sum[]) {
    if (a[0].row != b[0].row || a[0].col != b[0].col) {
        cout << "Matrices dimensions do not match.\n";
        sum[0].value = 0;
        return;
    }

   sum[0].row = a[0].row;
    sum[0].col = a[0].col;

   int i = 1, j = 1, k = 1;
    int aCount = a[0].value;
    int bCount = b[0].value;

   while (i <= aCount && j <= bCount) {
        if (a[i].row < b[j].row || (a[i].row == b[j].row && a[i].col < b[j].col)) {
            sum[k++] = a[i++];
        } else if (b[j].row < a[i].row || (b[j].row == a[i].row && b[j].col < a[i].col)) {
            sum[k++] = b[j++];
        } else {
            int addedValue = a[i].value + b[j].value;
            if (addedValue != 0) {
                sum[k].row = a[i].row;
                sum[k].col = a[i].col;
                sum[k].value = addedValue;
                k++;
            }
            i++;
            j++;
        }
    }

   while (i <= aCount) {
        sum[k++] = a[i++];
    }

   while (j <= bCount) {
        sum[k++] = b[j++];
    }

   sum[0].value = k - 1;
}

int main() {
    Triplet a[100], b[100], sum[200];
    int aCount, bCount;
    cout << "Matrix A:\n";
    readSparseMatrix(a, aCount);
    cout << "\nMatrix B:\n";
    readSparseMatrix(b, bCount);
    cout << "\nMatrix A:\n";
    displaySparseMatrix(a);
    cout << "\nMatrix B:\n";
    displaySparseMatrix(b);
    addSparseMatrices(a, b, sum);
    if (sum[0].value > 0) {
        cout << "\nSum of A and B:\n";
        displaySparseMatrix(sum);
    }
   return 0;
}

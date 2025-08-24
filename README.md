#include <iostream>
using namespace std;

class Tridiagonal {
    int* A;
    int n;

public:
    Tridiagonal(int size) {
        n = size;
        A = new int[3 * n - 2];
    }

   Tridiagonal() {
        delete[] A;
    }

   void set(int i, int j, int value) {
        if (i - j == 1)
            A[i - 1] = value;
        else if (i == j)
            A[n - 1 + i] = value;
        else if (j - i == 1)
            A[2 * n - 1 + i] = value;
    }

   int get(int i, int j) {
        if (i - j == 1)
            return A[i - 1];
        else if (i == j)
            return A[n - 1 + i];
        else if (j - i == 1)
            return A[2 * n - 1 + i];
        else
            return 0;
    }

   void display() {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                cout << get(i, j) << " ";
            }
            cout << endl;
        }
    }
};

int main() {
    Tridiagonal t(4);
    t.set(0, 0, 1);
    t.set(0, 1, 2);
    t.set(1, 0, 3);
    t.set(1, 1, 4);
    t.set(1, 2, 5);
    t.set(2, 1, 6);
    t.set(2, 2, 7);
    t.set(2, 3, 8);
    t.set(3, 2, 9);
    t.set(3, 3, 10);

    
   t.display();
    return 0;
}

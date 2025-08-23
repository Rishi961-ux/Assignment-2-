#include <iostream>
using namespace std;

class DiagonalMatrix {
    int* arr;
    int n;

public:
    DiagonalMatrix(int size) {
        n = size;
        arr = new int[n];
    }

   DiagonalMatrix() {
        delete[] arr;
    }
   void set(int i, int j, int value) {
        if (i == j && i >= 0 && i < n) {
            arr[i] = value;
        } else if (value != 0) {
            cout << "Warning: Only diagonal elements can be non-zero!" << endl;
        }
    }
   int get(int i, int j) {
        if (i == j && i >= 0 && i < n)
            return arr[i];
        else
            return 0;
    }

  void display() {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (i == j)
                    cout << arr[i] << " ";
                else
                    cout << "0 ";
            }
            cout << endl;
        }
    }
};

int main() {
    int size = 4;
    DiagonalMatrix dm(size);

   dm.set(0, 0, 5);
    dm.set(1, 1, 8);
    dm.set(2, 2, 3);
    dm.set(3, 3, 6);

   dm.display();

    return 0;
}

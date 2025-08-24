#include <iostream>
using namespace std;

class LowerTriangular {
private:
    int *A;
    int n;

public:
    LowerTriangular(int n) {
        this->n = n;
        A = new int[n * (n + 1) / 2];
    }

   ~LowerTriangular() {
        delete[] A;
    }

   
   void set(int i, int j, int value) {
        if (i >= j) {
            A[i * (i + 1) / 2 + j] = value;
        }
    }
   int get(int i, int j) const {
        if (i >= j) {
            return A[i * (i + 1) / 2 + j];
        } else {
            return 0;
        }
    }
    void display() const {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                cout << get(i, j) << " ";
            }
            cout << endl;
        }
    }
};

int main() {
    int n;
    cout << "Enter dimension: ";
    cin >> n;
    LowerTriangular lt(n);
    cout << "Enter elements row-wise:\n";
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            int x;
            cin >> x;
            lt.set(i, j, x);
        }
    }
   cout << "Matrix is:\n";
    lt.display();

 return 0;
}

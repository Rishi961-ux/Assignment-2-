#include <iostream>
using namespace std;

class UpperTriangular {
private:
    int *A;
    int n;

public:
    UpperTriangular(int n) {
        this->n = n;
        A = new int[n * (n + 1) / 2];
    }

    ~UpperTriangular() {
        delete[] A;
    }

    void set(int i, int j, int value) {
        if (i <= j) {
            A[j * (j + 1) / 2 + i] = value;
        }
    }

    int get(int i, int j) const {
        if (i <= j) {
            return A[j * (j + 1) / 2 + i];
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

 UpperTriangular ut(n);
    cout << "Enter elements row-wise:\n";
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            int x;
            cin >> x;
            ut.set(i, j, x);
        }
    }
    cout << "Matrix is:\n";
    ut.display();

    return 0;
}

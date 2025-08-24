#include <iostream>
using namespace std;

long long mergeAndCount(int arr[], int temp[], int left, int mid, int right) {
    long long invCount = 0;
    int i = left, j = mid + 1, k = left;
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp[k++] = arr[i++];
        } else {
            temp[k++] = arr[j++];
            invCount += (mid - i + 1);
        }
    }

while (i <= mid) {
        temp[k++] = arr[i++];
    }
       while (j <= right) {
        temp[k++] = arr[j++];
    }

   for (int p = left; p <= right; p++) {
        arr[p] = temp[p];
    }

   return invCount;
}

long long mergeSortAndCount(int arr[], int temp[], int left, int right) {
    long long invCount = 0;
    if (left < right) {
        int mid = (left + right) / 2;
        invCount += mergeSortAndCount(arr, temp, left, mid);
        invCount += mergeSortAndCount(arr, temp, mid + 1, right);
        invCount += mergeAndCount(arr, temp, left, mid, right);
    }
    return invCount;
}

int main() {
    int n;
    cout << "Enter number of elements: ";
    cin >> n;
    int arr[n], temp[n];
    cout << "Enter the elements:\n";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    long long inversions = mergeSortAndCount(arr, temp, 0, n - 1);
    cout << "Number of inversions: " << inversions << endl;
    return 0;
}

#include <iostream>
using namespace std;

#define MAX 5

class CircularQueue {
    int arr[MAX];
    int front, rear;

public:
    CircularQueue() {
        front = -1;
        rear = -1;
    }
   bool isEmpty() {
        return front == -1;
    }
    bool isFull() {
        return (front == (rear + 1) % MAX);
    }
   void enqueue(int val) {
        if (isFull()) {
            cout << "Queue is full,

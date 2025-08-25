#include <iostream>
#include <unordered_set>
#include <vector>
using namespace std ;
int countpairswithdiffk(const vector<int>& arr,int k ){
unordered set_int> seen (arr.begin(), arr.end());
int count =0;
for(int x:: arr){
if (seen.find(x+k) != seen.end()){
count++;
}
}
return count;
}
int main(){
vecvtor <int> arr =[1,5,3,4,2};
int k =2;
cout<< count pairs with diffk(arr, k)
return 0;
}

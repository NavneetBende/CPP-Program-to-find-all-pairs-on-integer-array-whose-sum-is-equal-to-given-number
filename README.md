All pairs whose sum is equal to given number in C++
Here, in this page we will discuss the program to find all pairs whose sum is equal to given number in C++ . We are given with an array and a value sum and we need to return the count of all the pairs whose sum is equal to given value of the sum.

Example :

Input :

arr[] = {1, 5, 7, -1}   sum = 6

Output :

2 ( Pairs with sum 6 are (1, 5) and (7, -1) )
All pairs whose sum is equal to given number in C++
Method 1 (Brute Force Approach) :
A simple solution is to traverse each element and check if there’s another number in the array which can be added to it to give sum. 

Take the size of the array from the user and store it in variable say n.
Take the value of the sum from the user and store it in variable say sum.
Now, declare an array of n size and take n integers from the  user and store them in the declared array.
Now, declare a variable say count = 0, that will count the required pairs.
Now, run a lop from i=0 to i=n-1, and check inside that loop whether there is a number which add up with the i-th number to give the value sum, if it is so then increment the value of count by 1.
After the complete of iteration print the value of the count.
 
Time and Space Complexities :
Time complexity : O(n^2)
Space Complexity : O(1)
All pairs with given sum
Code in C++ :
#include <bits/stdc++.h>
using namespace std;

int getPairsCount(int arr[], int n, int sum)
{
  int count = 0; // Initialize result

  // Consider all possible pairs and check their sums
  for (int i = 0; i < n; i++){
     for (int j = i + 1; j < n; j++){
        if (arr[i] + arr[j] == sum)
          count++;
     }
  }
  return count;
}

// Driver function to test the above function
int main()
{ 
   int n, sum;
   cin>>n>>sum;

   int arr[n];
   for(int i=0; i<n; i++) cin>>arr[i];

   cout << "Count of pairs is "<< getPairsCount(arr, n, sum);
   return 0;
}
Input :

13 11
10 12 10 15 -1 7 6 5 4 2 1 1 1}, 

Output : 
9
Method 2 (Using Hash-Map) :
Declare an unordered map to store the frequency of each element.
Iterate over the array, store it’s frequency in the map.
In the next traversal of array, for every i-th element check if it can be combined with any other element (other than itself!) to give the desired sum. Increment the counter accordingly.
After completion of second traversal, we’d have twice the required value stored in counter because every pair is counted two times. Hence divide count by 2 and return.
Time and Space Complexities :
Time complexity : O(n)
Space Complexity : O(n)
Code in C++ :
#include <bits/stdc++.h>
using namespace std;

int getPairsCount(int arr[], int n, int sum)
{
  unordered_map<int, int> m;

  // Store counts of all elements in map m
  for (int i = 0; i < n; i++)
    m[arr[i]]++;

  int twice_count = 0;

  // iterate through each element and increment the
  // count (Notice that every pair is counted twice)
  for (int i = 0; i < n; i++) {
    twice_count += m[sum - arr[i]];

    if (sum - arr[i] == arr[i])
     twice_count--;
  }

  // return the half of twice_count
  return twice_count / 2;
}

// Driver function to test the above function
int main()
{ 
  int n, sum;
  cin>>n>>sum;

  int arr[n];
  for(int i=0; i<n; i++) cin>>arr[i];

  cout << "Count of pairs is "<< getPairsCount(arr, n, sum);
  return 0;
}
Input :

13 11
10 12 10 15 -1 7 6 5 4 2 1 1 1}, 

Output : 
9
Related Pages
Given an array which consists of only 0, 1 and 2

Move all the negative elements to one side of the array

Minimum no. of Jumps to reach the end of an array 

Find Largest sum contiguous Subarray

Minimize the maximum difference between heights 

Prime Course Trailer

Related Banners
Get PrepInsta Prime & get Access to all 200+ courses offered by PrepInsta in One Subscription

Get Prime
While loop in C

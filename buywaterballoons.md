# Coding question - Buy Water Balloons     

Buy Water Balloons
Problem Description
As Holi is coming, Karan wants to buy some water balloons to prepare for it. He visits a shopkeeper who has N different types of balloons. Each type of balloon has a price denoted by array A.

The shopkeeper has an offer where Karan can buy at most B balloons at the price of one. The price of these B or less balloons would be equal to the price of the maximum-priced balloon. Karan wants to buy only one balloon of each type. He has an amount equal to C, so he can’t spend more amount than C. What is the maximum number of balloons he can buy?


Problem Constraints
1 <= |A| <= 105

1 <= A[i] <= 104

1 <= B <= |A|

1 <= C <= 109


Input Format
The first argument is an integer array A.
The second argument is an integer B.
The third argument is an integer C.


Output Format
Return an integer, the answer to the problem.


Example Input
Input 1:
A = [2, 4, 5, 3, 7]
B = 2
C = 6
Input 2:
A = [1]
B = 1
C = 1


Example Output
Output 1:
3
Output 2:
1


Example Explanation
For Input 1:
First, Karan can buy type 2 and type 4 at the price of 4 as type 2 has the maximum price. Then he buys the type 1 alone at the price of 2. He spends a total amount of 6 buying 3 balloons.
For Input 2:
He buys type 1 at price 1.

Solution: 

```
int Solution::solve(vector<int> &A, int B, int C) {
    int n = A.size();
    assert(n >= 1 && n <= 1e5);
    assert(B >= 1 && B <= n);
    assert(C >= 1 && C <= 1e9);

    sort(A.begin(), A.end());

    int dp[n];
    int ans = n;
    for (int i = 0; i < n; i++) {
        assert(A[i] >= 1 && A[i] <= 1e4);

        if (i < B)
            dp[i] = A[i];
        else
            dp[i] = dp[i - B] + A[i];
        
        if (dp[i] > C) {
            ans = i;
            break;
        }
    }
    return ans;
}
```

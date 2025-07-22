# DP Example
Print Fibonacci number

(1) Using Recursion: TC: O(2^n), SC: O(n)

#include<bits/stdc++.h>
using namespace std;

int fib(int n){
    if(n<=1) return n;
    
    return fib(n-1)+fib(n-2);
}

int main(){
    int n=5;
    cout<< fib(n);
    
    return 0;
}

(2) Converted to Memoization: TC: O(n), SC: O(n)[for vector] + O(n)[for recursion stack]

#include<bits/stdc++.h>
using namespace std;

int fib(int n, vector<int> &dp){
    if(n<=1) return n;
    if(dp[n]!=-1) return dp[n];
    
    return dp[n]= fib(n-1, dp) + fib(n-2, dp);
}

int main(){
    int n=5;
    vector<int> dp(n+1,-1);
    cout<< fib(n, dp);
    
    return 0;
}

(3) Converted to Tabulation: TC: O(n), SC: O(n)[for vector]

#include<bits/stdc++.h>
using namespace std;

int main(){
    int n=5;
    vector<int> dp(n+1,-1);
    dp[0]=0; dp[1]=1;
    for(int i=2;i<=n;i++){
        dp[i] = dp[i-1] + dp[i-2];
    }
    cout<< dp[n];
    
    return 0;
}

(4) Space Optimized of Tabulation (Iterative code): TC: O(n), SC: O(1)

#include<bits/stdc++.h>
using namespace std;

int main(){
    int n= 5;
    int prev2=0, prev=1, cur=0;
    for(int i=2;i<=n;i++){
        cur= prev+prev2;
        prev2= prev;
        prev= cur;
    }
    cout<< prev;
    
    return 0;
}

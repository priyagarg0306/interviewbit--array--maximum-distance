# interviewbit--array--maximum-distance

**-----> Question:**

Given an array A of integers, find the maximum of j - i subjected to the constraint of A[i] <= A[j].



Input Format
First and only argument is an integer array A.



Output Format
Return an integer denoting the maximum value of j - i;



Example Input
Input 1:

 A = [3, 5, 4, 2]


Example Output
Output 1:

 2


Example Explanation
Explanation 1:

 Maximum value occurs for pair (3, 4).
 
 **-----> Code:**
 
 int Solution::maximumGap(const vector<int> &A) {

    int n=A.size();

    vector<int> mini(n),maxi(n);

    mini[0]=A[0];
    for(int i=1;i<n;i++){
        mini[i]=min(mini[i-1],A[i]);
    }

    maxi[n-1]=A[n-1];
    for(int i=n-2;i>=0;i--){
        maxi[i]=max(A[i],maxi[i+1]);
    }

    int i=0,j=0,ans=0;

    while(i<n && j<n){
        if(mini[i]<=maxi[j]){
            ans=max(ans,j-i);
            j++;
        }else{
            i++;
        }
    }

    return ans;

}

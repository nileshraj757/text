class Solution {
public:
    int side;
    vector<bool> visited;
    matchstick problem leetcode - #473
    
    
    bool makesquare(vector<int>& mat) {
        int n = mat.size();
         visited.resize(n,false);
       int sum = accumulate(mat.begin(),mat.end(),0);
        cout<<sum;
        if(sum%4!=0 || n<4)
           return false;
         side = sum/4;
        
        return backtrack(0,mat,0,0);
    }
    
    bool backtrack(int i,vector<int>&mat,int subsetsum,int subset)
    {
        if(subset ==4)
            return true;
        if(subsetsum==side)
           {
           return backtrack(0,mat,0,subset+1);
        }
        for(int j=i;j<mat.size();j++)
        {
            if(visited[j] || subsetsum+mat[j]>side)
                continue;
            visited[j]=true;
            if(backtrack(j+1,mat,subsetsum+mat[j],subset))
                return true;
            visited[j]=false;
        }
        
        return false;
    }
    
    
};

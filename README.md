# -Predict-the-Winner-leetCode-

int solve(vector<int>&nums, int s, int e)
    {
        if(s>e || s>=nums.size() || e<0)
        {
            return 0;
        }

        int a = nums[s] + min(solve(nums, s+2, e), solve(nums, s+1, e-1));

        int b = nums[e] + min(solve(nums, s, e-2), solve(nums, s+1, e-1));
     
        return max(a,b);
    }
    bool PredictTheWinner(vector<int>& nums) {



        int p1= solve(nums, 0, nums.size()-1);
        int p2=accumulate(nums.begin(), nums.end(), 0) - p1;

        if(p1>=p2)
        {
            return true;
        }

        return false;




        
    }

Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target.
The same repeated number may be chosen from candidates unlimited number of times.
Note:
All numbers (including target) will be positive integers.
The solution set must not contain duplicate combinations.
Example 1:
Input: candidates = [2,3,6,7], target = 7,
A solution set is:
[
  [7],
  [2,2,3]
]
Example 2:
Input: candidates = [2,3,5], target = 8,
A solution set is:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]
//此题若无全路径要求，用动态规划(类似背包问题)速度要快许多
```c++
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        int n,tmp;
	    vector<int> temp;
	    vector<vector<int> > ans;
	    DFS(temp, candidates, ans, 0 , target,0);
        return ans;
    }
    void DFS(vector<int> &temp, vector<int> &candidates, vector<vector<int> >& ans,int sum,int target,int l)
    {
	    if (sum > target) return;
	    if (sum == target)
	    {
		    ans.push_back(temp);
	    }
	    for (int i = l; i < candidates.size(); i++)
	    {
		    temp.push_back(candidates[i]);
		    DFS(temp,candidates,ans,sum+candidates[i],target,i);//能否重复区别仅在此:不能重复时i+1
		    temp.pop_back();
	    }
    }
};
```

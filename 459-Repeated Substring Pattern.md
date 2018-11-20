Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.
 
Example 1:
Input: "abab"
Output: True
Explanation: It's the substring "ab" twice.
Example 2:
Input: "aba"
Output: False
Example 3:
Input: "abcabcabcabc"
Output: True
Explanation: It's the substring "abc" four times. (And the substring "abcabc" twice.)
```c++
class Solution {
public:
    bool repeatedSubstringPattern(string s) {
	for(int i=2;i<=s.size();i++)
	{
		if(s.size()%i==0)
		{
			string x;
			string temp(s.begin(), s.begin() + s.size() / i);
			for (int j = 0; j < i; j++)
			{
				x += temp;
			}
			if (x == s)
			{
				return true;
			}
		}
	}
	return false;
    }
};
```

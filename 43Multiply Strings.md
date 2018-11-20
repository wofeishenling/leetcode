```c++
class Solution {
public:
    string multiply(string num1, string num2) {
         if (num1 == "0" || num2 == "0") return "0";
        
        reverse(num1.begin(), num1.end());
        reverse(num2.begin(), num2.end());
        
        int n1 = num1.size(), n2 = num2.size();
        vector<int> mul(n1 + n2, 0);
        for (int i = 0; i < n1; ++i) {
            int mul1 = num1[i] - '0';
            for (int j = 0; j < n2; ++j) {
                mul[i+j] += mul1 * (num2[j] - '0');
            }
        }
        
        string ret = "";
        int carry = 0;
        for (int i = 0; i < mul.size(); ++i) {
            carry += mul[i];
            ret = to_string(carry % 10) + ret;
            carry /= 10;
        }
        // remove the prefix '0'
        int i = 0;
        while (i < ret.size() && ret[i] == '0') i++;
        
        return ret.substr(i, ret.size() - i);
    }
};
```

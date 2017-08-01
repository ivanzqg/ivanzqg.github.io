#### Problem: Find longest substr

using sliping window method;

**Complexity Analysis**

- Time complexity : O(n)O(n). Index jj will iterate nn times.

- Space complexity (HashMap) : O(min(m, n))O(min(m,n)). Same as the previous approach.

- Space complexity (Table): O(m)O(m). mm is the size of the charset.

#### Problem: Find Median of Two Sorted Arary

Manacher Algorithm

```c++
//manacher algorithm
#define MAX(X, Y) ((X) > (Y) ? (X) : (Y))
#define MIN(X, Y) ((X) < (Y) ? (X) : (Y))
#define PLACEHOLDER '#'

string longgestPalindrome(string s)
{
    string tmp;
    for (auto it = s.begin(); it != s.end(); it++)
    {
        tmp += PLACEHOLDER;
        tmp += *it;
    }
    tmp += PLACEHOLDER;
    swap(tmp, s);

    int midPos = 0;
    int maxRight = 0;

    int maxMid = 0;
    int maxRL = 0;

    vector<int> RL(s.length(), 0);

    for (int i = 0; i < s.length(); i++)
    {
        if(i < maxRight)
        {
            RL[i] = MIN(RL[midPos * 2 - i], maxRight - i);
        }
        else
        {
            RL[i] = 1;
        }

        //expand
        while(i - RL[i] >= 0 && i + RL[i] < s.length() && s[i - RL[i]] == s[i + RL[i]])
        {
            RL[i]++;
        }
        if(i + RL[i] > maxRight)
        {
            maxRight = i + RL[i];
            midPos = i;
        }
        if(RL[i] > maxRL)
        {
            maxRL = RL[i];
            maxMid = i;
        }
    }

    tmp = s.substr(maxMid - maxRL + 1, maxRL * 2 - 1);
    s.clear();
    for (int i = 0; i < tmp.length(); i++)
    {
        if(tmp[i] != PLACEHOLDER)
        {
            s += tmp[i];
        }
    }

    return s;
}
```

### Dynamic Programming


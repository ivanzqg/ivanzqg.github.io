#### Problem: Find longest substr

using sliping window method;

**Complexity Analysis**

- Time complexity : O(n)O(n). Index jj will iterate nn times.

- Space complexity (HashMap) : O(min(m, n))O(min(m,n)). Same as the previous approach.

- Space complexity (Table): O(m)O(m). mm is the size of the charset.

#### Problem: Find Median of Two Sorted Arary

done

```c++
using Nums = vector<int>;
class Solution {
public:    
    double getMidNum(vector<int> &nums, int n = 0)
    {
        if(n == 0)
        {
            return (nums.at((nums.size() - 1) / 2) + nums.at(nums.size() / 2)) * 0.5;
        }
        else
        {
            size_t size = nums.size();
            if(size % 2 == 0)   //even size
            {
                if(n <= nums[size / 2 - 1])
                {
                    return nums[size / 2 - 1];
                }
                else if(n >= nums[size / 2])
                {
                    return nums[size / 2];
                }
                else
                {
                    return n;
                }
            }
            else    //odd size
            {
                if(n <= nums[size / 2 - 1])
                {
                    return (nums[size / 2 - 1] + nums[size / 2]) * 0.5;
                }
                else if(n >= nums[size / 2 + 1])
                {
                    return (nums[size / 2] + nums[size / 2 + 1]) * 0.5;
                }
                else
                {
                    return (nums[size / 2] + n) * 0.5;
                }
            }
        }
    }
    
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        if(nums1.size() == 0 || nums2.size() == 0)
        {
            return getMidNum(nums1.size() > nums2.size()? nums1 : nums2);
        }

        size_t size1 = nums1.size();
        size_t size2 = nums2.size();

        if(size1 == 1 && size2 == 1)
        {
            return (nums1[0] + nums2[0]) * 0.5;
        }
        else if(size1 == 1)
        {
            return getMidNum(nums2, nums1[0]);
        }
        else if(size2 == 1)
        {
            return getMidNum(nums1, nums2[0]);
        }
        //else

        //recursion
        double mid1 = getMidNum(nums1);
        double mid2 = getMidNum(nums2);

        if(mid1 == mid2)
        {
            return mid1;
        }
        //else
        
        if(size1 % 2 == 0 && size2 % 2 == 0)
        {
            if(nums1[size1 / 2 - 1] <= nums2[size2 / 2 - 1] && nums1[size1 / 2] >= nums2[size2 / 2])
            {
                return (nums2[size2 / 2 - 1] + nums2[size2 / 2]) * 0.5;
            }
            else if(nums1[size1 / 2 - 1] > nums2[size2 / 2 - 1] && nums1[size1 / 2] < nums2[size2 / 2])
            {
                return (nums1[size1 / 2 - 1] + nums1[size1 / 2]) * 0.5;
            }
        }

        size_t len = (size1 < size2 ? size1 : size2) / 2;   //len to cut
        if(mid1 < mid2)
        {
            Nums sub1(nums1.begin() + len, nums1.end());
            Nums sub2(nums2.begin(), nums2.end() - len);
            return findMedianSortedArrays(sub1, sub2);
        }
        else if(mid1 > mid2)
        {
            Nums sub1(nums1.begin(), nums1.end() - len);
            Nums sub2(nums2.begin() + len, nums2.end());
            return findMedianSortedArrays(sub1, sub2);
        }

    }
};
```

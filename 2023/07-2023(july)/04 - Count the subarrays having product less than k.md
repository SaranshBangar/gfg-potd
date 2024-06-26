## 04. Count the subarrays having product less than k

The problem can be found at the following link: [Question Link](https://practice.geeksforgeeks.org/problems/count-the-subarrays-having-product-less-than-k1708/1)


### My Approach

- I uses a simple approach with two pointers, `i` and `j`. `i` represents the starting pointer, and `j` represents the ending pointer.
- A variable `currProd` is used to store the current product of elements in the subarray.
- The code traverses through the array until both `i` and `j` do not reach the value `n`.
- During the traversal, we checks whether the subarray between the `starting` and `ending` pointers has a product less than `k`.
- If the product is greater than or equal to `k`, we updates the value of starting pointer `i` to make the current product value less than `k`.
- If the product is less than `k`, we increments the `output` variable out by the distance between `i` and `j`, representing the `subarray count`.
- Finally, increments `j` to move the ending pointer to the next element.

#### Example
```
n = 6, k = 10
a = {1, 2, 3, 4, 3 , 2}

dry run - (every value represents loop)

{1, 2, 3, 4, 3 , 2}       => currProd = 1,  out = 0 + 1 = 1
 -
{1, 2, 3, 4, 3 , 2}       => currProd = 2,  out = 1 + 2 = 3
 -  -
{1, 2, 3, 4, 3 , 2}       => currProd = 6,  out = 3 + 3 = 6
 -  -  -
{1, 2, 3, 4, 3 , 2}       => currProd = 24
 -  -  -  -     
at this starting pointer updates
{1, 2, 3, 4, 3 , 2}       => currProd = 4,  out = 6 + 1 = 7
          -     
{1, 2, 3, 4, 3 , 2}       => currProd = 12
          -  -     
at this starting pointer updates
{1, 2, 3, 4, 3 , 2}       => currProd = 3,  out = 7 + 1 = 8
             -
{1, 2, 3, 4, 3 , 2}       => currProd = 6,  out = 8 + 2 = 10
             -   -
```

### Time and Auxiliary Space Complexity

- **Time Complexity** : `O(2n)` since we used two pointers here which in worst case can iterate for 2n times.
- **Auxiliary Space Complexity** : `constant` auxiliary space complexity as it does not require any extra space.

### Code (C++) 
```cpp

class Solution{
  public:
    long long countSubArrayProductLessThanK(const vector<int>& a, int n, long long k) {
        long long p = 1;
        long long res = 0;
        for (int start = 0, end = 0; end < n; end++) {
    
            // Move right bound by 1 step. Update the product.
            p *= a[end];
    
            // Move left bound so guarantee that p is again
            // less than k.
            while (start < end && p >= k) p /= a[start++];
    
            // If p is less than k, update the counter.
            // Note that this is working even for (start == end):
            // it means that the previous window cannot grow
            // anymore and a single array element is the only
            // addendum.
            if (p < k) {
                int len = end - start + 1;
                res += len;
            }
        }
    
        return res;
    }
};

```


### Contribution and Support

For discussions, questions, or doubts related to this solution, please visit our [discussion section](https://github.com/getlost01/gfg-potd/discussions). We welcome your input and aim to foster a collaborative learning environment.

If you find this solution helpful, consider supporting us by giving a `⭐ star` to the [getlost01/gfg-potd](https://github.com/getlost01/gfg-potd) repository.

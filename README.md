## GFG Problem Of The Day

### Today - 11 April 2024
### Que - Gray to Binary equivalent
The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/gray-to-binary-equivalent-1587115620/1)

### My Approach
To convert a Gray code to binary, we can use bitwise XOR operations. The process involves iterating through each bit of the Gray code, and at each step, XOR-ing it with the previously processed bit. This results in the binary representation of the given Gray code.

### Time and Auxiliary Space Complexity

- **Time Complexity** : `O(log n)`, where n is the input number.
- **Auxiliary Space Complexity** : O(1).

### Code (C++)
```cpp
class Solution {
public:
    int grayToBinary(int n)
    {
        int ans = 0;
        while(n > 0)
        {
            ans = ans ^ n;
            n = n >> 1;
        }
        return ans;
    }
};
```

### Contribution and Support

I always encourage contributors to participate in the discussion forum for this repository.

If you have a better solution or any queries / discussions related to the `Problem of the Day` solution, please visit our [discussion section](https://github.com/getlost01/gfg-potd/discussions). We welcome your input and aim to foster a collaborative learning environment.

If you find this solution helpful, consider supporting us by giving a `⭐ star` to the [getlost01/gfg-potd](https://github.com/getlost01/gfg-potd) repository.

![Total number of repository visitors](https://komarev.com/ghpvc/?username=gl01potdgfg&color=blue&&label=Visitors)
![](https://hit.yhype.me/github/profile?user_id=79409258)


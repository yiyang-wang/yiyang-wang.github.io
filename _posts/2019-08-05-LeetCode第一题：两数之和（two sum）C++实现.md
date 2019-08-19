说来惭愧。当时本科开始的时候，我偶尔还会刷刷acm，后来确定保研了，代码都不咋写了，目前码代码很生疏了，现在满心的后悔（**当然世界上没有后悔药可以买/(ㄒoㄒ)/~~**），~~我可不是替我的菜找借口啊~~ 。
下面进入正题，开始我最直接的解题思路是这样的：首先对数组的元素进行排序，并且得到排序后各个元素的原来索引，（也就是元素大小在进行排序的过程中位置发生改变，索引是原来的索引值，但是位置也相应变化），那么这样就只要在数组中搜索小于target的前n个元素，对这些进行暴力遍历即可。~~后来想了一想，还不如直接暴力法呢，排序干嘛，我总是想的好复杂啊（就是自己太弱鸡了）~~ 

```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> index;
        vector<int> res;
        int length = nums.size();
        int num_size = nums.size();


        for(int i=0; i<num_size; i++) {
            index.push_back(i+1);
        }

        for(int j=0; j<num_size; j++) {
            for(int k=0; k<num_size-j-1; k++) {
                if(nums[k] > nums[k+1]) {
                    int temp = nums[k];
                    nums[k] = nums[k+1];
                    nums[k+1] = temp;

                    int temp_index = index[k];
                    index[k] = index[k+1];
                    index[k+1] = temp_index;
                }
            }
        }

        for(int m=0; m<num_size; m++) {
            if(target >= *max_element(nums.begin(), nums.end())) {
                length = num_size;
            }
            else if(target < nums[m]) {
                length = m+1;
                break;
            }
        }

        for(int n=0; n<length; n++) {
            for(int p=n+1; p<length; p++) {
                if(nums[n]+nums[p] == target) {
                    res.push_back(index[n]);
                    res.push_back(index[p]);
                    sort(res.begin(), res.end());

                    return res;
                }
            }
        }
    }

};
```
接下来是官方的解题方法：
  
    //方法二 C++版本的两遍哈希表（官方题解）
    /*
    通过以空间换取速度的方式，我们可以将查找时间从 O(n) 降低到 O(1)。
    C++版本的哈希表算法采用unordered_map。
    */
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> ans;
        unordered_map<int,int> tmpmap;
        int length = nums.size();
        for(int i = 0;i < length;i++){
            tmpmap[nums[i]] = i;
        }
        for (int i = 0; i < length; i++){
            if(tmpmap.count(target - nums[i]) != 0 && tmpmap[target - nums[i]] != i){  
            //使用count，返回的是被查找元素的个数。如果有，返回1；否则，返回0。
                ans.push_back(i);
                ans.push_back(tmpmap[target - nums[i]]);
                break;
            }
        }
        return ans;
    }
    
    //方法三 C++版本的一遍哈希表（官方题解）
    /*
    事实证明，我们可以一次完成。在进行迭代并将元素插入到表中的同时，我们还会回过头来检查
    表中是否已经存在当前元素所对应的目标元素。如果它存在，那我们已经找到了对应解，并立即将其返回。
    */
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> ans;
        unordered_map<int,int> tmpmap;
        int length = nums.size();
        for (int i = 0; i < length; i++){
            if(tmpmap.count(nums[i]) != 0){
                ans.push_back(tmpmap[nums[i]]);
                ans.push_back(i);
                break;
            }
            tmpmap[target - nums[i]] = i;
        }
        return ans;
    }


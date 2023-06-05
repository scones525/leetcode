題目敘述 :給兩個正整數 n、k，並且找出n所有因數中的第K的因數。

# 我的作法
想法 :窮舉所有n的因數、進行排序後再返回第K大的因數

code : 
```
class Solution {
public:
    int kthFactor(int n, int k) {

        vector<int> arr;
        int i = 1;
        do{
            if(n%i == 0 && i != n/i && i < n/i){
                arr.push_back(i);
                arr.push_back(n/i);
                //cout<<n/i<<" ";
            }
            else if(n%i == 0 && i == n/i)arr.push_back(i);
            i++;
        }while(i < n/2);
        sort(arr.begin(),arr.end());
        //for(int i = 0 ; i < arr.size() ; i++)cout<<arr[i]<<" ";
        if(k  > arr.size())return -1;
        return arr[k-1];
        
    }
};
```
run time : win 39.11%   Memory : win 39.43%
### 問題1.
一開始我是直觀的使用for迴圈一直從1跑到n/2，但是後來發現這樣對於1這個元素就沒有考慮到，因此改成do while迴圈。
 
### 問題2.
後來因為條件式沒有寫的很清楚，例如雖是1~n/2間所有元素，但例如對於24來說對於3、8兩個元素因為都小於n/2導致加入兩次，
後來在push_back arr的條件是中加入i < n/i保證加入元素不重複。

### 問題3.
因為調用C++ sort，時間複雜度為nlogn，仍有改善空間。

# 更新做法2
從k這邊開始下手，從小到大去找出n的因數、每找一個就k--。

code : 
```c++
class Solution {
public:
    int kthFactor(int n, int k) {
        int d;
        for(d = 1; d <= n ; d++){
            if(d*d == n && k == 1)return d;
            else if(n % d == 0 && --k == 0){
                return d;
            }
        }
        return -1;
    }
};
```
run time : win 100%   Memory : win 39.43%






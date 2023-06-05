題目敘述 :給兩個正整數 n、k，並且找出n所有因數中的第K的因數。

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

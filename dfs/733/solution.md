
###題目理解 : 將當前給定sr、sc周圍的非0元素都改變成當前image[sr][sc]的color

最直接想到DFS作法 : 由row-1、col-1、row+1、col+1四個方位去查找是否有相同的color，

因此跳出條件為 :  1.row、col超出邊界
                 2.當前顏色(也就是image[r][c])與將要被染成的顏色相同。
                 3.當前沒有顏色
                 


```c++
class Solution {
public:
    void dfs(vector<vector<int>>& image,int r,int c,int color,int ter){
        if(r<0 || c<0 || r >= image.size() || c >= image[0].size() || image[r][c] != ter || image[r][c] == color)return ;

        image[r][c] = color;

        dfs(image,r-1,c,color,ter);
        dfs(image,r,c-1,color,ter);
        dfs(image,r+1,c,color,ter);
        dfs(image,r,c+1,color,ter);
        
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
        if(image.size() == 0 && image[0].size() == 0)return image;
        dfs(image,sr,sc,color,image[sr][sc]);
        return image;
    }
};
```

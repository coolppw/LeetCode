# LeetCodeNote

[toc]

## 知识

* lambda表达式
  * 一个lambda表达式表达了一个函数对象
* string.find()
  * 若字符串中未包含要查找字符串，则返回string::npos


## 技巧

### 翻转链表两个节点

* ```c++
  ListNode* pre; //待翻转节点的前一个节点
  ListNode* cur; //待翻转的第一个节点
  ListNode* next; //待翻转的后一个节点
  
  cur = pre->next;
  //翻转节点
  next = cur->next;
  cur->next = next->next;
  next->next = pre->next;
  pre->next = next;
  ```


### 大小写字母转换

* 将字母与32异或

### 前缀和


* 常用于求数组的子数组的和

### 滑动窗口


* 可求最大连续子区间

### 动归

* **如果求组合数就是外层for循环遍历物品，内层for遍历背包**。
* **如果求排列数就是外层for遍历背包，内层for循环遍历物品**

### 拓扑排序：

* 对DFS后序遍历的结果进行反转

### 二分

* 使用二分进行查值，需要确保序列本身满足“**二段性**”
* 当选定一个端点（基准值）后，结合“**一段满足&另一段不满足**”的特性来实现“折半查找“的效果
* 二分的本质是两段性，并非单调性。
* 只要一段满足某个性质，另外一段不满足某个性质，就可以用二分

## 函数

* 纯数字字符串转整型

  * ```c++
    stoi()
    ```

* 数组求和

  - ```c++
    vector<int> nums;
    int sum = accumulate(nums.begin(), nums.end(), 0) // 0代表起始值
    ```

* 求数组中的最大值

  * ```c++
    vector<int> nums;
    int maxNum = *max_element(nums.begin(), nums.end());
    ```

* 判断是否为奇数

  * ```c++
    int num;
    if (num & 1) 
    ```

* 二分查找

  * ```c++
    vector<int> nums;
    lower_bound(nums.begin(), nums.end(), val);
    //lower_bound() 函数查找升序数组中大于等于（>=）指定元素（val）的第一个元素下标
    lower_bound(nums.begin(), nums.end(), val, greater<int>());
    //lower_bound() 函数查找降序数组中小于等于（<=）指定元素的第一个元素下标
    ```

  * ```c++
    vector<int> nums;
    upper_bound(nums.begin(), nums.end(), val);
    //upper_bound()函数查找升序数组中大于（>）指定元素的第一个元素下标
    upper_bound(nums.begin(), nums.end(), val, greater<int>());
    //upper_bound()函数查找降序数组中小于（<）指定元素的第一个元素下标 
    ```

    

## 算法模板

### 二分查找模板

* 将区间[left, right]划分成[left, mid]和[mid + 1, right]，找到第一个大于等于target的位置

* ```c++
  vector<int> nums;
  int left = 0;
  int right = nums.size() - 1;
  while (left < right) {
      int mid = left + (right - left) / 2;
      if (nums[mid] >= target) right = mid;
      else left = mid + 1;
  }
  return right;
  ```

* 将区间[left, right]划分成[left, mid - 1]和[mid, right]，找到最后一个小于等于target的位置

* ```c++
  vector<int> nums;
  int left = 0;
  int right = nums.size() - 1;
  while (left < right) {
      int mid = left + (right - left + 1) / 2;
      if (nums[mid] <= target) left = mid;
      else right = mid - 1;
  }
  return right;
  ```

  



### 并查集

- ```c++
  class UF {
  private:
      int count;
      vector<int> parent;
      
  public:
      UF(int n) {
          count = n;
          parent.resize(n);
          for (int i = 0; i < n; i++) {
              parent[i] = i;
          }
      }
      
      void unionNew(int p, int q) {
          int rootP = find(p);
          int rootQ = find(q);
          
          if (rootP == rootQ)
              return;
          
          parent[rootQ] = rootP;
          count--;
      }
      
      bool connected(int p, int q) {
          int rootP = find(p);
          int rootQ = find(Q);
          return rootP == rootQ;
      }
      
      int find(int x) {
          if (parent[x] != x) {
              parent[x] = find(parent[x]);
          }
          return parent[x];
      }
      
      int countNum() {
          return count;
      }
  };
  ```

  

- BFS

  - ```c++
    //计算从起点Start到终点Target最近距离
    int BFS()
    ```

    

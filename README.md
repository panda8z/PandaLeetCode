# PandaLeetCode primer to advance

本仓库使用VSCode完成,以下是一个leetcode插件:
[jdneo/vscode-leetcode: Solve LeetCode problems in VS Code](https://github.com/jdneo/vscode-leetcode)
[LeetCode - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=shengchen.vscode-leetcode)

## Day 1 2019年02月18日 simple two-sum

第一版本:

我自己一开始就是这个水平.

双层循环.

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] answer = new int[2];
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if ((nums[i] + nums[j]) == target) {
                    answer[0] = i;
                    answer[1] = j;
                }
            }
        }
        return answer;
    }
}
```

第二版本:

看了别人的结题思路.

1. 放到`HashMap`里面
2. 遍历给定整型数组
3. 根据`HashMap`的key唯一属性轻松获取到符合条件的key

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] answer = new int[2];
        HashMap<Integer,Integer> m = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            m.put(nums[i], i);
        }
        for (int i = 0; i < nums.length; i++) {
            int t = target - nums[i];
            if(m.containsKey(t) && m.get(t) != i){
                answer[0] = i;
                answer[1] = m.get(t);
            }
        }
        return answer;
    }
}
```
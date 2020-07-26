#QS的Leetcode周赛编程笔记
199周周赛
Q1：重新排列字符串

> 给你一个字符串 s 和一个 长度相同 的整数数组 indices 。
> 
> 请你重新排列字符串 s ，其中第 i 个字符需要移动到 indices[i] 指示的位置。
> 
> 返回重新排列后的字符串。
    
    输入：s = "codeleet", indices = [4,5,6,7,0,2,1,3]
    输出："leetcode"
    解释："codeleet" 重新排列后变为 "leetcode" 

    输入：s = "aaiougrt", indices = [4,0,2,6,7,3,1,5]
    输出："arigatou"

大佬编码：

    class Solution { 
    	public String restoreString(String s, int[] indices) { 
    		int n = s.length(); 
    		char[] chars = new char[n]; 
    		for(int i = 0 ; i < n ; i++){ 
    			chars[indices[i]] = s.charAt(i); 
    		} 
    	return new String(chars); 
		}
    }

我的编码(垃圾)：
    
    class Solution { 
    	public String restoreString(String s, int[] indices) { 
    		char[] chstr = s.toCharArray(); 
    		ArrayList NumList = new ArrayList(); 
    		for(int i = 0 ; i < s.length() ; i++ ){ 
    			for(int j = 0;j < s.length() ; j++ ){ 
    				if(indices[j] == i){ 
    					NumList.add(chstr[j]);
     				}
     			}
     		if(NumList.size()==s.length()){break;} 
   			 } 
    	return NumList.toString().replaceAll("[^a-z]",""); 
    	}   
    }


Q2：灯泡开关问题

> 房间中有 n 个灯泡，编号从 0 到 n-1 ，自左向右排成一行。最开始的时候，所有的灯泡都是 关 着的。
> 
> 请你设法使得灯泡的开关状态和 target 描述的状态一致，其中 target[i] 等于 1 第 i 个灯泡是开着的，等于 0 意味着第 i 个灯是关着的。
> 
> 有一个开关可以用于翻转灯泡的状态，翻转操作定义如下：
> 
> 选择当前配置下的任意一个灯泡（下标为 i ）
> 翻转下标从 i 到 n-1 的每个灯泡
> 翻转时，如果灯泡的状态为 0 就变为 1，为 1 就变为 0 。
> 
> 返回达成 target 描述的状态所需的 最少 翻转次数。



    输入：target = "10111"
    输出：3
    解释：初始配置 "00000".
    从第 3 个灯泡（下标为 2）开始翻转 "00000" -> "00111"
    从第 1 个灯泡（下标为 0）开始翻转 "00111" -> "11000"
    从第 2 个灯泡（下标为 1）开始翻转 "11000" -> "10111"
    至少需要翻转 3 次才能达成 target 描述的状态
    

    输入：target = "101"
    输出：3
    解释："000" -> "111" -> "100" -> "101".

大佬代码：

    class Solution { 
    	public int minFlips(String target) { 
    		int time = 0, n = target.length(), res = 0; 
    		for(int i = 0 ; i < n ; i++){ 
    			if(target.charAt(i) - '0' != time){ 
    				time ^= 1; 
    				res++; 
    			} 
    		} 
    	return res; 
    	} 
    }


> 视频解释：https://www.bilibili.com/video/BV1Up4y1i711?p=3
> 
> 类似【翻转】题目结论：
> 1.每一个位置最多只会被翻转一次（0/1，不会出现2次）
> 2.操作的顺序不会对结果造成影响


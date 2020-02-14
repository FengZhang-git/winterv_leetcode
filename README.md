# 寒假leetcode记录  
## 2.14  
  ### 1）最长回文字符串  
  给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。  
  ```c++
   string longestPalindrome(string s) {
        int start = 0;
        int end = -1;
        
        for(int i=0;i<s.length();i++){
            int len1 = expandPalindrome(s,i,i);
            int len2 = expandPalindrome(s,i,i+1);
            int len = len1>len2?len1:len2;
           // cout<<"len:"<<len;
            if(len > (end-start+1)){
                start = i - (len-1)/2;
                end = i+ len/2;
               // cout<<"start:"<<start<<"end:"<<end<<endl;
               // cout<<s.substr(start,len)<<endl;
            }

        }
        return s.substr(start,end-start+1);

    }

    int expandPalindrome(string s, int left, int right){
        
        while(left >=0 && right <s.length() && s[left] == s[right]){
            left--;
            right++;
        }   
        return right-left - 1;
    }
  ```

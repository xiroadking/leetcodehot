```
package lkanswer;

/**
 * 给你一个字符串 s，找到 s 中最长的回文子串。
 * <p>
 * 输入：s = "babad"
 * 输出："bab"
 * 解释："aba" 同样是符合题意的答案。
 */
public class HotLK5 {
    public static void main(String[] args) {
        HotLK5 hotLK5 = new HotLK5();
        String result = hotLK5.longestPalindrome("badac");
        System.out.println(result);
    }

    public String longestPalindrome(String s) {
        int maxLeft = 0, maxRight = -1;
        for (int i = 0; i < s.length(); ++i) {
            int left = i, right = i;
            while (left >= 0 && s.charAt(left) == s.charAt(i))
                --left;

            while (right <= s.length() - 1 && s.charAt(right) == s.charAt(i))
                ++right;

            while (left >= 0 && right <= s.length() - 1 && s.charAt(left) == s.charAt(right)) {
                --left;
                ++right;
            }

            if (maxRight - maxLeft < right - left) {
                maxLeft = left;
                maxRight = right;
            }
        }

        return s.substring(maxLeft + 1, Math.min(maxRight, s.length()));
    }
}

```
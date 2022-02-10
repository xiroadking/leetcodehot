```
package lkanswer;

import java.util.HashMap;
import java.util.Map;

/**
 * 给定一个整数数组 nums和一个整数目标值 target，请你在该数组中找出 和为目标值 target的那两个整数，
 * 并返回它们的数组下标。
 * 你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。
 * 你可以按任意顺序返回答案。
 * <p>
 * 输入：nums = [2,7,11,15], target = 9
 * 输出：[0,1]
 * 解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。
 */
public class HotLK1 {

    public static void main(String[] args) {
        int[] nums = {2, 7, 11, 15};
        int target = 22;

        HotLK1 ts = new HotLK1();
        ts.twoSum(nums, target);
    }

    public int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];

        // 法一：双循环
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    result[0] = i;
                    result[1] = j;
                    break;
                }
            }
        }
        System.out.println("【法一】返回的数组下标->" + result[0] + "," + result[1]);

        // 法二：哈希
        Map<Integer, Integer> map = new HashMap<>();
        for (int n = 0; n < nums.length; n++) {
            int otherAdd = target - nums[n];
            if (map.containsKey(otherAdd)) {
                result[0] = n;
                result[1] = map.get(otherAdd);
            }

            map.put(nums[n], n);
        }

        System.out.println("【法二】返回的数组下标->" + result[0] + "," + result[1]);
        return result;
    }

}
```
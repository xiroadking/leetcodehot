```
package lkanswer;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;
import java.util.stream.Collectors;

/**
 * 给定两个大小分别为 m 和 n 的正序（从小到大）数组nums1 和nums2。请你找出并返回这两个正序数组的 中位数 。
 * <p>
 * 算法的时间复杂度应该为 O(log (m+n)) 。
 */
public class HotLK4 {

    public static void main(String[] args) {
        int[] nums1 = {1, 7, 5};
        int[] nums2 = {2, 6};

        double result = HotLK4.findMedianSortedArrays(nums1, nums2);
        System.out.println(result);
    }

    public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
        List<Integer> list = new ArrayList<>();
        list.addAll(Arrays.stream(nums1).boxed().collect(Collectors.toList()));
        list.addAll(Arrays.stream(nums2).boxed().collect(Collectors.toList()));

        Collections.sort(list);

        if (list.size() == 0) {
            return 0;
        }

        if (list.size() % 2 > 0) {
            return list.get(((list.size() + 1) / 2) - 1);
        } else {
            int a = list.size() / 2;
            return (double) (list.get(a) + list.get(a - 1)) / 2;
        }
    }
}

```
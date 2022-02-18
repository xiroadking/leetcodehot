```
package lkanswer;

import java.util.ArrayList;
import java.util.List;

/**
 * *给你两个非空 的链表，表示两个非负的整数。它们每位数字都是按照逆序的方式存储的，
 * 并且每个节点只能存储一位数字。请你将两个数相加，并以相同形式返回一个表示和的链表。
 * 你可以假设除了数字 0 之外，这两个数都不会以 0开头。
 * <p>
 * 输入：l1 = [2,4,3], l2 = [5,6,4]
 * 输出：[7,0,8]
 * 解释：342 + 465 = 807.
 */
public class HotLK2 {

    public static void main(String[] args) {
        List<Integer> list1 = new ArrayList<>();
        list1.add(2);
        list1.add(4);
        list1.add(3);

        List<Integer> list2 = new ArrayList<>();
        list2.add(5);
        list2.add(6);
        list2.add(4);

        HotLK2.twoNumsAdd(createListNode(list1), createListNode(list2));
    }

    public static ListNode twoNumsAdd(ListNode l1, ListNode l2) {
        if (null == l1 || null == l2) {
            return null;
        }

        ListNode result = new ListNode();
        ListNode head = result;

        // 进位数
        int addFlagNum = 0;
        while (null != l1 || null != l2 || addFlagNum != 0) {
            int val1 = (null != l1 ? l1.val : 0);
            int val2 = (null != l2 ? l2.val : 0);
            int sum = val1 + val2 + addFlagNum;
            // 进位后的值
            head.next = new ListNode(sum % 10);
            head = head.next;
            // 进位的值
            addFlagNum = sum / 10;

            if (null != l1) {
                l1 = l1.next;
            }

            if (null != l2) {
                l2 = l2.next;
            }
        }

        printNode(result);
        return result;
    }

    /**
     * 创建链表
     *
     * @param list
     * @return
     */
    public static ListNode createListNode(List<Integer> list) {
        ListNode firstNode = new ListNode();
        ListNode nextNode = firstNode;
        for (int i : list) {
            ListNode node = new ListNode(i);
            nextNode.next = node;
            nextNode = nextNode.next;
        }

        nextNode = firstNode;
        printNode(nextNode);
        return nextNode;
    }

    /**
     * 打印链表
     *
     * @param listNode
     */
    public static void printNode(ListNode listNode) {
        while (null != listNode) {
            System.out.println("节点：" + listNode.val);
            listNode = listNode.next;
        }
        System.out.println();
    }
}

```


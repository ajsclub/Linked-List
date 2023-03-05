# Linked-List
Linked Question(LeetCode)
1.
Given the head of a singly linked list, return true if it is a 
palindrome
 or false otherwise.

 

Example 1:


Input: head = [1,2,2,1]
Output: true
Example 2:


Input: head = [1,2]
Output: false
 

Constraints:

The number of nodes in the list is in the range [1, 105].
0 <= Node.val <= 9

Answer:-class Solution {
    static ListNode reverseList(ListNode head){
        ListNode prev=null;
        ListNode curr=head;
        ListNode post=null;
        while(curr!=null){
            post=curr.next;
            curr.next=prev;
            prev=curr;
            curr=post;

        }
        return prev;
    }
    public boolean isPalindrome(ListNode head) {
        if(head==null || head.next==null)
           return true;
        ListNode slow=head;
        ListNode fast=head.next;
        while(fast!=null && fast.next!=null){
            slow=slow.next;
            fast=fast.next.next;
        }
        ListNode head2=slow.next;
        slow.next=null;
        head2=reverseList(head2);
        while(head!=null && head2!=null){
            if(head.val!=head2.val)
              return false;
            head=head.next;
            head2=head2.next;
        }
        return true;
        
    }
}
 

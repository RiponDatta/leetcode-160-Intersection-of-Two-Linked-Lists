# leetcode-160-Intersection-of-Two-Linked-Lists

## C#
```C#
public static ListNode GetIntersectionNode(ListNode headA, ListNode headB)
{
    var hs = new Hashtable();
    var temp = headA;
    while (temp != null)
    {
        hs.Add(temp, 1);
        temp = temp.next;
    }
    while (headB != null)
    {
        if (hs.Contains(headB)) return headB;
        headB = headB.next;
    }
    return null;
}
```

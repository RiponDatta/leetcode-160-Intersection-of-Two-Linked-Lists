# leetcode-160-Intersection-of-Two-Linked-Lists

## C#
```C#
public class ListNode
{
    public int val;
    public ListNode next;
    public ListNode(int x) { val = x; }
}

static void Main(string[] args)
{
    var listA = new ListNode(1);
    listA.next = new ListNode(9);
    listA.next.next = new ListNode(1);
    var n = new ListNode(2);
    listA.next.next.next = n;
    listA.next.next.next.next = new ListNode(4);

    var listB = new ListNode(3);
    listB.next = n;

    GetIntersectionNode(listA, listB);
}

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

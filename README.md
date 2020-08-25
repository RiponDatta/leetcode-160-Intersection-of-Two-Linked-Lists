# leetcode 160 - Intersection of Two Linked Lists

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
```
### Solution 1
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

### Solution 2
```C#
public static ListNode GetIntersectionNode(ListNode headA, ListNode headB)
{
    var lenA = GetCount(headA);
    var lenB = GetCount(headB);
    var diff = Math.Abs(lenA - lenB);
    if(lenA > lenB)
        VisitTillDiff(ref headA, diff);
    else
        VisitTillDiff(ref headB, diff);

    while(headA != null)
    {
        if (headA == headB) return headA;
        headA = headA.next;
        headB = headB.next;
    }
    return null;
}

private static void VisitTillDiff(ref ListNode head, int diff)
{
    while (diff > 0)
    {
        head = head.next;
        diff--;
    }
}

private static int GetCount(ListNode node)
{
    var current = node;
    int count = 0;
    while(current != null)
    {
        count++;
        current = current.next;
    }
    return count;
}
```

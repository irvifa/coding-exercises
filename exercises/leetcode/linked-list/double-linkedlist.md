# Double LinkedList

```
class ListNode {

    int val;
    ListNode next;
    ListNode prev;

    ListNode(int x) {
      val = x;
    }
  }
```

```
class LinkedList {
  int size;
  // pseudo-head and pseudo-tail
  ListNode head;
  ListNode tail;

  public LinkedList() {
    size = 0;
    head = new ListNode(0);
    tail = new ListNode(0);
    head.next = tail;
    tail.prev = head;
  }

  /**
   * Get the value of the index-th node in the linked list. If the index is invalid, return -1.
   */
  public int get(int index) {
    // if index is invalid
    if (index < 0 || index >= size) {
      return -1;
    }

    // choose the fastest way: to move from the head
    // or to move from the tail
    ListNode node = head;
    if (index + 1 < size - index) {
      for (int i = 0; i < index + 1; ++i) {
        node = node.next;
      }
    } else {
      node = tail;
      for (int i = 0; i < size - index; ++i) {
        node = node.prev;
      }
    }

    return node.val;
  }

  /**
   * Add a node of value val before the first element of the linked list. After the insertion, the
   * new node will be the first node of the linked list.
   */
  public void addAtHead(int val) {
    ListNode predecessor = head;
    ListNode successor = head.next;

    ++size;
    ListNode toAdd = new ListNode(val);
    toAdd.prev = predecessor;
    toAdd.next = successor;
    predecessor.next = toAdd;
    successor.prev = toAdd;
  }

  /**
   * Append a node of value val to the last element of the linked list.
   */
  public void addAtTail(int val) {
    ListNode successor = tail, predecessor = tail.prev;

    ++size;
    ListNode toAdd = new ListNode(val);
    toAdd.prev = predecessor;
    toAdd.next = successor;
    predecessor.next = toAdd;
    successor.prev = toAdd;
  }

  /**
   * Add a node of value val before the index-th node in the linked list. If index equals to the
   * length of linked list, the node will be appended to the end of linked list. If index is greater
   * than the length, the node will not be inserted.
   */
  public void addAtIndex(int index, int val) {
    // If index is greater than the length,
    // the node will not be inserted.
    if (index > size) {
      return;
    }

    // [so weird] If index is negative,
    // the node will be inserted at the head of the list.
    if (index < 0) {
      index = 0;
    }

    // find predecessor and successor of the node to be added
    ListNode predecessor, successor;
    if (index < size - index) {
      predecessor = head;
      for (int i = 0; i < index; ++i) {
        predecessor = predecessor.next;
      }
      successor = predecessor.next;
    } else {
      successor = tail;
      for (int i = 0; i < size - index; ++i) {
        successor = successor.prev;
      }
      predecessor = successor.prev;
    }

    // insertion itself
    ++size;
    ListNode toAdd = new ListNode(val);
    toAdd.prev = predecessor;
    toAdd.next = successor;
    predecessor.next = toAdd;
    successor.prev = toAdd;
  }

  /**
   * Delete the index-th node in the linked list, if the index is valid.
   */
  public void deleteAtIndex(int index) {
    // if the index is invalid, do nothing
    if (index < 0 || index >= size) {
      return;
    }

    // find predecessor and successor of the node to be deleted
    ListNode predecessor, successor;
    if (index < size - index) {
      predecessor = head;
      for (int i = 0; i < index; ++i) {
        predecessor = predecessor.next;
      }
      successor = predecessor.next.next;
    } else {
      successor = tail;
      for (int i = 0; i < size - index - 1; ++i) {
        successor = successor.prev;
      }
      predecessor = successor.prev.prev;
    }

    // delete pred.next
    --size;
    predecessor.next = successor;
    successor.prev = predecessor;
  }
}
```

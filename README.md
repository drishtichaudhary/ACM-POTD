# ACM-POTD
the first commit

# DrishtiChaudhary_22-3-26_Day-1.md
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/b8e83fd5-f437-455d-8c1b-15b750c5b459" />

# DrishtiChaudhary_23-3-26_Day-1.md
<img width="1847" height="1037" alt="image" src="https://github.com/user-attachments/assets/28ea9d74-24df-41c7-995f-4e733abbe112" />

# DrishtiChaudhary_24-3-26_Day-1.md
- Code:
```
class Solution {
    public int maxProfit(int[] prices) {
        int buyPrice = Integer.MAX_VALUE;
        int maxProfit = 0;

        for(int i=0; i<prices.length; i++){
            if(prices[i] < buyPrice){ //buy stock TODAY at lowest price
                buyPrice = prices[i];
            }
            //prices[i] = TODAY'S selling price
            int profit = prices[i] - buyPrice; // TODAY'S profit

            maxProfit = Math.max(maxProfit, profit); // maxProfit UPTIL NOW vs profit TODAY
        }

        return maxProfit;
    }
}
```

- Screenshot:
  <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/3468aa89-ba47-4076-a67b-12d24cf85f0c" />

# DrishtiChaudhary_25-3-26_Day-1.md
- Code:
```
class Solution {
    public int missingNumber(int[] nums) {
        Arrays.sort(nums);
        HashSet<Integer> set = new HashSet<>();
        HashSet<Integer> set2 = new HashSet<>();

        for(int i=0; i<=nums.length; i++){
            set.add(i);
        }

        for(int i=0; i<nums.length; i++){
            set2.add(nums[i]);
        }

        int res=0;

        for(int val:set){
            if(!set2.contains(val)){
                res=val;
            }
        }

        return res;
    }
}
```

- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/5208a416-e786-43c5-8cd0-f45847e37556" />

# DrishtiChaudhary_26-3-26_Day-1.md
- Code:
```
class Solution {
    public void moveZeroes(int[] nums) {
        for(int i=0; i<nums.length; i++){
            for(int j=i+1; j<nums.length; j++){
                if(nums[i] == 0 && nums[j] != 0){
                    int temp = nums[i];
                    nums[i] = nums[j];
                    nums[j] = temp;
                }
            }
        }
    }
}
```
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/edb3f8ab-3740-4274-b468-6ed702106c4c" />

# DrishtiChaudhary_27-3-26_Day-1.md
- INTERMEDIATE
- Code:
```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        if(nums == null || nums.length<3){
            return new ArrayList<>();
        }

        //sort elements
        Arrays.sort(nums);
        Set<List<Integer>> result = new HashSet<>();

        //now fix 1st element and find the rest 2 elements
        for(int i=0; i<nums.length-2; i++){
            //find other elements using 2Sum
            int left = i+1;
            int right = nums.length-1;

            while(left < right){
                int sum = nums[i] + nums[left] + nums[right];

                if(sum == 0){
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    left++;
                    right--;
                } else if(sum < 0){
                    left++;
                } else{
                    right--;
                }
            }
        }
        return new ArrayList<>(result);
    }
}
```
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d32b2907-8632-49ef-8371-c957ae76f430" />

# DrishtiChaudhary_28-3-26_Day-1.md
189. Rotate Array
- Beginner
- Code:
```
class Solution {
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k = k % n; //handle cases where k > n

        //reverse the entire array
        reverse(nums, 0, n - 1);
        //reverse the first k elements
        reverse(nums, 0, k - 1);
        //reverse the remaining elements
        reverse(nums, k, n - 1);
    }

    public void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;

            start++;
            end--;
        }
    }
}
```
- Screenshot:
<img width="1919" height="1027" alt="image" src="https://github.com/user-attachments/assets/783f7e4a-abe3-475b-b6f5-50e0e422cc5b" />

# DrishtiChaudhary_29-3-26_Day-1.md
206. Reverse Linked List
- Code:
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode curr = head;
        ListNode next;

        while(curr!=null){
            next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        head = prev;
        return head;
    }
}
```
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/247dad14-25c2-405a-890d-06d72abb453e" />

# DrishtiChaudhary_30-3-26_Day-1.md
141. Linked List Cycle
- Code:
```
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        HashSet<ListNode> set = new HashSet<>();

        ListNode temp = head;
        while(temp!=null){
            if(set.contains(temp)){ //agar element set mein already hai -> cycle hoga, kyuki node humesha unique hogi "no cycle" wali linked list mein
                return true; //cylce present hai
            }
            set.add(temp);
            temp = temp.next;
        }

        return false; //no cycle
    }
}
```
- Screenshot:
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/dd0a362e-e0a9-4579-9661-4a638f10fb32" />

# DrishtiChaudhary_31-3-26_Day-1.md
21. Merge Two Sorted Lists
- Code:
```
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode temp1 = list1;
        ListNode temp2 = list2;
        
        ListNode returnNode = new ListNode(Integer.MIN_VALUE);
        ListNode headNode = returnNode;

        while(temp1 != null && temp2 != null){

            if(temp1.val > temp2.val){
                returnNode.next = temp2;
                temp2 = temp2.next;
            } else{
                returnNode.next = temp1;
                temp1 = temp1.next;
            }

            returnNode = returnNode.next;
        }

        if(temp1 == null){
            returnNode.next = temp2;
        } else if(temp2 == null){
            returnNode.next = temp1;
        }

        return headNode.next;
    }
}
```
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e5258e40-d640-4ef6-bee3-38b435e8d0e4" />

# DrishtiChaudhary_1-4-26_Day-1.md
21. Merge Two Sorted Lists
- Code:
```
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode temp1 = list1;
        ListNode temp2 = list2;
        
        ListNode returnNode = new ListNode(Integer.MIN_VALUE);
        ListNode headNode = returnNode;

        while(temp1 != null && temp2 != null){

            if(temp1.val > temp2.val){
                returnNode.next = temp2;
                temp2 = temp2.next;
            } else{
                returnNode.next = temp1;
                temp1 = temp1.next;
            }

            returnNode = returnNode.next;
        }

        if(temp1 == null){
            returnNode.next = temp2;
        } else if(temp2 == null){
            returnNode.next = temp1;
        }

        return headNode.next;
    }
}
```
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ef1bf3ee-fc73-4fca-b914-76e1007e8db8" />

# DrishtiChaudhary_2-4-26_Day-1.md
83. Remove duplicates from sorted list
- Code:
```
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode curr = head;
        while (curr != null && curr.next != null) {
            if (curr.val == curr.next.val) {
                curr.next = curr.next.next;
            } else {
                curr = curr.next;
            }
        }
        return head;
    }
}
```
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ef02df6b-d35a-4535-a59d-83111d8e7fab" />

# DrishtiChaudhary_5-4-26_Day-1.md
- Code:
```
class Solution {
    public boolean isValid(String s) {
        Deque<Character> stack = new ArrayDeque<>();

        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);

            //opening bracket -> push
            if (ch == '(' || ch == '[' || ch == '{') {
                stack.push(ch);
            } 
            else { //closing bracket

                if (stack.isEmpty()) return false;

                char top = stack.peek();

                if ((top == '(' && ch == ')') ||
                    (top == '[' && ch == ']') ||
                    (top == '{' && ch == '}')) {
                    stack.pop();
                } else {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }
}
```
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/40aa176e-781d-4bbe-a6bb-aa21a9331317" />

# DrishtiChaudhary_6-4-26_Day-1.md
```
class MyQueue {
    Stack<Integer> s1 = new Stack<>();
    Stack<Integer> s2 = new Stack<>();

    public MyQueue() {

    }
    
    public void push(int x) {
        //push all elements of stack 1 in stack1
        while(!s1.isEmpty()){
            s2.push(s1.pop());
        }
        // add the new element in stack1
        s1.push(x);
        //push all elements from stack2 back in stack1
        while(!s2.isEmpty()){
            s1.push(s2.pop());
        }
    }
    
    public int pop() {
        if(empty()){
            return -1;
        }
        return s1.pop();
    }
    
    public int peek() {
        if(empty()){
            return -1;
        }
        return s1.peek();
    }
    
    public boolean empty() {
        return s1.isEmpty();
    }
}

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */
```
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9872d9b7-d16f-40f3-98a9-6086f04ac68f" />

# DrishtiChaudhary_7-4-26_Day-1.md
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/faf8efd5-6ce6-4772-89a7-9891f93d2296" />

# DrishtiChaudhary_8-4-26_Day-1.md
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2a61a0db-1fb7-4997-9405-ea230b6bf29e" />

# DrishtiChaudhary_9-4-26_Day-1.md
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ca49f9d5-2018-4c9d-b30b-5fe30e5263e1" />

# DrishtiChaudhary_10-4-26_Day-1.md
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b6b492ad-ee77-4572-801f-b4e4faa2c1df" />

# DrishtiChaudhary_12-4-26_Day-1.md
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ac2339bb-591f-4af2-b79e-7af674fad99e" />

# DrishtiChaudhary_13-4-26_Day-1.md
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/962e7f62-3379-4112-92f9-f9d8db78c133" />

# DrishtiChaudhary_14-4-26_Day-1.md
- Screenshot:
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/74615b77-e8ac-4bbe-bb26-1c3c03275d3f" />

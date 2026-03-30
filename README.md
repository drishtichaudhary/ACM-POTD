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

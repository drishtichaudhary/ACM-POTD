# ACM-POTD
the first commit

# DrishtiChaudhary_22-3-26_Day-1.md
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/b8e83fd5-f437-455d-8c1b-15b750c5b459" />

# DrishtiChaudhary_23-3-26_Day-1.md
<img width="1847" height="1037" alt="image" src="https://github.com/user-attachments/assets/28ea9d74-24df-41c7-995f-4e733abbe112" />

# DrishtiChaudhary_24-3-26_Day-1.md
- Code:
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

- Screenshot:
  <img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/3468aa89-ba47-4076-a67b-12d24cf85f0c" />

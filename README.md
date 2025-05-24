# ANAGRAM
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        
        int[] freq = new int[26];
        for (int i = 0; i < s.length(); i++) {
            freq[s.charAt(i) - 'a']++;
            freq[t.charAt(i) - 'a']--;
        }
        
        for (int i = 0; i < freq.length; i++) {
            if (freq[i] != 0) {
                return false;
            }
        }
        
        return true;
    }
}

# FIND THE PEAKS

class Solution {
    public List<Integer> findPeaks(int[] mountain) {
        List<Integer> nm=new ArrayList<>();
        for(int i=1;i<mountain.length-1;i++)
        {
            if(mountain[i]>mountain[i-1] && mountain[i]>mountain[i+1])
            {
                nm.add(i);
            }
        }
        return nm;
    }
}

# BUY TWO CHOCOLATES

class Solution {
    public int buyChoco(int[] arr, int key) {

        int ans = Integer.MAX_VALUE;
        int fin;
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr.length; j++) {
                if (i != j ) {
                    int sum = arr[i] + arr[j];
                    ans = Math.min(ans, sum);
                }
            }
        }
       
        fin = key - ans;
        if(fin>=0){
        return fin;
        }
        else{
            return key;
        }
    }
}

# HOUSE ROBBER

class Solution {
    public int rob(int[] nums) {
        int rob = 0;
        int norob = 0;
        for (int i = 0; i < nums.length; i ++) {
            int newRob = norob + nums[i];
            int newNoRob = Math.max(norob, rob);
            rob = newRob;
            norob = newNoRob;
        }
        return Math.max(rob, norob);
    }
}

# pass the pillow

class Solution {
    public int passThePillow(int n, int time) {
        int completed = time / (n-1);
        int remaining = time % (n-1);
        int ans = 0;
        if (completed % 2 != 0) {
            ans = n - remaining;
        } else {
            ans = remaining + 1;
        }
        return ans;
    }
}

# Count Hills and Valleys in an Array

class Solution {
    public int countHillValley(int[] a) {
        int r = 0, left = a[0];
        for(int i = 1; i < a.length - 1; i++)
            if(left < a[i] && a[i] > a[i + 1] || left > a[i] && a[i] < a[i + 1]){
                r++;
                left = a[i];
            }
        return r;
    }
}

# Check if Number is a Sum of Powers of Three

class Solution {
    public boolean checkPowersOfThree(int n) {
        int cap=16; 
        int[] arr=new int[cap];
        for(int i=0; i<cap; i++){
            arr[i]=(int)Math.pow(3,i);
        }
        for(int i=cap-1; i>=0; i--){
            if(n>=arr[i]){
                n-=arr[i];
            }            
            if(n==0){
                return true;
            }
        }

        return false;
    }
}

# Calculate Money in Leetcode Bank

class Solution {
    public int totalMoney(int n) {
        int week_count = n / 7;
        int remaining_days = n % 7;
        
        int total = ((week_count * (week_count - 1)) / 2) * 7; // Contribution from complete weeks
        total += week_count * 28; // Contribution from complete weeks (additional on Mondays)
        total += ((remaining_days * (remaining_days + 1)) / 2) + (week_count * remaining_days); // Contribution from remaining days
        
        return total;
    }
}

# Best Poker Hand

class Solution {
    public String bestHand(int[] ranks, char[] suits) {
        Map<Integer, Integer> mapr = new HashMap<>();
        Map<Character, Integer> maps = new HashMap<>();
        for (int n : ranks)
            mapr.put(n, mapr.getOrDefault(n, 0) + 1);
        for (char c : suits)
            maps.put(c, maps.getOrDefault(c, 0) + 1);

        if (maps.size() == 1)
            return "Flush";
        int count = 0;
        for (int rank : mapr.keySet()) count = Math.max(count, mapr.get(rank));
        
        if (count >= 3) 
            return "Three of a Kind";
        else if (count == 2) 
            return "Pair";
        else
            return "High Card";
    }
}


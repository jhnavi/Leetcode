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

#FIND THE PEAKS

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

#BUY TWO CHOCOLATES

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

#HOUSE ROBBER

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

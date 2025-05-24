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

# Bulls and Cows

class Solution:
    def getHint(self, secret: str, guess: str) -> str:
        b,c=0,0
        s,g=[],[]
        for i in range(len(secret)):
            if secret[i]==guess[i]:
                b+=1
            else:
                s.append(secret[i])
                g.append(guess[i])
        print(g,s)
        for i in g:
            if i in s:
                c+=1
                s.remove(i)
        return str(b)+'A'+str(c)+'B'

# Daily Temperatures



class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        for(int i=0;i<temperatures.length;i++){
            if(i==temperatures.length-1){
                temperatures[i]=0;
                break;
            }
            for(int j=i+1;j<temperatures.length;j++){
                if(temperatures[i]<temperatures[j]){
                    temperatures[i]=j-i;
                    break;
                }
                if(j==temperatures.length-1){
                    temperatures[i]=0;
                    break;
                }
            }
        }
        return temperatures;
    }
}

# Rotate Image

class Solution {
    public void rotate(int[][] matrix) {
        int edgeLength = matrix.length;

        int top = 0;
        int bottom = edgeLength - 1;

        while (top < bottom) {
            for (int col = 0; col < edgeLength; col++) {
                int temp = matrix[top][col];
                matrix[top][col] = matrix[bottom][col];
                matrix[bottom][col] = temp;
            }
            top++;
            bottom--;
        }

        for (int row = 0; row < edgeLength; row++) {
            for (int col = row + 1; col < edgeLength; col++) {
                int temp = matrix[row][col];
                matrix[row][col] = matrix[col][row];
                matrix[col][row] = temp;
            }
        }        
    }
}

# Text Justification

class Solution {
    public List<String> fullJustify(String[] words, int maxWidth) {
        List<String> ans = new ArrayList<>();
        int n = words.length;
        int i = 0;
        
        while (i < n) {
            int charCnt = 0;
            int j = i;
            while (j < n && charCnt + words[j].length() <= maxWidth) {
                charCnt += words[j].length() + 1; // +1 for space; beacuse some situation might arrise where you take the group of words whose char counts exactly to the maxWidth, now here the text can not be justified. Hence assume a minimum of single space
                j++;
            }
            
            StringBuilder sb = new StringBuilder();
            int spaces = maxWidth - (charCnt - (j - i));
            int gaps = j - i - 1;
            
        
//if it is last line or only one word, then we need to keep it left justified
            if (j == n || gaps == 0) {
                for (int k = i; k < j; k++) {
                    sb.append(words[k]);
                    if (k < j - 1) sb.append(" ");
                }
                while (sb.length() < maxWidth) sb.append(" ");
            } else {
                for (int k = i; k < j; k++) {
                    sb.append(words[k]);
                    if (k < j - 1) {
                        int spaceToAdd = spaces / gaps + (k - i < spaces % gaps ? 1 : 0);
                        for (int l = 0; l < spaceToAdd; l++) {
                            sb.append(" ");
                        }
                    }
                }
            }
            
            ans.add(sb.toString());
            i = j;
        }
        
        return ans;
    }
}

# zigzag Conversion

class Solution {
    public String convert(String s, int numRows) {
        if (numRows == 1) return s;
        StringBuilder a = new StringBuilder();
        for (int i = 0; i < numRows; i++) {
            for (int j = i; j < s.length(); j += (2 * (numRows - 1))) {
                a.append(s.charAt(j));
                if (i > 0 && i < numRows - 1 && j + (2 * (numRows - 1)) - (2 * i) < s.length()) {
                    a.append(s.charAt(j + (2 * (numRows - 1)) - (2 * i)));
                }
            }
        }
        return a.toString();
    }
}

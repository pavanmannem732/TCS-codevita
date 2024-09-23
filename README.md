# TCS-codevita
TCS codevita question and answers
hello guys 



import java.util.*;

public class BeautifulArray {
 public static void main(String[] args) {
 Scanner scanner = new Scanner(System.in);
 int N = scanner.nextInt();
 int[] arr = new int[N];
 for (int i = 0; i < N; i++) {
 arr[i] = scanner.nextInt();
 }
 
 int swaps = countSwapsToMakeBeautiful(arr);
 System.out.println(swaps);
 }

 private static int countSwapsToMakeBeautiful(int[] arr) {
 int[] sortedArr = arr.clone();
 Arrays.sort(sortedArr);
 Map indexMap = new HashMap();
 for (int i = 0; i < arr.length; i++) {
 indexMap.put(sortedArr[i], i);
 }

 boolean[] visited = new boolean[arr.length];
 int swaps = 0;

 for (int i = 0; i < arr.length; i++) {
 if (visited[i] || arr[i] == sortedArr[i]) {
 continue;
 }

 int cycleSize = 0;
 int j = i;

 while (!visited[j]) {
 visited[j] = true;
 j = indexMap.get(arr[j]);
 cycleSize++;
 }

 if (cycleSize > 0) {
 swaps += (cycleSize - 1);
 }
 }

 return swaps;
 }
}

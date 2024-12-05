# Partition array into N subsets with balanced sum

```
/*
Give you one sorted array, please put them into n buckets, we need to ensure we get n sub array with approximately equal weights.
Example;
input {1, 2, 3, 4, 5} n = 3
output [[[5],[1,4],[2,3]];
*/
// "static void main" must be defined in a public class.
public class Main {
	// O(N log K)
	public static List<List<Integer>> part(int[] nums, int n) {
		int[] sums = new int[n];
		PriorityQueue<Integer> pq = new PriorityQueue<>(
			(a, b) -> sums[a.intValue()] - sums[b.intValue()]);
		List<List<Integer>> result = new ArrayList<>();
		
		for (int i = 0; i < n; i++) {
			result.add(new ArrayList<>());
			pq.add(i);
		}
		
		for (int i = nums.length - 1; i >= 0; i--) {
			int c = pq.poll();
			result.get(c).add(nums[i]);
			sums[c] += nums[i];
			pq.add(c);
		}
		
		return result;
	}


	public static void main(String[] args) {
		List<List<Integer>> result = part(
			new int[] {1,2,3,4,5,6,7,8,9,10}, 3);
		System.out.println(result);
	}
}
```

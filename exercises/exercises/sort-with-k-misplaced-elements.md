# Sort with K Misplaced Elements

```
// "static void main" must be defined in a public class.
/**
Given a sorted n-size array, there are k elements have been changed i.e. [1, 3, 5, 6, 4, 2, 12] (it might be changed from [1, 3, 5, 6, 7, 8, 12] with k = 2). Important to know is that k is unknown and k is much smaller than n. The task is to re-sort the entire array.
The interviewer wants O(n) solution. I bombed this one. In the end, the interviewer kind of fed the solution to me. What he suggested: a. break the array into two: one sorted array and one unsorted array e.g. [1, 3, 5, 12] and [6, 4, 2]. This takes O(n) b. Sort the unsorted array. This takes O(klogk) c. Merge two sorted arrays. This takes O(n). Because k is very small, so in the end O(n) + O(klogk) ~= O(n).
Does this solution make sense to you ? In O(n) how can we split array into sorted and unsorted with unsorted arry being of size k?

*/
public class Main {
    static Pair<List<Integer>, List<Integer>> getMisplacedElement(List<Integer> nums) {
        List<Integer> outOfOrder = new ArrayList<>();
        List<Integer> inPlace = new ArrayList<>();
        inPlace.add(nums.get(0));
        for (int i = 1; i < nums.size(); i++) {
            if (nums.get(i) < inPlace.get(inPlace.size() - 1)) {
                outOfOrder.add(nums.get(i));
            } else {
                inPlace.add(nums.get(i));
            }
        }
        return new Pair<>(inPlace, outOfOrder);
    }
    
    // O(N + k log(k)), k is number of misplaced element
    static List<Integer> merge(List<Integer> inPlace, List<Integer> outOfOrder) {
        Collections.sort(outOfOrder);
        List<Integer> sorted = new ArrayList<>();
        int i = 0;
        int j = 0;
        while (i < inPlace.size() && j < outOfOrder.size()) {
            if (inPlace.get(i) < outOfOrder.get(j)) {
                sorted.add(inPlace.get(i));
                i++;
            } else {
                sorted.add(outOfOrder.get(j));
                j++;
            }
        }
        
        while (i < inPlace.size()) {
            sorted.add(inPlace.get(i));
            i++;
        }
        
        while (j < outOfOrder.size()) {
            sorted.add(outOfOrder.get(j));
            j++;
        }
        
        return sorted;
    }
    
    static void test(List<Integer> nums, List<Integer> expected) {
            Pair<List<Integer>, List<Integer>>  res = getMisplacedElement(nums);
            List<Integer> inPlace = res.getKey();
            List<Integer> outOfOrder = res.getValue();
            List<Integer> actual = merge(inPlace, outOfOrder);
            for (int i = 0; i < expected.size(); i++) {
                assert actual.get(i) == expected.get(i);
            }
            assert actual.toString().equals(expected.toString());
            System.out.println(actual.toString());
            System.out.println(expected.toString());
    }
    
    public static void main(String[] args) {
        List<Pair<List<Integer>, List<Integer>>> testCases = 
            new ArrayList<>();
        testCases.add(
            new Pair(
                Arrays.asList(1, 4, 5, 2, 3, 10, 12),
                Arrays.asList(1, 2, 3, 4, 5, 10, 12)));
        testCases.add(
            new Pair(
                Arrays.asList(1, 10, 5, 2, 3, 4, 12),
                Arrays.asList(1, 2, 3, 4, 5, 10, 12)));
        for (Pair<List<Integer>, List<Integer>> testCase: testCases) {
            test(testCase.getKey(), testCase.getValue());
        }
    }
}
```

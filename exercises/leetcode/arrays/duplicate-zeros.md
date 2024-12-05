# Duplicate Zeros

```
    public void duplicateZeros(int[] arr) {
        int countZeros = Arrays.stream(arr).filter(i -> i == 0).map(i -> 1).sum();
        int len = arr.length + countZeros;
        int i = arr.length - 1;
        int j = len - 1;
        while (i < j) {
            if (arr[i] != 0) {
                if (j < arr.length) {
                    arr[j] = arr[i];
                }
            } else {
                // Copy zero twice
                if (j < arr.length) {
                    arr[j] = arr[i];
                }
                j--;
                if (j < arr.length) {
                    arr[j] = arr[i];
                }
            }
            i--;
            j--;
        }
    }
```

# Jurassic Park

Examples:

* Given X = \[4, 0, 2, −2], Y = \[4, 1, 2, −3] and colors = "RGRR", your function should return 2. The circle contains points (0, 1) and (2, 2), but not points (−2, −3) and (4, 4).
* Given X = \[1, 1, −1, −1], Y = \[1, −1, 1, −1] and colors = "RGRG", your function should return 4. All points lie inside the circle.
* Given X = \[1, 0, 0], Y = \[0, 1, −1] and colors = "GGR", your function should return 0. Any circle that contains more than zero points has an unequal number of green and red points.
* Given X = \[5, −5, 5], Y = \[1, −1, −3] and colors = "GRG", your function should return 2.
* Given X = \[3000, −3000, 4100, −4100, −3000], Y = \[5000, −5000, 4100, −4100, 5000] and colors = "RRGRG", your function should return 2.

{% embed url="https://app.codility.com/cert/view/certMBFV3M-PTC6X4D6SDB4PMXN/" %}
Awards
{% endembed %}

```
// O N log N

import java.util.*;
class Solution {
    class Pair {
        private int val;
        private char color;

        public Pair(int val, char color) {
            this.val = val;
            this.color = color;
        }

        public int getVal() {
            return val;
        }

        public char getColor() {
            return color;
        }
    }
    public int solution(int[] X, int[] Y, String colors) {
        // write your code in Java SE 11
        int r = 0;
        int g = 0;
        int answer = 0;
        List<Pair> lines = new ArrayList<>();
        for (int i = 0; i < X.length; i++) {
            lines.add(new Pair(X[i]*X[i] + Y[i]*Y[i], colors.charAt(i)));
        }

        lines.sort((Pair a, Pair b) -> a.getVal() - b.getVal())
        ;

        int prev = 0;
        for (Pair line: lines) {
            if (prev == line.getVal()) {
                if(line.getColor() == 'R') {
                    r++;
                } else {
                    g++;
                }
            } else {
                if (r == g) {
                    answer = r + g;
                }
                prev = line.getVal();
                if (line.getColor() == 'R') {
                    r++;
                } else {
                    g++;
                }
            }
        }

        if (r == g) {
            answer = r + g;
        }
        return answer;
    }
}
```

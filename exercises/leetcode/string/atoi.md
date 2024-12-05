# Atoi

```
class Solution {
    public int myAtoi(String input) {
        final int multiplier = 10;
        int sign = 1; 
        int result = 0; 
        int index = 0;
        int n = input.length();
        
        // Discard all spaces from the beginning of the input string.
        while (index < n && input.charAt(index) == ' ') { 
            index++; 
        }
        
        // sign = +1, if it's positive number, otherwise sign = -1. 
        if (index < n && isSign(input.charAt(index))) {
            if (input.charAt(index) == '-')
                sign = -1;
            index++;
        }
        
        // Traverse next digits of input and stop if it is not a digit
        while (index < n && Character.isDigit(input.charAt(index))) {
            int digit = toInteger(input.charAt(index));

            // Check overflow and underflow conditions. 
            if ((result > Integer.MAX_VALUE / multiplier) || 
                (result == Integer.MAX_VALUE / multiplier && digit > Integer.MAX_VALUE % multiplier)) {     
                // If integer overflowed return 2^31-1, otherwise if underflowed return -2^31.    
                return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
            
            // Append current digit to the result.
            result *= multiplier;
            result += digit;
            index++;
        }
        
        return sign * result;
    }
    
    private int toInteger(char c) {
        return c - '0';
    }
    
    private boolean isSign(char c) {
        return (c == '+' || c == '-');
    }
}
```

# Add Binary Numbers

```
import java.util.*;

class Solution {
    public String solve(String a, String b) {
        if(a==null || a.length()==0)
            return b;
        if(b==null || b.length()==0)
            return a;
    
        int pa = a.length()-1;
        int pb = b.length()-1;
    
        int flag = 0;
        StringBuilder sb = new StringBuilder();
        while(pa >= 0 || pb >=0){
            int va = 0;
            int vb = 0;
    
            if(pa >= 0){
                va = a.charAt(pa)=='0'? 0 : 1;    
                pa--;
            }
            if(pb >= 0){
                vb = b.charAt(pb)=='0'? 0: 1;
                pb--;
            }
    
            int sum = va + vb + flag;
            if(sum >= 2){
                sb.append(String.valueOf(sum-2));
                flag = 1;
            }else{
                flag = 0;
                sb.append(String.valueOf(sum));
            }
        }
    
        if(flag == 1){
            sb.append("1");
        }
    
        String reversed = sb.reverse().toString();
        return reversed;
    }
}
```

# Log

```
// "static void main" must be defined in a public class.
/**
A long running webserver is writing to a log file, one request summary per line. 
Here is an example file: 

# timestamp(millis), URL, status, processing time
1000001, /index.html, 200, 150 
1000002, /article/1234.html, 500, 1 
1000005, /index.html, 200, 50 
1001000, /article/4321.html, 200, 10

Return all the input timestamp but associated with the number of requests being processed at the time of the timestamp.

Output :
1000001 --> 1
1000002 --> 2  (since the first process is still running, timestamp 1000002 would have two processes running)
1000005 --> 2  (since the first process is still running, timestamp 1000005 would have two processes running)
1001000 --> 1
*/

public class Main {
    static class Log {
        long startTime;
        String path;
        int processingTime;
        int status;
        
        public Log(
            long startTime,
            String path,
            int processingTime,
            int status) {
            this.startTime = startTime;
            this.path = path;
            this.processingTime = processingTime;
            this.status = status;
        }
    }
    
    static Map<Long, Long> getProcesing(List<Log> logs) {
        Map<Long, Long> res = new HashMap<>();
        PriorityQueue<Long> pq = new PriorityQueue<>();
        for (Log log: logs) {
            long startTime = log.startTime;
            long endTime = startTime + log.processingTime;
            res.put(startTime, 1L);
            
            while (!pq.isEmpty()) {
                if (startTime <= pq.peek()) {
                    res.put(startTime, (long) pq.size() + 1);
                    break;
                } else {
                    pq.poll();
                }
            }
            pq.offer(endTime);
        }
        return res;
    }
    
    public static void main(String[] args) {
        System.out.println("Hello World!");
        List<Log> logs = Arrays.asList(
            new Log(1000001, "/index.html", 200, 150),
            new Log(1000002, "/article/1234.html", 500, 1),
            new Log(1000005, "/index.html", 200, 50), 
            new Log(1001000, "/article/4321.html", 200, 10));
        
        Map<Long, Long> res = getProcesing(logs);
        for (Long key: res.keySet()) {
            System.out.println(key + " " + res.get(key));
        }
    }
}
```

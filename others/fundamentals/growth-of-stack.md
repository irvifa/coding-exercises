# Growth of Stack

Stack typically contains local variables with information that usually retrieved when the function is being executed. Stack will grow downward or upward depending on the system architecture. To check the direction growth of the stack we can compare the address of two local variables.

```
// This function will return 1 if the stack is going upwards, and otherwise.
int is_going_upward(const int *main_addess) {
    int local_address;
    return (main_addess < &local_address);
}
```

# 1342. Number of Steps to Reduce a Number to Zero
### O(N)

```C#

public class Solution {
    public int NumberOfSteps(int num) {
        return Calculate(num, 0);
    }
    
    private int Calculate(int num, int count)
    {
        if (num == 0) return count;

        if (num % 2 == 0)
        {
            num /= 2;
        }
        else
        {
            num -= 1;
        }

        return Calculate(num, ++count);
    }
}

```

# 1116. Print Zero Even Odd
### O(N)

```C#

using System.Threading;

public class ZeroEvenOdd {
    private int n;
    AutoResetEvent zeroEvent = new AutoResetEvent(false);
    AutoResetEvent evenEnvet = new AutoResetEvent(false);
    AutoResetEvent oddEvent = new AutoResetEvent(false);
    
    private int count;
    
    public ZeroEvenOdd(int n) {
        this.n = n;
        
        count = 0;
        
        zeroEvent.Set();
    }

    // printNumber(x) outputs "x", where x is an integer.
    public void Zero(Action<int> printNumber) {
        while (true) {
            zeroEvent.WaitOne();
            
            printNumber(0);
            
            count++;
            
            if (count % 2 == 0) {
                evenEvent.Set();
            }
            else {
                oddEvent.Set();
            }
        }
    }

    public void Even(Action<int> printNumber) {
        while (true) {
            evenEvent.WaitOne();
            if (count > n) return;
            
            printNumber(count);
            
            zeroEvent.Set();
        }
    }

    public void Odd(Action<int> printNumber) {
        while (true) {
            oddEvent.WaitOne();
            if (count > n) return;
            
            printNumber(count);
            
            zeroEvent.Set();
        }
    }
}

```

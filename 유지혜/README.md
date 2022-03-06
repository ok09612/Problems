# 1342. Number of Steps to Reduce a Number to Zero
public int NumberOfSteps(int num)
    {
        int result = 0;

        while (num > 0)
        {
            int odd = num % 2;
            if (odd == 0)
            {
                num = num / 2;
            }
            else
            {
                num = num - odd;
            }
            result++;
        }

        return result;
    }


# 1116. Print Zero Even Odd
public class ZeroEvenOdd
    {
        private int n;

        AutoResetEvent zeroEvent = new AutoResetEvent(true);
        AutoResetEvent evenEvent = new AutoResetEvent(false);
        AutoResetEvent oddEvent = new AutoResetEvent(false);

        public ZeroEvenOdd(int n)
        {
            this.n = n;
            Thread tzero = new Thread(new ParameterizedThreadStart(Zero));
            Thread teven = new Thread(new ParameterizedThreadStart(Even));
            Thread teodd = new Thread(new ParameterizedThreadStart(Odd));
            tzero.Start();
            teven.Start();
            teodd.Start();
        }

        // printNumber(x) outputs "x", where x is an integer.
        public void Zero(object printNumber)
        {
            Action<int> print = new Action<int>(PrintNumber);
            int i = 1;
            while (i <= n)
            {
                zeroEvent.WaitOne();
                print(0);
                evenEvent.Set();
                i++;
            }
            oddEvent.Set();
        }

        public void Even(object printNumber)
        {
            Action<int> print = new Action<int>(PrintNumber);
            int i = 1;
            while (i < n)
            {
                evenEvent.WaitOne();
                print(i);
                i++;
                zeroEvent.Set();
            }
        }

        public void Odd(object printNumber)
        {
            Action<int> print = new Action<int>(PrintNumber);
            oddEvent.WaitOne();
            print(n);
        }

        private void PrintNumber(int i)
        {
            Console.Write(i);
        }
    }    
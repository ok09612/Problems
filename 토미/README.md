# Problems

https://leetcode.com/problems/sort-colors/

``` C#
public class Solution {
    public void SortColors(int[] nums) {
         new Quick().Sort(nums);
    }
}

   public class Sorter
    {
        protected void Write(int[] array)
        {
            for (int i = 0; i < array.Length; i++)
            {
                Console.Write(array[i] + "  ");
            }
            Console.WriteLine();
        }

        protected void Swap(int[] array, int index1, int index2)
        {
            int tmp = array[index1];

            array[index1] = array[index2];

            array[index2] = tmp;
        }
    }
    interface ISorter
        
    {
        void Sort(int[] array);
    }

    class Quick : Sorter, ISorter
    {
        Random random = new Random();

        public void Sort(int[] array)
        {
            //Write(array);

            int leftIndex = 0;
            int rightIndex = array.Length - 1;

            QuickSort(array, leftIndex, rightIndex);

            //Write(array);
        }

        void SwapAndSetPivot(int[] array, int index, ref int pivot)
        {
            if (index > pivot)
            {
                if (array[index] <= array[pivot])
                {
                    Swap(array, index, pivot);

                    pivot = index;
                }
            }
            else if (index < pivot)
            {
                if (array[index] >= array[pivot])
                {
                    Swap(array, index, pivot);

                    pivot = index;
                }
            }
        }

        private void QuickSort(int[] array, int leftIndex, int rightIndex)
        {
            int gap = rightIndex - leftIndex + 1;

            if (gap == 2)
            {
                if (array[leftIndex] > array[rightIndex])
                {
                    Swap(array, leftIndex, rightIndex);
                }

                return;
            }
            else if (gap > 1)
            {
                //make a pivot number
                int pivot = random.Next(leftIndex, rightIndex);

                Swap(array, pivot, rightIndex);

                pivot = rightIndex;

                int left = leftIndex;
                int right = rightIndex - 1;

                while (true)
                {
                    while (array[left] <= array[pivot] && left < right)
                    {
                        left++;
                    }

                    if (left == right)
                    {
                        if (array[left] >= array[pivot])
                        {
                            Swap(array, left, pivot);
                        }

                        pivot = left;
                        //left
                        QuickSort(array, leftIndex, pivot);
                        //right
                        QuickSort(array, pivot + 1, rightIndex);

                        break;
                    }

                    while (array[right] >= array[pivot] && left < right)
                    {
                        right--;
                    }

                    if (left == right)
                    {
                        if (array[right] > array[pivot])
                        {
                            Swap(array, right, pivot);
                        }


                        pivot = right;

                        //left
                        QuickSort(array, leftIndex, pivot);
                        //right
                        QuickSort(array, pivot + 1, rightIndex);

                        break;
                    }

                    Swap(array, left, right);
                }
            }
        }
    }
```
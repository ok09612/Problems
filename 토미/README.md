# Problems

https://leetcode.com/problems/merge-sorted-array/

``` C#
public class Solution
{
	public void Merge(int[] nums1, int m, int[] nums2, int n)
	{
        //전체 뒷쪽부터 채워넣기위한 전체 인덱스
		var currentIndex = nums1.Length - 1;

        //각 배열별 인덱스로 사용하기위해 1 빼기
		m--;
		n--;

		while (m >= 0 && n >= 0)
		{
			if (nums1[m] > nums2[n])
			{
				nums1[currentIndex--] = nums1[m--];
			}
			else
			{
				nums1[currentIndex--] = nums2[n--];
			}
		}

        //남아있는 것이 있다면 다 넣고 끝내버리기
		if (m >= 0)
		{
			while(currentIndex > -1)
			{
				nums1[currentIndex--] = nums1[m--];
			}
			return;
		}

		if(n >= 0)
		{
			while (currentIndex > -1)
			{
				nums1[currentIndex--] = nums2[n--];
			}
			return;
		}
	}
}
```
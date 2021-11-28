# Problems

https://leetcode.com/problems/generate-parentheses/

``` C#
public class Solution
{
	public IList<string> GenerateParenthesis(int n)
	{
		var result = new List<string>();

		var openCount = n;
		var closeCount = n;

		Generate(string.Empty, openCount, closeCount, result);

		return result;
	}

	private void Generate(string text, int openCount, int closeCount, List<string> result)
	{
		if (openCount == 0 && closeCount == 0)
		{
			result.Add(text);
			return;
		}

		if (openCount > 0)
		{
			Generate(text + "(", openCount - 1, closeCount, result);
		}

		if (openCount < closeCount)
		{
			Generate(text + ")", openCount, closeCount - 1, result);
		}
	}
}
```

https://leetcode.com/problems/palindrome-number/

``` C#
public class Solution
{
	public bool IsPalindrome(int x)
	{
		if (x < 0)
		{
			return false;
		}

		if (x < 10)
		{
			return true;
		}

		var value = x;

		var dequeue = new DoubleEndedQueue<int>();
		var length = 0;

		while (value > 0)
		{
			var tail = value % 10;

			dequeue.FrontEnqueue(tail);

			value /= 10;
			length++;
		}

		for (int i = 0; i < length / 2; i++)
		{
			var forward = dequeue.GetForward();
			var backward = dequeue.GetBackward();

			if (forward != backward)
			{
				return false;
			}
		}

		return true;
	}
}

public class DoubleEndedQueue<T>
{
	public T Forward {
		get
		{
			if (ForwardNode == null)
			{
				throw new Exception($"{nameof(Forward)} is Empty");
			}
			else
			{
				return ForwardNode.Value;
			}
		}
	}

	public T Backward {
		get
		{
			if (BackwardNode == null)
			{
				throw new Exception($"{nameof(Backward)} is Empty");
			}
			else
			{
				return BackwardNode.Value;
			}
		}
	}

	private Node<T> ForwardNode { get; set; }

	private Node<T> BackwardNode { get; set; }

	public T GetForward()
	{
		if (ForwardNode == null)
		{
			throw new Exception($"{nameof(Forward)} is Empty");
		}

		var result = ForwardNode.Value;

		ForwardArrange();

		return result;
	}



	public T GetBackward()
	{
		if (BackwardNode == null)
		{
			throw new Exception($"{nameof(Backward)} is Empty");
		}

		var result = BackwardNode.Value;

		BackwardArrange();

		return result;
	}

	private void ForwardArrange()
	{
		if (ForwardNode == BackwardNode)
		{
			ForwardNode = null;
			BackwardNode = null;
		}
		else
		{
			ForwardNode = ForwardNode.Back;

			if (ForwardNode != null)
			{
				ForwardNode.Front = null;
			}
		}
	}

	private void BackwardArrange()
	{
		if (ForwardNode == BackwardNode)
		{
			ForwardNode = null;
			BackwardNode = null;
		}
		else
		{
			BackwardNode = BackwardNode.Front;

			if (BackwardNode != null)
			{
				BackwardNode.Back = null;
			}
		}
	}

	public void FrontEnqueue(T value)
	{
		var newNode = new Node<T>() { Value = value };

		if (ForwardNode == null)
		{
			BackwardNode = newNode;
			ForwardNode = newNode;
		}
		else
		{
			newNode.Back = ForwardNode;
			ForwardNode.Front = newNode;
			ForwardNode = newNode;
		}
	}

	public void BackEnqueue(T value)
	{
		var newNode = new Node<T>() { Value = value };

		if (BackwardNode == null)
		{
			BackwardNode = newNode;
			ForwardNode = newNode;
		}
		else
		{
			newNode.Front = BackwardNode;
			BackwardNode.Back = newNode;
			BackwardNode = newNode;
		}
	}
}

public class Node<T>
{
	public T Value { get; set; }

	public Node<T> Front { get; set; }

	public Node<T> Back { get; set; }
}
```
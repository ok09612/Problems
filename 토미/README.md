# Problems

https://leetcode.com/problems/decode-string/

``` C#
  public class Solution
    {
        public string DecodeString(string s)
        {
            var result = new StringBuilder();

            var i = 0;

            while (i < s.Length)
            {
                var value = (int)s[i];

                i++;

                //숫자인 경우
                if (value < 0x3A)
                {
                    var numSize = 1;

					while (s[i - 1 + numSize] < 0x3A)
					{
                        numSize++;
					}

					var count = int.Parse(s.Substring(i - 1, numSize));
					i += numSize;
					result.Append(GetRepeat(count, s, ref i));
                }
                //문자인 경우
                else if (value > 0x60)
                {
                    result.Append((char)value);

                }
            }

            return result.ToString();
        }

        private string GetRepeat(int c, string s, ref int index)
        {
            var sb = new StringBuilder();

            while (true)
            {
                var value = (int)s[index];

                index++;

                if (value < 0x3A)
                {
                    var numSize = 1;

                    while (s[index - 1 + numSize] < 0x3A)
                    {
                        numSize++;
                    }

                    var count = int.Parse(s.Substring(index - 1, numSize));
					index += numSize;

					sb.Append(GetRepeat(count, s, ref index));
                }
                else if (value > 0x60)
                {
                    sb.Append((char)value);
                }
                else
                {
                    break;
                }
            }

            var text = sb.ToString();

            for (int j = 0; j < c - 1; j++)
            {
                sb.Append(text);
            }

            return sb.ToString();
        }
    }
```
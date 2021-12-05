# Plus One
public int[] PlusOne(int[] digits) {
    bool plus =true;
    int[] calc = new int[digits.Length];
    for (int i = digits.Length - 1; i >= 0; i--)
    {
        int ori = digits[i];
        if (plus)
        {
            digits[i] += 1;

            if(digits[i] == 10)
            {
                digits[i] = 0;
            }
            else
            {
                plus = false;
            }
        }

        calc[i] = digits[i];
    }

    int[] answer = calc;
    if (plus)
    {
        answer = new int[digits.Length + 1];
        answer[0] = 1;
        for(int i = 0; i < calc.Length; i++)
        {
            answer[i + 1] = calc[i];
        }
    }

    return answer;
}

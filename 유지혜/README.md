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


#신고 결과 받기
using System;
using System.Collections.Generic;
using System.Linq;

public class Solution {
     public int[] solution(string[] id_list, string[] report, int k)
        {
            int idcount = id_list.Length;
            int[] answer = new int[idcount];

            List<Users> users = new List<Users>();
            List<string> list = new List<string>();
            List<string> reported = new List<string>();

            list.AddRange(report.Distinct().ToList());

            foreach (string id in id_list)
            {
                Users user = new Users();
                user.Id = id;
                user.ReportUser = new List<string>();

                foreach (string item in list)
                {
                    string[] s = item.Split(' ');
                    string reportid = s[0];
                    string reportedid = s[1];
                    if (user.Id == reportid)
                    {
                        user.ReportUser.Add(reportedid);
                    }

                    if (user.Id == reportedid)
                    {
                        user.ReportedCount = user.ReportedCount + 1;
                    }
                }

                if (user.ReportedCount >= k)
                {
                    reported.Add(user.Id);
                }

                users.Add(user);
            }

            for (int i = 0; i < idcount; i++)
            {
                Users users1 = users[i];

                int count = 0;
                foreach(var item in reported)
                {
                    if (users1.ReportUser.Exists(x=> x == item))
                    {
                        count++;
                    }
                }

                answer[i] = count;
            }

            return answer;
        }
}

public class Users
{
    public string Id { get; set; }
    public List<string> ReportUser { get; set; } = new List<string>();
    public int ReportedCount { get; set; }
}
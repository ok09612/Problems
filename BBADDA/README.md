# Problems (문자열 관련문제 2개)


https://programmers.co.kr/learn/courses/30/lessons/12926
# 시저 암호 (LV1)
```javascript
function solution(s, n) {
    var answer = '';
    let string_array = [...s];
    
    answer = string_array.map((item, idx, cur) => {
        if (item == ' ') {
            return item;
        }else{
            let type = '';
            let item_char_code = item.charCodeAt(0);
            let convert_char_code = item.charCodeAt(0) + n;
            
            if (item_char_code >= 97 && item_char_code <= 122) {
                type = 1;
            }
            
            if (item_char_code >= 65 && item_char_code <= 90) {
                type = 2;
            }
            
            if (type == 1 && convert_char_code > 122) {
                convert_char_code -= 26;
            }
            
            if (type == 2 && convert_char_code > 90) {
                convert_char_code -= 26;
            }
            return String.fromCharCode(convert_char_code);
        }
    });
    
    
    return answer.join('');
}
```


https://programmers.co.kr/learn/courses/30/lessons/12948
# 핸드폰 번호 가리기 (LV1)
```javascript
function solution(phone_number) {
    var answer = '';
    answer += phone_number.slice(0, -4).replace(/[0-9]/g, '*');
    answer += phone_number.slice(-4);
    return answer;
}
```





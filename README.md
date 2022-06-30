# 정규표현식(RedExp)
정규식, Regular Expression

## 역할
- 문자 검색
- 문자 대체
- 문자 추출

## 정규식 생성

```js
// 생성자
new RegExp('표현', '옵션')
new RegExp('[a-z], 'gi')

// 리터럴
/표현/옵션
/[a-z]/gi
```

## 예제 문자
```js
const str = `
010-6723-4401
thesecond@gmail.com
https://www.omdbapi.com/?apikey=7035c60c&s=frozen
The quick brown fox jumps over the lazy dog.
abbcccdddd
`
```

## 메소드

메소드 | 문법 | 설명
--|--|--
test | `정규식.test(문자열)` | 일치 여부(Boolean)
match | `문자열.match(정규식)` | 일차하는 문자의 배열(Array)
replace | `문자열.replace(정규식, 대체문자)` | 일치하는 문자를 대체

## 플래그(옵션)

플래그 | 설명
--|--
g | 문자열 속에서 모든 일치하는 문자(global)
i | 영어 대소문자를 구분 않고 일치(ignore case)
m | 여러 줄 일치(multi line)

## 패턴(표현1)

패턴 | 설명
-- | --
^ab | 줄(Line) 시작에 있는 ab와 일치
ab$ | 줄 끝에 있는 ab와 일치
. | 임의의 한 문자와 일치
a&verbar;b | a 또는 b와 일치
ab? | b가 없거나 b와 일치
{3} | 3개 연속 일치 (숫자 변경 가능)
{3,} | 3개 이상 연속 일치
{3,5} | 3개 이상 5개 이하(3~5개) 연속 일치

## 패턴(표현2)
패턴 | 설명
-- | --
[abc] | a 또는 b 또는 c
[a-z] | a부터 z 사이의 문자 구간에 일치(영어 소문자)
[A-Z] | A부터 Z 사이의 문자 구간에 일치(영어 대문자)
[0-9] | 0부터 9 사이의 문자 구간에 일치(숫자)
[가-힣] | 가부터 힣 사이의 문자 구간에 일치(한글)
-- | --
\w | 63개 문자(word, 대소영문52개 + 숫자10개 + _ )에 일치)
\b | 63개 문자에 일치하지 않는 문자 경계(Boundary)
\d | 숫자(Digit)에 일치
\s | 공백(Space, Tab 등)에 일치
-- | --
(?=) | 앞쪽 일치(Lookahead)
(?<=) | 뒤쪽 일치(Lookbehind)

# 활용 예시

/\bf\w{1,}\b/g : f로 시작하는 모든 문자열 : frozen, fox

h.replace(/\s/g, '') : h 변수에 저장된 문자열의 모든 공백을 대체

match(/.{1,}(?=@)/g) : @앞쪽 일치
match(/(?<=@).{1,}/g) : @뒤쪽 일치

/^\/posts\/([a-zA-Z0-9-_]+)$/ : /posts/ 뒤에 오는 소문자, 대문자 여러개의 문자 캡쳐()
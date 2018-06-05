---
layout: post
title: Linux Shell Command
tags: [Linux,perl,python,주석,프로세스]
excerpt_separator: <!--more-->
---
Linux Shell Command 용법
<!--more-->

### 들어가기에 앞서

Bash 기준으로 설명. 선언부에 ``#!/bin/sh``를 명시.

### 용법

- 반복문

```bash
for i in 1 2 3 4 5
do
echo i
done
```
반복문에서 연속된 값은 다음과 같이 표현 가능하다.
```bash
for i in {1..5}
do
echo $i
done
```

- 문자열 처리

파일명을 변경할 때 유용한 팁들
```bash
i="text123"
echo ${i:2}	# n≥0일 때, 두 번째 파라미터는 n+1번째 위치부터 남길 글자
xt123
echo ${i:(-4)}	# n<0일 때, 두 번째 파라미터는 n번째 위치부터 남길 글자
t123
echo ${i:0:4}	# n=0일 때, 세 번째 파라미터만큼 글자를 자름
text
echo ${i:2:2}	# 세 번째 파라미터는 남길 글자
xt
```
문자열 붙이기
```bash
i="text123"
j="string"
k=$i$j		# does works
k=${i}${j}	# does works
```

```bash
i="text123"
echo ${i%t*3}	# % 다음 시작문자, * 다음 끝문자
tex		# Shortest Match
echo ${i%%t*3}	# % 다음 시작문자, * 다음 끝문자
		# Longest Match
```

```bash
echo ${i/#text/book}	# text를 book으로
text123			# Front-end Match
echo ${i/%123/456}	# 123을 456으로
text123			# Back-end Match
```

숫자 0으로 채우기 (padding)
```bash
for i in {1..100}
do
i=$(printf %01d $i)
echo $i
done
```
위와 같이 작성하면 ``0001, 0002, ..., 0999, 1000``과 같이 나온다.

- [String Manupulation](https://www.tldp.org/LDP/abs/html/string-manipulation.html)

### wget 관련
``wget``을 이용하여 ``https`` 관련 프로토콜을 받을 때 다음과 같이 사용.
```bash
wget --no-check-certificate IN -O OUT
```

다른 방법으로는 ``.wgetrc``에 설정 파일을 만드는 것도 있다.
```bash
echo "check_certificate = off" >> ~/.wgetrc
```

### 라인 조작
- 라인 랜덤출력
```bash
shuf
```
- 임의의 글자넣기
```bash
echo -ne '\n' >> a.txt
```

### perl
#### print the whole thing one at a time (perl 5)

```perl
for $i ( 0 .. $#AoA ) {
    for $j ( 0 .. $#{ $AoA[$i] } ) {
        print "elt $i $j is $AoA[$i][$j]\n";
    }
}
```
#### perl 주석
```perl
=pod
=cut
```
로 범위지정

### python
python 2 or 3 사용시 다음을 명시
```python
from __future__ import print_function
```

### 기타 유용한 팁
- 비프음 끄기
```bash
setterm -blength 0
```

- zombie process kill
```bash
ps -ef | grep defunct | awk '{print $3}' | xargs kill -9
```

- root 권한에서 killall5 사용금지 (시스템 강제종료)

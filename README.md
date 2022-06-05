# 목차
[리눅스시스템 명령어](#리눅스시스템-명령어)
>1) [top](#1_top)
>2) [ps](#2_ps)
>3) [jobs](#3_jobs)
>4) [kill](#4_kill)
>5) [리눅스시스템 명령어 요약](#리눅스시스템-명령어-요약)

[vim 에디터 매크로 사용방법](#vim-에디터-매크로-사용방법)

[참조사이트](#참조사이트)


---
# 리눅스시스템 명령어

## 1_top
**top(table of processes)** 명령어는 현재 OS의 상태를 나타내주는 CLI 어플리케이션입니다. 메모리 사용량, CPU 사용량등을 나타내주며 top을 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여줍니다.
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Frxlg4%2FbtqYfV2LE3L%2FSW5SbyO65ZUa5PggM3KI8K%2Fimg.png)

요약 영역은 전체 프로세스가 OS에 대해서 리소스를 어느정도 차지하고 있는지를 알려줍니다.
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcIwHTf%2FbtqYiCOXiQk%2F0wpKbRc7uKG8mo9vfKLWiK%2Fimg.png)

**주요옵션**
* -d(갱신시간) : 갱신시간설정(초 단위)
* -p : 특정PID값을 갖는 프로세스를 모니터링할때 사용
* -b : 배치모드(batch mode)로 실행하는 옵션 다른 프로그램이나 파일에 전송할 때 사용함 보통 -n옵션과 같이 실행함
* -n : top명령의 실행횟수를 지정하는 옵션

## 2_ps
**ps(process status)** 명령어는 현재 실행중인 프로세스 목록과 상태를 보여줍니다. 주로 파이프라인, grep명령어와 함께 사용하여 특정 프로세스를 확인하는데 많이 사용된다.

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile29.uf.tistory.com%2Fimage%2F992BFB3A5BC6E4EE29CE2E)

가장많이 사용되는 형태는 ps -ef | grep (프로세스명)

모든프로세스의 출력값을 grep을 이용해 (프로세스명)이 포함된 라인들을 출력

예) `ps -ef | grep apache`

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile25.uf.tistory.com%2Fimage%2F99CB14385BC6EE9417CC26)

## 3_jobs
**jobs** 명령어는 작업의 상태를 표시하는 명령어다. 현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력되며, 각 작업에는 번호가 붙어있어 kill명령어 뒤에 %번호 등으로 사용할 수 있다.

`jobs [옵션][작업번호]`

```
testuser@ubuntu1:~$ sleep 300 &
[1] 30335
testuser@ubuntu1:~$ sleep 400 &
[2] 30336
testuser@ubuntu1:~$ sleep 500 &
[3] 30337
testuser@ubuntu1:~$ jobs
[1]   Running                 sleep 300 &
[2]-  Running                 sleep 400 &
[3]+  Running                 sleep 500 &
testuser@ubuntu1:~$ kill %2
testuser@ubuntu1:~$ 
[2]-  Terminated              sleep 400
testuser@ubuntu1:~$ jobs
[1]-  Running                 sleep 300 &
[3]+  Running                 sleep 500 &
testuser@ubuntu1:~$ kill %1 %3
testuser@ubuntu1:~$ 
[1]-  Terminated              sleep 300
[3]+  Terminated              sleep 500
testuser@ubuntu1:~$ jobs
testuser@ubuntu1:~$
```

|상태|설명|
|:---:|:---|
|Running|작업이 계속 진행중임|
|Done|작업이 완료되어 0을 반환|
|Done(code)|작업이 종료되었으며 0이 아닌 코드를 반환|
|Stopped|작업이 일시중단|
|Stopped(SIGTSTP)|SIGTSTP 시그널이 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 시그널이 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 시그널이 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 시그널이 작업을 일시 중단|

**주요옵션**
* -l : 프로세스 그룹 ID를 state필드 앞에 출력
* -n : 프로세스 그룹중에 대표 프로세스 ID를 출력
* -p : 각 프로세스 ID에 대해 한 행씩 출력
* command : 지정한 명령어를 실행

## 4_kill
**kill** 명령어는 대개 프로세스를 죽일 때 사용합니다. 하지만 내부적으로는 프로세스에 시그널을 보내 원하는 작업을 하게 하는 명령어입니다.

`kill[PID]`

예를들어 node.js로 실행중인 서버를 죽이고 싶다면 ps명령어를 통해 node.js의 PID를 얻고 kill명령어의 파라미터로 넘겨 실행시키면 종료시킬 수 있습니다.

![image](https://t1.daumcdn.net/cfile/tistory/993696485C6377E90C)

## 리눅스시스템 명령어 요약

||명령어|설명|
|:---:|:---:|:---|
|1|top|현재 OS의 상태를 나타내주는 명령어|
|2|ps|현재 실행중인 프로세스의 목록을 보는 명령어|
|3|jobs|작업의 상태를 표시하는 명령어|
|4|kill|현재 실행중인 프로세스를 종료하는 명령어|

**ps와 top의 차이점**
* ps는 ps한 시점에 proc에서 검색한 cpu 사용량
* top은 proc에서 일정주기로 합산해 cpu 사용량 출력
---
# vim 에디터 매크로 사용방법

레코딩 매크로는 '사용자가 입력한 것을 기록했다가 그대로 반복해 주기 위한 기능' 이다.

``` c
#include <stdio.h>

int main(int argc, const char *argv[])
{
  int a = 0;
  int b = 1;
  int c = 2;
  int d = 3;
  
  return 0;
}
```
***이 소스코드에서 int로 선언된 변수 4개 a, b, c, d의 이름을 _a,_b,_c,_d로 바꾸려고한다.***

1) :5ENTER - 5번라인으로 이동
2) qa - q키로 매크로 녹화시작. a는 매크로의 이름
3) /intENTER -'int'로 검색한다. 이 경우 'int a'항목이 제일 먼저 검색될 것이다.
4) w - 다음 단어로 이동. 즉 커서가 'a'로 이동한다.
5) i_ -i를 눌러서 입력모드로 들어가서 언더라인(_)을 입력한다는 의미
6) ESC - 편집모드 종료
7) q - 레코딩 종료

``` c
int main(int argc, const char *argv[])
{
  int _a = 0;
  int b = 1;
  int c = 2;
  int d = 3;
  
  return 0;
}
```
레코딩이 완료되었다. 지금까지 한 행동은 5번 라인에서 원하는 형식으로 편집하는 행위를 그대로 녹화한 것이다. 따라서 5번라인은 편집이 끝난 상태가 된다.
그럼 이제 다음 키를 입력해보자.

`@a`@의 의미는 녹화된 매크로를 실행한다는 의미다. 이 다음으로오는 'a'는 a라는 매크로를 실행한다는 의미다.

이 키를 누르면 그 다음 라인의 편집이 된다. 즉, int _b = 1;으로 바뀌는 것을 볼 수 있다.

``` c
int main(int argc, const char *argv[])
{
  int _a = 0;
  int _b = 1;
  int c = 2;
  int d = 3;
  
  return 0;
}
```

계속해서 @a를 2번 더 누르면 원하는 결과물이 나온다.

``` c
int main(int argc, const char *argv[])
{
  int _a = 0;
  int _b = 1;
  int _c = 2;
  int _d = 3;
  
  return 0;
}
```

---
# 참조사이트
* [리눅스top명령어로서버의상태파악하기](https://sabarada.tistory.com/146)

* [리눅스명령어top](https://starrykss.tistory.com/1691?category=592475)

* [리눅스ps명령어(프로세스확인명령어,특정프로세스확인)](https://arer.tistory.com/150)

* [리눅스jobs명령어 사용법](https://hbase.tistory.com/265)

* [리눅스jobs](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_jobs)

* [리눅스kill명령어 사용법(프로세스 죽이기)](https://sisiblog.tistory.com/209)

* [Vim자동편집을위한길,Recording](http://seorenn.blogspot.com/2011/04/vim-recording.html)

## 리눅스시스템 명령어

||명령어|설명|
|:---:|:---:|:---|
|1|[top](1.top)|현재 OS의 상태를 나타내주는 명령어|
|2|[ps](2.ps)|현재 실행중인 프로세스의 목록을 보는 명령어|
|3|[jobs](3.jobs)|작업의 상태를 표시하는 명령어|
|4|[kill](4.kill)|현재 실행중인 프로세스를 종료하는 명령어|

**ps와 top의 차이점**
* ps는 ps한 시점에 proc에서 검색한 cpu 사용량
* top은 proc에서 일정주기로 합산해 cpu 사용량 출력


### 1. top
**top(table of processes)** 명령어는 현재 OS의 상태를 나타내주는 CLI 어플리케이션입니다. 메모리 사용량, CPU 사용량등을 나타내주며 top을 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여줍니다.
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Frxlg4%2FbtqYfV2LE3L%2FSW5SbyO65ZUa5PggM3KI8K%2Fimg.png)

요약 영역은 전체 프로세스가 OS에 대해서 리소스를 어느정도 차지하고 있는지를 알려줍니다.
![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcIwHTf%2FbtqYiCOXiQk%2F0wpKbRc7uKG8mo9vfKLWiK%2Fimg.png)

### 2. ps
**ps(process status)** 명령어는 현재 실행중인 프로세스 목록과 상태를 보여줍니다. 주로 파이프라인, grep명령어와 함께 사용하여 특정 프로세스를 확인하는데 많이 사용된다.

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile29.uf.tistory.com%2Fimage%2F992BFB3A5BC6E4EE29CE2E)

가장많이 사용되는 형태는 ps -ef | grep (프로세스명)

모든프로세스의 출력값을 grep을 이용해 (프로세스명)이 포함된 라인들을 출력

예) ps -ef | grep apache

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile25.uf.tistory.com%2Fimage%2F99CB14385BC6EE9417CC26)

### 3. jobs

### 4. kill

## vim 에디터 매크로 활용방법

## 참조사이트
[리눅스top명령어로서버의상태파악하기](https://sabarada.tistory.com/146)

[리눅스ps명령어(프로세스확인명령어,특정프로세스확인)](https://arer.tistory.com/150)

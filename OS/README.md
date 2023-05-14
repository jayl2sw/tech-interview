# Operating System

**운영체제**는 사용자의 하드웨어, 시스템 리소스를 제어하고 프로그램에 대한 일반적 서비스를 지원하는 시스템 소프트웨어입니다. 응용 프로그램과 하드웨어 사이의 인터페이스로 응용 프로그램들이 메모리와 CPU, 입출력 장치 등의 자원들을 사용할 수 있도록 만들어 주며 시스템 하드웨어를 관리합니다. 뿐만 아니라 응용 소프트웨어를 실행하기 위하여 하드웨어 추상화 플랫폼과 공통 시스템 서비스를 제공합니다.



<br>

#### 1. 프로세스 & 스레드 

* 프로세스와 스레드의 차이점에 대해서 설명해주세요.
* 멀티 프로세스와 멀티 스레드의 차이점에 대해 설명해주세요.
* PCB에 대해서 설명해주세요.
* 컨텍스트 스위칭이 무엇이고 어떤 일들이 일어나는지 설명해주세요.
* 프로세스의 컨텍스트 스위칭과 스레드의 컨텍스트 스위칭 간의 차이점은 무엇인가요?

[답변](https://github.com/jayl2sw/tech-interview/blob/master/OS/answer/README.md)



<br>

#### 2. 프로세스 주소 공간

* 프로세스의 주소 공간에 대해서 설명해주세요
* Heap 영역과 Stack 영역에 각각 어떤 데이터가 저장되나요?
* Stack과 Heap영역 중, 접근 속도가 더 빠른 영역은 어디일까요?
* 다음과 같이 공간을 분할하는 이유가 있을까요?
* 스레드의 주소공간은 어떻게 구성되어 있을까요?

[답변](https://github.com/jayl2sw/tech-interview/blob/master/OS/answer/README.md)



<br>

#### 3. 스케쥴러

* 단기, 중기, 장기 스케줄러에 대해 설명해주세요.
* 현대 OS에서 사용되는 스케줄러 방식에 대해 설명해주세요.
* 프로세스의 상태에 대해 설명해주세요.
* OOM(Out of Memory)가 발생한 경우 Process는 어떠한 상태로 변화하나요?

[답변](https://github.com/jayl2sw/tech-interview/blob/master/OS/answer/README.md)



<br>

#### 4. 스케줄링 알고리즘

* 알고 있는 프로세스 스케줄링 알고리즘들을 말해주세요.
* RR(Round Robin) 알고리즘에서 Time Slice에 따른 trade-off를 설명해주세요.
* 동시성과 병렬성의 차이에 대해 설명해주세요.
* Multi-level Feedback Queue에 대해 설명해주세요. 
  * 타 스케줄러와 비교 했을 때, 어떤 문제점을 해결할 수 있나요?


[답변](https://github.com/jayl2sw/tech-interview/blob/master/OS/answer/README.md)



<br>

#### 5. Mutex & Semaphore

* 뮤텍스와 세마포어에 대해서 설명해주세요. (공통점, 차이점)
* 뮤텍스와 이진 세마포어의 차이점에 대해 설명해주세요.
* Monitor에 대해 설명해주세요.

[답변](https://github.com/jayl2sw/tech-interview/blob/master/OS/answer/README.md)



<br>

#### 6. DeadLock

* Deadlock이 발생하는 4가지 조건에 대해 설명해주세요.
  * deadlock을 어떤 방식으로 예방할 수 있을까요?
  * 현대 OS의 경우 왜 deadlock을 예방하지 않나요?

[답변](https://github.com/jayl2sw/tech-interview/blob/master/OS/answer/README.md)



<br>

#### 7.  가상 메모리

* 가상 메모리란 무엇인가요?
* 내부 단편화와 외부 단편화에 대해 설명해주세요.
* Page Fault가 발생했을 때, 어떻게 처리하는지 설명해 주세요.
* Thrashing이란 무엇인가요?
  * Thrashing이 일어났을 때, 어떻게 해결할 수 있나요?
* Segmentation과 Paging의 차이점은 무엇인가요?
  * 둘 둥, 현대 OS에서 사용하는 방식은 무엇인가요?
* 페이지 크기에 대한 Trade-Off를 설명해 주세요.
  * 페이지 크기와 Page Fault의 빈도, 오버헤드와의 관계를 설명해주세요.
* 페이지 교체 알고리즘에 대해 설명해주세요 
  * LRU 알고리즘은 어떻게 구현할 수 있을까요?
  * clock 알고리즘에 대해 설명해주세요
* 가상 메모리 주소를 가지고 실제 주소를 어떻게 가져올 수 있는지 설명해 주세요.
* 32비트에서, 페이지의 크기가 1kb 이라면 페이지 테이블의 최대 크기는 몇 개일까요?



##### 7-1. TLB(Translation Lookaside Buffer)

* TLB란 무엇인가요?
* TLB를 쓰면 왜 빨라지나요?
* Context Switching와 TLB는 어떤 관계가 있나요?
* MMU는 무엇인가요?
* TLB와 MMU는 현대에 어디에 위치해 있나요?

[답변](https://github.com/jayl2sw/tech-interview/blob/master/OS/answer/README.md)



<br>

#### 8. 캐시 메모리



[답변](https://github.com/jayl2sw/tech-interview/blob/master/OS/answer/README.md)

#### 9. File System




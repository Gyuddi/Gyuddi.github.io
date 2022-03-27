---
title:  "Computer System"
excerpt: "컴퓨터 시스템과 OS에 대해 araboja"

categories:
  - Computer System
tags:
  - [Computer System, Operating System]

toc: true
toc_sticky: true
 
date: 2022-03-08
last_modified_at: 2022-03-08
---
   
**Computer System이란?**    

컴퓨터 시스템의 기본 구성 - 하드웨어, 시스템 소프트웨어(OS), 응용소프츠웨어.
소프트웨어는 코드와 명령어의 시퀀스이다.
즉, 하드웨어가 수행하는 instruction의 시퀀스.
* 소프트웨어는 하드웨어를 변경하지 않고 새로운 기능을 추가 가능하다.(유연성)

하드웨어
1. CPU - 지시를 해석하고 control signal을 만들어 내는 하드웨어.
2. Memory - 데이터와 프로그램을 저장하는 공간.
3. I(input)/O(output) Components - 컴퓨터 외부와 인터페이스 input은 키보드 output은 디스플레이.

* hardware 만 사용하는 방식은 동작 시간이 매우 빠름. 하지만 명령을 수정하기 위해선 물질적 변화가 필요함.   
* hardware 와 software은 함께 사용할 경우 명령을 수정하기 위해선 물질적 변화가 필요하지 않음. 하지만 General-purpose를 위한 다양한 기능을 제공하기에, 비싸다.   

**History of Computers**
- 펜실베니아 대학교에서 1943~1946년에 만든 ENIAC이 최초의 컴퓨터. 진공관에 1bit를 담아 17000개의 진공관을 이용하였다. 2KB의 용량이였다!
2차 대전 당시 포탄의 계산을 위해 만들어졌다. 하지만 종전 후 완성됨.
이후 수소폭탄의 연산을 위해 사용됨....
- 이후 **John von Neumann**이 프린스턴 대학교에서 EDVAC을 기반으로 ISA Computer를 만듦 소프트웨어의 첫 등장 by **instruction 과 Date를 하나의 메모리에 집어넣는다.**-> __본 노이만 방식__(stored program computer)
- UNIVAC은 ENIAC의 발전된 버전으로 최초의 상업적 컴퓨터이다.
- 60년대에 들어서며 IBM이 컴퓨터 제작에 참여하며 IBM 360이 제작된다. **종이(펀치카드)**에 구멍을 뚫어 코딩을 하는 방식이다! - **Data는 진공관에 Insetructiondms 펀치카드에 즉, 서로 다른 메모리에 존재한다.** -> __하버드 방식__
- 70년대 초반 DEC사에서 PDP-11을 제작한다. 펀치카드가 터미널로 변화하게 된다(C와 Unix 사용).with 키보드와 모니터.
- 80년대 애플의 매킨토시와 IBM의 5101이 탄생한다. -> 소형 컴퓨터의 등장으로 컴퓨터의 개인 보급이 시작된다.

**컴퓨터의 기능**
1. Data processing
2. Data storage/movement
3. Flow control   
by Control Mechanism

* computer의 구성 - 메모리,CPU,I/O, System bus(3개를 연결해줌)
* CPU의 구성 - ALU(산술,논리 연산),레지스터(CPU 내부의 메모리,매우 빠르지만 비쌈),Control Unit(지시를 읽고 해석하여 Control signal를 전송)
* 프로세서 - 유한개의 상태를 가질 수 있는 로직으로 구성된다. FSM기법을 사용

**소프트웨어**
- Firmware -> 하드웨어 안에 들어가는 소프트웨어,컴퓨터 부팅 시 실행된다. 임베디드 프로그래머가 요기를 건든다.
1. bios setup - 기본적 입출력을 setup한다.
2. bootstrap - 운영체제를 기동시킨다.
3. addressing modes 등등...
- OS
- Develoment Software
- Software Development

**기억장치**
1. 주 기억장치 - 컴퓨터 내부에 존재한다. Cpu바로 옆에 있어 속도가 매우 빠르다. 하지만 비싸다.
* CPU내부의 캐시 메모리
2. 보조 기억장치 - 외부에 존재한다. 속도는 느리지만 저렴하다.

**CPU와 IO의 연결** ->주변 기기 제어기를 통해 System bus로 연결된다.
ex)그래픽 카드
system bus - address bus, data bus, control bus로 나뉜다.
**무어의 법칙** - 반도체 집적회로의 성능이 18개월마다 2배로 증가한다는 법칙   
2000년도에 들어오며 깨진다.by 삼성전자가 12개월마다 2배로 올려버림
* intel은 최초의 microprocessor 4004를 만들고 8080으로 대박을 친다. 8086이 ibm컴퓨터에 사용되게 된다.

* PC -  PC, AC, MAR, IR
* PC란? - 다음 인출할 명령어의 위치에 대한 정보가 저장
* AC란? - 데이터를 일시 저장하는 레지스터
* MAR이란? 메모리에 접근을 할때 정보를 읽어오고자 하는 위치, 주소를 저장하는 곳.
* MBR이란? 메모리에서 사용하는 데이터가 저장되는 공간. 또는 메모리로 전송되는 데이터가 저장되는 공간.
* I/OAR이란? IO기기의 주소자 저장되어있는 공간을 저장하는 곳.
* I/OBR이란? IO에서 사용하는 데이터가 저장되는 공간.
* IR이란? 명령어의 저장공간 ->**명령어** FETCH = cpu가 가르키고 있는 위치의 명령어를 AC에 넣는 것.

* 본 노이만 방식 - 메모리 안에 Instruction과 Data가 같이 있는 방식 ->하나의 메모리만 사용하기에 속도가 느리다(병목현상).   
* 하버드 방식 - 두 메모리 안에 Instruction과 Data가 분리되어 있는 방식 ->비싸고 복잡하다.   
해결책 - cpu 내부의 BUS 분리 후 캐시 메모리를 DATA 캐시와 instruction캐시를 넣어둔다. 즉 cpu 안에서는 하버드 방식. 외부에서는 본 노이만 방식
=(modified harvard 방식)

__CPU 내부의 구체적 작동 방식__
high level language가 컴파일을 통해 어샘블리 코드, 기계어로 변환된다.
* 기계어 - Opcode 4bit(명령어ex)add,move)와 Operand 12bit(데이터를 가져오는 위치)로 구성됨, Cpu 마다 그 구조가 다르다!
ex)1940인 경우 opcode는 1 address는 940이다.
* 기계어 구동 방식 - ex) Opcode 0001 = 메모리로부터 AC(cpu 안의 레지스터(고속의 메모리))를 가져와 CPU에 저장하라.
0010 = Store AC to memory    
0101 = Add to AC form memeory   
* 구체적 작동방식
meoery - 300/1940   
cpu register - pc = 300 , ir = 1940   
-> opcpde는 1 operand는 940. 메모리의 940번지로 가 그 데이터를 AC에 저장한다. pc주소는 1이 증가한다.   
cpu register - pc = 301, ir = 5941   
-> opcode는 5 operand는 941. 메모리는 941번지로 가 AC와 메모리 값의 합을 AC에 저장한다. pc주소는 1 증가한다.   
cpu register - pc = 302, ir = 2941
-> opcode는 2 operand는 941. 메모리는 941번지로 가 AC값을 메모리 941번지에 저장한다. pc는 1 증가한다.   

* IO작동방식
- write를 하고 싶다면 
1. IO로 전송하여 프린트가 완료 될 때 까지 기다렸다가 다음 작업을 실행한다.
2. IO로 전송하여 명령을 전송하고 프린트는 작동하며 cpu는 다른 작업을 또 실행한다. 프린팅이 끝나면 cpu가 돌아와서 종료한다.interrupt(cpu외부의 event 발생 여부를 알려주는 것)를 통해 프린팅이 끝난 것을 알 수 있다. - short I/O 방식   

nested interrupt -> interrupt 도중에 또다른 interrupt가 발생하는것.
maskable interrupt -> interrupt를 무시하는것
non - maskable interrupt -> 무조건적으로 interrupt를 수행하는것. ex) 컴퓨터의 전원이 꺼지는것. -> 남은 전류로 처리중인 데이터를 저장공간에 저장한다.   

* 명령어에 따른 CPU의 종류
1. CISC - 복잡한 명령어를 사용하는 구조
명령어의 수와 형식이 많고 복잡하며 길이가 가변적이고 Micro-Program 제어방식을 사용하여 느리다. 복잡한 일을 처리하기 좋다.
2. RISC - CISC 명령어의 종류를 줄여서 사용하는 명령어를 사용하는 구조
명령어의 수와 형식이 적고 단순하며 길이가 고정적이고 Hard-Wired 제어방식을 사용하여 빠르다.복잡한 일을 처리하기 힘들다.   
--> 사용되는 프로그램에 따라 두 방식의 속도는 달라진다. 따라서 많이 쓰는 명령어만 골라 RISC에 추가하여 효율성을 높혔다!   
명령어 FETCH 이후 명령어 executiond이 발생한다.   

* FETCH -> 1.PC의 위치 값을 MAR 에 넣는다.   
2.기억장치 속 MAR위치의 값을 MBR에 넣는다. PC += 1;
3.MBR의 값을 IR에 옮긴다.   
이후   
1.명령어를  decoding한다.   
2.명령어를 execution한다.   
3.결과를 다시 AC에 저장한다(write back)   

* modified harvard 방식에 나온 BUS란?
같은 기능을 하는 Line을 의미한다.   
Bus에는 Data Bus, Address Bus, Control Bus이 존재한다. 이를 다 합하여 System Bus라고 한다.

CPU프로세서는 캐시와 속도가 따른 Local bus로 이어져있고 캐시는 main memory와 적당한 속도의 System bus로 연결되어있고 IO는 속도가 느린 bus를 사용한다.
위와 같이 **위계적인 bus**가 사용된다.   
modified harvard 방식의 경우 I-캐시, D-캐시가 연결되어있다!

**CPU 구조**
기본 구조   
* ALU 
* 레지스터 세트 
* 제어 유닛 
* 버스 - 주소 버스, 데이터 버스, 제어 버스

* 산술명령어의 경우   
instr 캐시 -> 레지스터 -> ALU ->Data 캐시   + opcode는 제어 유닛으로 전송되어 control 신호를 보낸다.   
이 과정이 **data path**를 통해 진행된다.   
CPU 설계의 과정 => ISA(명령어의 형태를 결정), data path(데이터 흐름 결정), control 로직(각 파트의 작동을 컨트롤함)   
명령어에는 opcode와 oprand(변수의 주소)으로 구성되어있다.   
+ opcode의 형태에 따라서 oprand의 구조가 달라질 수 있다 -> addressing mode

**ALU**구동 방식
- ALU에는 뺏셈이 없다. 음수를 더할 뿐. ADDSUB의 신호(by control signal)를 통해 더해주는 값의 부호를 결정한다.
- 나머지 연산은 Logic unit에서 진행된다.   

* 명령어의 종류 -> ISA에 의해 결정됨
1. 데이터 전송 - 기억장치 간 데이터를 이동하는 동작 
2. 산술,논리연산 
3. 입출력
4. 프로그램 제어 - 명령어의 실행 순서를 변경하는 연산

* Addressing mode -> 데이터가 들어있는 위치를 어떤 식으로 지시할 것인가.
- 직접 주소지정 방식 - 명령어에 메모리 속 데이터 위치가 들어있음
- 간접 주소지정 방식 - 명령어에 데이터 위치가 저장되어 있는 저장소의 위치를 명시해 줌으로 간접적으로 데이터 위치를 가져옴
- 즉치 주소지정 방식 - 데이터다 명령어에 명시되어 있음.
- 레지스터 간접 주소지정 방식 - 레지스터의 위치와 기억장치의 직접적인 주소가 명시되어 있음. 레지스터에 저장되어있는 값과 직접적 주소를 더하여 실제 위치를 나타냄. 
- 묵시적 주소지정 방식 - 명령어에 위치가 명시되어있지 않음. 미리 지정된 주소가 사용됨.

+ 명령어에 따라 수행 시간이 다르다.
   
* control logic의 설계
Hard-wired 방식 - 속도는 빠르지만 고정적이다.   
S/W방식 - 속도는 느리지만 유연하다.

__MU0__
- PC,ALU,ACC,IR이 존재
**과정**
1. fetch = PC의 내용이 address bus로 이동하여 memory로 가 memory의 데이터가 data bus 를 통해 IR로 감.
2. decoding = opcode를 분석하여 control signal을 만들어낸다. ALU를 통해 PC += 1이 된다.
3. execution = 데이터를 Addressing mode에 따라 address bus를 통해 memory로 가 데이터를 획득하고 명령어가 수행된다.
4. wirte back = ACC 또는 memory에 결과값이 저장된다.
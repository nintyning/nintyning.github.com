---
layout: post
title: "gcc&g++ 의 컴파일 옵션들"
description: "프로그래밍"
category: programming
tags: [gcc,g++,programming]
---
{% include JB/setup %}

 -o
목적 파일을 지정한다. -o 다음에 오는 문자열은 목적 파일의 경로와 이름을 지정한다.
 -E
전처리 과정만을 진행한다. 복잡한 선택적 컴파일을 수행할 때 유용하다. 또한 매크로 함수의 문법적 오류를 찾아내는 데에도 유용하게 사용될 수 있다.
 -Idir
include 할 헤더 파일등의 위치를 지정한다.
 -nostdinc
default 디렉토리"(standard include 디렉토리)"를 검색하지 않도록 한다.
 -Dmacro 혹은
 -Dmacro=defn
-D다음에 오는 macro를 정의한다. -D_CPU_BIT_=32 는 #define _CPU_BIT_ 32 와 동일하다.
 -Umacro
위의 -D로 지정한 매크로를 해제할때 사용한다.
 -M
Make 파일을 만드는 rule을 표시하도록 한다.
 -MM
기본 inlcude 를 제외한 항목에 대해서만 표시 나머지는 -M 과 같다.
 gcc -M helloworld.c
위의 명령행은 helloworld.c 를 컴파일할 때 사용하는 include 대상들을 Make 형식에 맞도록 화면에 표시하여 준다.
 -S
gcc 컴파일 과정중 C 컴파일 과정까지만 진행하고 나머지 단계를 처리하지 않도록 한다. 어셈블리 코드를 확인하고자 하는 경우등에 사용할 수 있다.
 -W
컴파일 과정중 발생하는 경고에 대한 옵션이다. -W 직후에 관련된 문자열을 선언하여 사용하며 -Wall 은 모든 종류의 경고에 대해 화면에 표시하도록 한다.
 -O
 -O2
 -O3
컴파일러 최적화 관련 옵션 , 위의 명령을 O 뒤의 숫자 에 해당하는 단계로 최적화를 진행한다.
 -g 
gdb를 사용하기 위한 디버깅 정보 파일을 생성하도록 한다.
 -p
 -pg
profiling 을 할수 있도록 프로그램의 수행 결과 (시간 등)을 파일로 저장하는 코드를 삽입한다.
 -c
Assemble 과정 까지만 진행하고 linking 과정을 수행하지 않도록 한다. 사실 가장 많이 쓰는 옵션이다.
 -static
Dynamic linking 을 하지 않고 Static linking을 수행 하도록 한다.
 -nostdlib
standard library를 사용하지 않고 linking을 진행한다. 또한 startup file 또한 포함하지 않는다.
 -llib_name
lib_name에 해당하는 라이브러리를 linking한다. library파일은 보통 lib로 시작하므로 lib를 뺀 이름을 사용하면 된다.
 -Ldir
dir에 해당하는 경로를 라이브러리 탐색 경로에 포함한다.

 -pthread
pthread 즉 POSIX 표준 thread 라이브러리를 사용하는 경우 사용하는 옵션이다. 이것을 주지 않고 컴파일시 core dump 등의 에러가 발생한다.
 -ansi
ANSI 표준에 부합하는 C 코드(C89)를 컴파일할 때 주는 옵션이다. 이식성이 좋지만 확장 문법을 사용하지 못한다.
 -std=(C 표준)
(C 표준)에 해당하는 표준 문법을 지정한다.
 c89 , c99 , gnu89 , gnu99 , c++98 , c++11 , c++1y

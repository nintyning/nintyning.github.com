---
layout: post
title: "블루투스 프로파일 정리"
description: "bluetooth profiles"
category: bluetooth
tags: [bluetooth]
---
{% include JB/setup %}

회사에서 뭐좀 만들려 정보 검색을 하는데 블루투스도 버전에 따라 기능이 다른게 아니더라

bluetooth 기술의 버전 정보에는 대역폭 , 신호세기 , 소비전력등의 정보만이 있고 정확히 어떤 application을 위해 모듈이 설계되어 있는지는 알기 어렵다.
하지만 profile 정보가 명시되어 있는경우 추가적으로 이 모듈이 어떤 기능을 위해 추가적인 기능을 제공하는지 알 수 있다.  


대표적인 profile 종류

SPP - Serial Port Profile
블루투스를 시리얼포트로 사용이 가능하게 기능을 제공하는 프로파일이다.

HID - Human Interface Device Profile
키보드 등의 주변기기로 사용되기 위해 기능을 제공하는 프로파일

A2DP - Advanced Audio Distribution Profile
오디오 기능을 제공하기위한 프로파일

AVRCP - Audio / Video Remote Control Profile
오디오 기능을 제공하기 위한 프로파일 특히 이 프로파일은 A2DP와 같이 사용되어 기기를 컨트롤할 수 있게한다.

PAN - Personal Area Natworking Profile
블루투스를 이용한 개인 네트워크 서비스 제공 프로파일
 
GOEP - Generic Object Exchange Profile
가장 기본적인 파일 전송을 위한 프로파일 바로 사용되는 경우는 흔치 않고 다른 프로파일의 하위로 사용되는 경우가 많다.

HSP - Headset Profile
해드셋 기능을 제공하기 위한 프로파일 통화를 위한 규격으로 64kbps 정도의 음질을 지원한다. 따라서 음질이 보장되지 않는다. 

HFP - Hands free Profile
핸즈프리를 위한 프로파일 
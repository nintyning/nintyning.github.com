---
layout: post
title: "websocket (웹 소켓)"
description: "프로그래밍"
category: programming
tags: [programming , networking , websocket]
---
{% include JB/setup %}

RFC : https://tools.ietf.org/html/rfc6455

websocket 은 기존의 HTTP 의 한계를 보완하기 위해 논의된 표준이다.

HTTP는 기본적으로 요청과 응답의 절차로 서버와 클라이언트의 통신을 행한다. 하지만 이는 많은 overhead를 야기하며 요즘같은 수 많은 스마트 디바이스들이 동적웹 서비스를 이용하는데 큰 약점을 가지게 된다.
전통적인 HTTP 1.0의 경우 connection-less 방식이므로 브라우져의 매회 요청마다 연결을 시도해야 하는 약점이 있다. 물론 이점은 HTTP 1.1 의 keep-alive 해더의 추가로 인해 문제가 해결되는 것처럼 보이지만 서비스 구현이 Dynamic web service 형태라면 이야기가 달라진다. Http의 통신방식으로는 서버는 요청없이 페이지의 변경을 브라우저에 알리는 방법이 극히 제한적이다. 물론 이를 위해 Ajax등의 다양한 해결점이 있지만  HTTP의 근본적인 문제를 혜결하기에는 문제점이 있어보인다. 이러한 문제를 해결하기 위해 발의된 RFC 가 WebSocket으로 보인다.

WebSocket은 HTTP를 이용해 handshake를 하고 같은 이후 프로토콜을 Upgrade하여 마치 Socket처럼 사용하는 것으로 보인다. 아직 완벽히 규격화된 표준이 아니라 다양한 구형 방법이 존재한다.

RFC에 의하면 Http 요청 해더의 Base64를 활용한 key 값을 보내고 서버는 이 응답으로 해당키를 sha1 해시화 메소드의 결과값을 전송함으로 WebSocket 통신이 준비됨을 알린다. 이후  각 구현체의 방법에 때라 Socket통신을 하듯 동신을 하게 된다.

아직 RFC를 전부 읽지 못하여 의문점이 남아 있으며 이후 다시 읽을시 생각할수 있도록 의문점을 여기에 기록한다.

의문점

1. WebSocket은 Http보다 상위 레이어의 계념인가? - 그렇다면 WebSocket은 Http 레이어 위에서 작동하는 multiplexer의 역활을 수행하는가?
2. WebSocket이 Http보다 상위 레이어의 계념이 아니라면 Http hand-shake 과정을 거치고 다른 포트로 연결을 하는가?

위와 같은 의문점이 남는다. 솔직히 위의 의문점이 합당한 의문점인지도 의심이 간다.
RFC는 단지 기술 표준을 위한 문서이므로 기능만 작동 된다면 그 구현 방법이 어떠한 것이든 상관이 없으므로 사실 위와 같은 의문점은 합당하지 않을 것이다.  Http handshake 다음 Socket을 하나 더 열어 통신을 하던 Http의 통신규약 위에 Payload를 추가해 기술을 구현하던 구현체를 작성하는 사람의 마음대로 하면된다. 단지 구현체가 규약대로 통신하면 될뿐이다.

단지 서버와 클라이언트간의 통신 방법에 관한 문제인 만큼 서버가 행동하는 방법을 클라이언트가 따라줘야 한다는 것이다. 이것이 브라우져이든 혹은 네이티브 프로그램이건 말이다.

추후 더 공부를 하고 의문점에 대한 포스트를 남기기로 한다.



---
layout: post
title: "wpa_supplicant을 사용해 무선인터넷 사용하기"
description: "무선인터넷"
category: Dev_study
tags: [pi , beagleboneblack , BBB , wpa_supplicant]
---
{% include JB/setup %}


비글 본 블랙 혹은 라즈베리 파이 등의 리눅스 머신의 wifi 카드를 사용해 무선인터넷을 연결하는 방법에 대해 정리한다.

wpa_supplicant 를 사용하기 이전 무선 인터넷을 사용하기 위한 장치가 준비 되었는지 확인한다.

iwconfig 을 사용해 장치를 확인 보통 wlan* 의 형태로 보이게 된다.
 
    $ iwconfig

ifconfig 를 사용해 해당 인터페이스를 사용가능하게 한다. 

    $ ifconfig wlan* up

iwlist 으로 장비 주변의 AP를 검색한다.

AP가 확인 되면 iwconfig 로 해당 인터페이스에 사용할 AP의 essid 를 알린다.

    $ iwconfig wlan* essid "AP_NAME"

wpa_passphrase 를 사용해 암호화된 key 값과 기본적인 conf 파일의 틀을 만든다. 이 때 wpa_supplicant_"AP_NAME".conf 로 파일명을 짓는 것이 관례이다.

    $ wpa_passphrase "AP_NAME" > /etc/wpa_supplicant/wpa_supplicant_"AP_NAME".conf

위의 명령행을 리턴 시키면 key값을 입력 받기위해 대기한다. 바로 AP의 비밀번호를 입력한다.

생성된 conf 파일을 접속 정보에 맞게 수정한다.

WPA2PSK 암호화 및 인증이 선택된 AP에 해당되는 conf 파일

    network={
        ssid="AP_NAME"
        key_mgmt=WPA-PSK
        pairwise=CCMP TKIP
        group=CCMP TKIP
        #psk = "암호화 되기 이전 key"
        psk = "암호화된 key"
    }

OPEN 된 AP 에 접속하기 위한 conf 파일 예시

    network={
        ssid="AP_NAME"
        key_mgmt=NONE
        auth_alg=OPEN
    }

수정을 완료 하였다면 wpa_supplicant를 사용해 AP에 접속을 시도한다.

    $ wpa_supplicant -iwlan* -c /etc/wpa_supplicant/wps_supplicant_"AP_NAME".conf &

ip를 할당 받기 위해 dhcp 서비스를 사용한다.

dhcpcd의 경우

    $ dhcpcd wlan* &

dhclient 의 경우

    $ dhclient wlan* &

이후 ping 을 사용해 연결을 확인한다. 보통 www.kt.com 을 사용한다.

    $ ping www.kt.com


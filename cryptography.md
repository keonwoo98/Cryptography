# **생활코딩 암호학**

> 본 글은 [생활코딩의 암호학1 강의](https://www.youtube.com/playlist?list=PLuHgQVnccGMD-9lk4xmb6EG1XK1OmwC3u)를 듣고 정리한 내용입니다.

&nbsp;

## **1. 암호학 개요**

**암호학(cryptography)이란?**
* `crypto`(기밀) + `graphy`(방법)

**암호학의 요소**
* 기밀성 (Confidentiality)
* 무결성 (Integrity)
* 인증 (Authentication)

![](https://images.velog.io/images/dogfootbirdfoot/post/18e21c95-9974-458c-b823-8407147fdbcf/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B71.png)

**암호법의 분류**
* 단방향 암호화 방식 : 암호화는 되지만 복호화는 안되는 방식 (무결성)
	
	* 예) md5, sha
* 양방향 암호화 방식 : 암호화와 복호화를 모두 할 수 있는 방식 (기밀성)
	
	* 대칭키 방식 : 암호화, 복호화 모두 같은 key를 사용
		
		* 예) AES, Twofish
	
	* 비대칭키 방식 : 암호화, 복호화 각각의 key를 사용
		
		* 예) RSA

&nbsp;

## **2. 단방향 암호화 방법**

단방향 암호화는 다른 말로 `hash`라고도 불린다.

`hash`의 사전적 의미 ➔ 다지다

즉, 한번 다지면 되돌릴 수 없다.

예시 :

![](https://images.velog.io/images/dogfootbirdfoot/post/a5e9f2c3-45af-488e-9dd2-23e7611f434d/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B72.png)

`hash`를 사용하는 이유 ➔ **무결성**

**무결성(Integrity)**
* 어떠한 정보가 원본으로부터 회손되었거나 또는 조작되지 않았는지를 파악

[MD5 File Checksum 사이트](https://emn178.github.io/online-tools/md5_checksum.html)

**hash algorithm**
* CRC
* MD5
* RIPEMD160
* SHA-1
* SHA-256
* SHA-512

**hash를 어떻게 사용하는가**
* 무결성 체크 (verifying `integrity` of messages and files)
* 전자서명할 때 사용 (`signature` generation and verification)
* 파일의 식별자 (file or data `identifier`)
* 사용자의 비밀번호를 서버에 안전하게 저장할 때 (`password` verification)
* 가상화폐를 채굴할 때 작업증명(POW)이라는 메커니즘에 사용 (`proof-of-work`)

&nbsp;

## **3. 양방향 암호화 방법 - 대칭키**

평문을 암호문으로 바꿀 때 사용했던 key를 복호화할 때도 그대로 사용

![](https://images.velog.io/images/dogfootbirdfoot/post/8a9b5789-f290-4a1c-acad-a42bed5bbd9b/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B73.png)

![](https://images.velog.io/images/dogfootbirdfoot/post/eb1af07b-e801-4922-816f-830236fc6458/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B74.png)

**대칭키 방식의 암호화를 구현하는 알고리즘**
* Twofish
* Serpent
* (Rijndael)
* Blowfish
* CAST5
* Kuznyechik
* RC4
* DES
* 3DES
* Skipjack
* Safer+/++ (Bluetooth)
* IDEA
* AES

가장 유명한 대칭키 방식의 알고리즘 ➔ `AES`

[AES encryption 사이트](https://aesencryption.net/)

암호화 하고싶은 text와 key값을 적은 뒤 키의 복잡성(128bit 숫자가 높을 수록 더 복잡해지지만 더 많은 컴퓨터 자원을 더 많이 잡아먹는다)를 정하고 encrypt 하면 암호값이 생성된다. 암호값과 key값을 넣고 decrypt하면 원래의 text를 얻을 수 있다.

&nbsp;

## **4. 양방향 암호화 방법 - 비대칭키(공개키 암호화)**

비대칭키 방식은 공개키로 암호화한 암호문은 비공개키로만 복호화할 수 있다.
반대로 비공개키로 암호화했으면 공개키로만 복호화할 수 있다.

![](https://images.velog.io/images/dogfootbirdfoot/post/63b8b9ad-d808-477a-ac7b-aa8b89a3a0ae/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B75.png)

![](https://images.velog.io/images/dogfootbirdfoot/post/bce5081f-5d27-4b4e-98fb-21b35600d3fc/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B76.png)

**대칭키 방식의 한계**

![](https://images.velog.io/images/dogfootbirdfoot/post/2e0e3974-1518-4b80-a24a-808138b733c9/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B77.png)

key가 원하지 않는 사람에게도 노출되는 배달사고로 인해서 보안이 뚫릴 수 있다.

**비대칭키 방식의 해결**

![](https://images.velog.io/images/dogfootbirdfoot/post/d732e77d-8cdc-4f19-ab57-8bbd4e546430/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B78.png)

[RSA encryption 사이트](https://www.devglan.com/online-tools/rsa-encryption-decryption)

공개키를 공개해두고 누군가 암호문을 보내면 나만 가지고 있던 개인키로 복호화한다.

&nbsp;

## **5. 비대칭키(공개키) 방식을 이용한 전자서명**

![](https://images.velog.io/images/dogfootbirdfoot/post/e4fe1193-bdf2-4ae7-a0d1-ecddd71eb582/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B79.png)

개인키를 이용해서 text를 암호화 시키면 전자서명이 된다. 그리고 공개키와 전자셔명을 배포한다. 사람들이 이 공개키와 전자셔명을 가지고 복호화한 내용과 text가 동일하면 공개키를 가지고 있는 사람이 자신의 개인키로 만든 것임을 확신할 수 있다. (`RSA 방식`)

&nbsp;

## **6. 수업을 마치며**

비대칭키 방식에서는 개인키를 잘 관리해야 한다. 이것은 보안의 영역이다. 키를 보관하고 있는 컴퓨터가 안전해야 키가 유출되지 않는다. 따라서 암호화의 핵심은 단지 어떤 암호화 알고리즘을 쓰느냐를 넘어서 암호를 보관하고 있는 컴퓨터가 안전하게 지켜져야 한다. 암호화를 통해서 보안이 완성되지만 보안을 통해서 암호화가 지켜지기도 한다. 누가 먼저라고 할 수 없다.

암호의 보안을 높이는 방법은 간단하다. 키값을 길게하거나 hash값이 긴 알고리즘을 사용하는 것이다. 하지만 키값이 길어지면 그만큼 암호화나 복호화를 하는데 더 많은 컴퓨터 자원을 사용해야 한다. 적정 수준의 알고리즘을 선택하는 것은 쉬운 일이 아니다. 그래서 국가에서는 그 시대에 어울리는 적당한 암호화 방법을 권고하고 있다.

다음 표는 한국인터넷지능원에서 2018년에 발간한 암호 알고리즘 및 키 길이 이용 안내서 이다. 이러한 자료를 통해 권고안에 맞는 암호를 선택해서 사용하면 된다. 수학적 관념과 컴퓨터 성능이 발전함에 따라서 안전한 암호화 방식은 달라지기 때문에 최신 동향을 살펴보는 것이 중요하다.

![](https://images.velog.io/images/dogfootbirdfoot/post/78b0fa16-f447-43cc-9ae0-a817b216a292/%E1%84%80%E1%85%B3%E1%84%85%E1%85%B5%E1%86%B710.png)

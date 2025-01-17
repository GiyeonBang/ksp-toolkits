# UbuCon Korea 2023 - GPG 키사이닝 파티

GPG Keysigning Party 에 참여 하고자 하시는 분들은 다음과 같은 사항을 미리 준비하세요.  
도움이 필요 하시거나 문의 사항이 있는 경우, 고민 하지 마시고 [youngbin@ubuntu-kr.org](mailto:youngbin@ubuntu-kr.org) 으로 바로 연락해 주세요.
> 이번 키아시닝 파티는 UbuCon Korea 2023 프로그램의 일부로, 티켓 구입 하시고 오프라인으로 참여 하셔야 참여 가능합니다. [티켓은 여기에서 구입 가능합니다.](https://2023.ubuntu-kr.org/tickets/)

## PGP, GPG? 키사이닝 파티(Keysigning Party)?
PGP(Pretty Good Privacy) 는 이메일이나 파일 등을 암호화 하거나 전자서명을 할 수 있게 해 주는 공개키 암호화 방식을 사용하는 프로그램 입니다.
GPG(GNU Privacy Guard) 는 PGP 의 OpenPGP 표준의 자유/오픈소스 구현체이며 오늘날 대부분의 리눅스 배포판에서 사용 가능합니다.
PGP(혹은 GPG) 는 이메일과 파일 암호화에도 많이 사용되지만, 오늘날 오픈소스 프로젝트에서 바이너리와 패키지 그리고 패치파일이나 커밋에 서명을 하여 본인이 한 작업물임을 보증되도록 하기 위해 사용 되기도 합니다.

GPG Keysigning Party 는 각자의 GPG 키에 대한 Web of Trust(신뢰 망)을 구축하는 것을 목적으로 하는 행사입니다.
참여자들이 서로의 신원을 꼼꼼히 확인한 후 서로의 GPG 공개키에 서명을 해 주어 신뢰를 쌓는 형태입니다.
우리가 진행하는 키사이닝 파티 방식은 [Phil Zimmermann과 Len Sassaman의 Hash Based Method Party](http://www.cryptnet.net/fdp/crypto/keysigning_party/en/keysigning_party.html#hash_based)에 기반하여 조금 변형한 형태 입니다.

## 참가자 명단이 나오기 전
- GPG 키를 준비하세요. 아직 강력한 키가 없다면, [**이 문서를 참고하여 새로 준비합니다.**](../../create-gpg-key.md)
    - 키 길이는 최소 3072(4096을 권장합니다), 서명 알고리즘은 SHA256 또는 더 강력한 것(SHA512 권장합니다)을 사용하는 GPG 키를 준비 하셔야 합니다.
- 공개키를 키서버에 업로드 합니다. 이번 행사에 참석 하시는 분들은, [keyserver.ubuntu.com](https://keyserver.ubuntu.com) 에 업로드 해주세요.
    - 키서버에 업로드 하는 방법은 [**동일한 문서(공개키 생성 가이드)에 같이 기술되어 있습니다.**](../../create-gpg-key.md)
- 준비된 GPG 키를 [**이 문서를 참고하여 내보내기 하고, Clearsign 한 뒤,**](../../attending.md) [**이 제출 양식을 이용하여 제출합니다.**](https://docs.google.com/forms/d/e/1FAIpQLSeZgAc2-GDr17y6O7_YawxaGUYR4v_OXaOqlCKPIwyVYX1jyQ/viewform?usp=sf_link)
    - 양식을 통해 **서명된(Clearsign된) 공개키 블록**과, **해당 공개키의 핑거프린트**를 제출하게 됩니다.
    - 늦어도 **9월 5일 23시 59분(한국시간)** 까지 모두 제출해 주시기 바랍니다.
    - 양식을 통해 공개키를 제출하시면 양식 응답 사본을 이메일로 받으시게 되며, 받으신 메일을 통해 제출기간 동안 응답 수정이 가능합니다.

## 참가자 명단이 나온 후

- 명단이 나오면 별도로 공지를 해 드립니다.
- 본 문서의 **파일 목록** 색션에 있는 파일을 모두 다운로드 합니다.
- 각 참가자 목록 파일(`*.txt`)의 SHA256 체크섬을 계산한 후, 각 참가자 목록 파일에 대한 체크섬 파일(`*.txt.sha256`)에 포함된 체크섬과 일치하는지 확인합니다.
    - 다음 명령행을 실행하여 체크섬을 계산합니다: `sha256sum (파일명)`
    - 실행 예시: `sha256sum ksp-20180915-2.txt`
    - 체크섬 일치 확인 실행 예시: `sha256sum ksp-20180915-2.txt | diff ksp-20180915-2.txt.sha256 -` (아무 내용도 뜨지 않아야 함)
- 각 참가자 목록 파일에 대한 서명 파일(`*.txt.asc`)과 각 참가자 목록 파일의 체크섬 파일에 대한 서명 파일(`*.txt.sha256.asc`)의 서명이 올바른지 검증하세요.
    - 서명을 검증하려면 먼저 서명에 쓰인 GPG 키의 공개키를 키서버에서 불러옵니다.
        - 핑거프린트가 `D8C8 103B 16C5 6E34 B56F 9A42 30B7 29F7 1213 8599` 인 GPG 키로 서명될 예정이며, keyserver.ubuntu.com 에서 불러올 수 있습니다.
        - `gpg --keyserver keyserver.ubuntu.com --recv-keys D8C8103B16C56E34B56F9A4230B729F712138599`
            - [해당 GPG 키 정보 보기](http://keyserver.ubuntu.com/pks/lookup?op=vindex&search=0x30B729F712138599)
    - Windows(Kleopatra) : Decrypt/Verify... 를 눌러서 검증할 파일을 열어 검증을 진행합니다.
    - MacOS(GPG Suite) : 검증할 파일을 우클릭 한 다음, 서비스 > OpenPGP: Verify Signature of File 를 눌러 진행합니다.
    - Linux: 
        - 다음 명령행을 실행하여 검증합니다.: `gpg --verify < (파일명)`
        - 실행 예시: `gpg --verify < ksp-20180915.txt.sha256.asc`
- 체크섬이 일치하고, 서명이 올바르다면. 이제 참가자 목록 파일을 프린터로 인쇄합니다.
- 인쇄한 종이에 본인이 계산한 SHA256 체크섬을 펜으로 직접 옮겨 적습니다.

## 행사 당일
- 각 참가자 목록 파일을 인쇄한 것에 체크섬을 적은 종이와 펜 그리고 본인의 **신분증** 을 지참합니다.
    - 성인의 경우 주민등록증, 운전면허증, 여권 또는 정부기관이 발행한 본인의 사진과 실명이 포함된 신분증을 지참합니다.
    - 청소년의 경우 여권, 청소년증, 학생증 또는 정부기관이 발행한 본인의 사진과 실명이 포함된 신분증을 지참합니다.
    - 외국인의 경우 여권, 외국인 등록증 또는 국제학생증을 지참합니다.
    - 신분증의 이름과 GPG 키에 있는 이름이 동일해야 합니다.
- 키사이닝 세션 시간에 다같이 체크섬을 확인합니다.
- 돌아 다니면서 키사이닝을 교환할 분을 만납니다.
    - 체크섬을 확인합니다. 다같이 확인할 때 확인한 경우 건너뜁니다.
    - 체크섬 확인이 불가능한 경우, 목록에 적힌 핑거프린트와 상대방이 제시하는 핑거프린트를 직접 대조하여 확인합니다.
    - 신분증을 제시하여 서로의 신원을 확인합니다.
    - 충분히 확인된 경우, 종이에서 체크표시 합니다.
    - 만나서 인사 한 김에, 수다 떠는 시간을 조금 가져봅니다.
## 행사 종료 후
[이 문서](../../sign-and-send-key.md) 를 참고해서 신원을 확인한 분들의 공개키에 키사이닝을 한 후 원래 주인분께 공유합니다.  
그리고 본인의 신원을 확인한 분들로부터 키사이닝된 본인의 키를 받아 불러옵니다.

> 참고: 신원을 확인 한 분들이여도, 신뢰하지 않는 사람이라면 꼭 키사이닝을 해 주지 않아도 됩니다. 신원을 확인 했고, 본인이 신뢰하는 분들에게 키사이닝을 해 주는 것이 Web of Trust 를 만들어 가는데 더 도움이 됩니다.

## 파일 목록

> 추후 배포됩니다.

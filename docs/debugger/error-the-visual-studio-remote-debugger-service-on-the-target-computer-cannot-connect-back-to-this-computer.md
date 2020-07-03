---
title: 오류 - 대상 컴퓨터의 Visual Studio 원격 디버거 서비스를 이 컴퓨터에 다시 연결할 수 없음
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b372b1f6fcdab357e87ff91fa4df257e8da7d68d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536671"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>오류: 대상 컴퓨터의 Visual Studio 원격 디버거 서비스가 이 컴퓨터에 다시 연결할 수 없습니다.
이 오류는 디버깅에 사용하려는 컴퓨터에 연결할 때 인증되지 않는 사용자 계정으로 원격 디버거 서비스가 실행되고 있음을 의미합니다. 이 오류는 레거시 디버깅 엔진을 사용하여 원격 디버그하고 원격 디버거가 서비스로 실행되고 있는 경우 발생할 수 있습니다.

 다음 표에는 컴퓨터에 액세스할 수 있는 계정이 나와 있습니다.

|시나리오|LocalSystem 계정|도메인 계정|두 컴퓨터에서 사용자 이름과 암호가 동일한 로컬 계정|
|-|-|-|-|
|동일한 도메인의 두 컴퓨터|예|예|예|
|도메인에서 양방향 트러스트가 있는 두 컴퓨터|아니요|아니요|예|
|작업 그룹의 한 컴퓨터 또는 두 컴퓨터|아니요|아니요|예|
|서로 다른 도메인의 컴퓨터|아니요|아니요|예|

 이 밖에도 다음 지침을 따릅니다.

- 모든 프로세스를 디버깅할 수 있으려면 Visual Studio 원격 디버거 서비스를 실행하는 데 사용되는 계정이 원격 컴퓨터의 관리자 계정이어야 합니다.

- 또한 계정에는 **로컬 보안 정책** 관리 도구를 사용하는 원격 컴퓨터에 대한 `Log on as a service` 권한이 부여되어야 합니다.

- 로컬 계정을 사용하여 컴퓨터에 액세스하는 경우 Visual Studio 원격 디버거 서비스를 로컬 계정으로 실행해야 합니다.

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. 원격 컴퓨터에서 Visual Studio 원격 디버거 서비스가 올바르게 설정되어 있는지 확인합니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.

2. 위 표에 나와 있듯이 디버거 호스트 컴퓨터에 액세스할 수 있는 계정으로 원격 디버거 서비스를 실행합니다.

### <a name="to-add-log-on-as-a-service-privilege"></a>"서비스로 로그온" 권한을 추가하려면

1. **시작** 메뉴에서 **제어판**을 선택합니다.

2. 필요한 경우 제어판에서 **클래식 보기**를 선택합니다.

3. **관리 도구**를 두 번 클릭합니다.

4. 관리 도구 창에서 **로컬 보안 정책**을 두 번 클릭합니다.

5. **로컬 보안 설정** 창에서 **로컬 정책** 폴더를 확장합니다.

6. **사용자 권한 할당**을 클릭합니다.

7. **P정책** 열에서 **서비스로 로그온**을 두 번 클릭하여 현재 로컬 그룹 정책 할당을 **서비스로 로그온** 대화 상자에 표시합니다.

8. 새 사용자를 추가하려면 **사용자 또는 그룹 추가** 단추를 클릭합니다.

9. 사용자 추가를 마쳤으면 **확인**을 클릭합니다.

### <a name="to-work-around-this-error"></a>이 오류를 해결하려면

- 원격 디버깅 모니터를 서비스가 아닌 애플리케이션으로 실행합니다.

## <a name="see-also"></a>참조
- [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)
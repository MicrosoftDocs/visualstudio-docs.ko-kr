---
title: 오류 - Windows 통합 인증을 사용할 수 없기 때문에 디버깅 실패 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9c4f0e25449b0e108ac39662ec52a0ba9abc217
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460840"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>오류: Windows 통합 인증을 사용할 수 없기 때문에 디버깅 실패
인증 오류로 인해 디버깅을 요청한 사용자를 인증할 수 없습니다. 웹 애플리케이션 또는 XML Web services를 한 단계씩 실행하려고 할 때 이 오류가 발생할 수 있습니다. 이 오류는 Windows 통합 인증이 사용할 수 없도록 설정되어 있기 때문에 발생할 수 있습니다. 이 인증을 사용하려면 "통합 Windows 인증을 사용하려면"의 단계를 따릅니다.

 Windows 통합 인증을 사용하도록 설정했는데도 이 오류가 계속 발생하면 **Windows 도메인 서버의 다이제스트 인증**을 사용하도록 설정했기 때문일 수 있습니다. 이 경우에는 네트워크 관리자에게 문의하십시오.

### <a name="to-enable-integrated-windows-authentication"></a>Windows 통합 인증을 사용하려면

1. 관리자 계정을 사용하여 웹 서버에 로그온합니다.

2. **시작**을 클릭한 다음, **제어판**을 클릭합니다.

3. **제어판**에서 **관리 도구**를 두 번 클릭합니다.

4. **인터넷 정보 서비스**를 두 번 클릭합니다.

5. 웹 서버 노드를 클릭합니다.

     서버 이름 아래에 **웹 사이트** 폴더가 열립니다.

6. 모든 웹 사이트 또는 개별 웹 사이트에 대해 인증을 구성할 수 있습니다. 모든 웹 사이트에 대해 인증을 구성하려면 **웹 사이트** 폴더를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다. 개별 웹 사이트에 대해 인증을 구성하려면 **웹 사이트** 폴더를 열고 해당 웹 사이트를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다.

     **속성** 대화 상자가 표시됩니다.

7. **디렉터리 보안** 탭을 클릭합니다.

8. **익명 액세스 및 인증 제어** 섹션에서 **편집**을 클릭합니다.

     **인증 방법** 대화 상자가 표시됩니다.

9. **인증된 액세스** 아래에서 **통합 Windows 인증**을 선택합니다.

10. **확인**을 클릭하여 **인증 방법** 대화 상자를 닫습니다.

11. **확인**을 클릭하여 **속성** 대화 상자를 닫습니다.

12. **인터넷 정보 서비스** 창을 닫습니다.

### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Windows Vista/IIS 7에서 통합 Windows 인증을 사용하려면

1. 관리자 계정을 사용하여 웹 서버에 로그온합니다.

2. Windows 인증 및 II6 관리 호환성을 설정하지 않은 경우 다음 단계에 따라 이를 설정합니다.

    1. **시작**, **제어판**, **프로그램**을 차례로 클릭합니다.

    2. **프로그램 및 기능**에서 **Windows 기능 사용/사용 안 함**을 클릭합니다.

         사용자 Access Control 대화 상자가 표시되고 작업을 계속할 수 있는 권한이 있는지 묻습니다.

    3. **Continue(계속)** 를 클릭합니다.

         Windows 기능 대화 상자가 표시됩니다.

    4. 기능 목록에서 **인터넷 정보 서비스** 노드를 확장합니다.

    5. **인터넷 정보 서비스** 아래에서 **World Wide Web 서비스** 노드를 확장합니다.

    6. **World Wide Web 서비스** 아래에서 **보안**을 클릭합니다.

    7. **Windows 인증**을 클릭합니다.

    8. **인터넷 정보 서비스** 아래에서 **웹 관리 도구** 노드를 확장합니다.

    9. **웹 관리 도구** 아래에서 **IIS 6 관리 호환성** 노드를 확장하고 **IIS 6 메타베이스 및 IIS 6 구성 호환성** 확인란을 선택합니다.

    10. **웹 관리 도구** 아래에서 **IIS 관리 콘솔**을 선택하고 **확인**을 클릭합니다.

    11. 컴퓨터를 다시 시작하여 이러한 변경 내용을 적용합니다.

3. **시작**을 클릭한 다음, **제어판**을 클릭합니다.

4. **클래식 보기**를 클릭한 다음, **관리 도구**를 두 번 클릭합니다.

5. **이름** 열에서 **IIS(인터넷 정보 서비스) 관리자**를 두 번 클릭합니다.

6. **연결** 열에서 해당 서버의 노드를 확장합니다.

     서버 이름 아래에 **웹 사이트** 폴더가 열립니다.

7. **웹 사이트** 노드를 확장하고 통합 Windows 인증을 사용할 웹 사이트를 클릭합니다.

8. 가운데 창의 제목이 선택한 웹 사이트의 이름으로 변경됩니다. 이 창의 **IIS** 머리글 아래에서 **인증**을 두 번 클릭합니다.

     창의 제목이 **인증**으로 변경됩니다.

9. **인증** 창의 **이름** 열에서 **Windows 인증**을 마우스 오른쪽 단추로 클릭한 다음, **사용**을 클릭합니다.

10. **IIS(인터넷 정보 서비스) 관리자** 창을 닫습니다.

## <a name="see-also"></a>참조
- [웹 애플리케이션 디버그: 오류 및 문제 해결](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Microsoft Digest 인증](/windows/win32/secauthn/microsoft-digest-authentication)
- [IIS 7.0 및 Visual Studio를 사용하여 Windows Vista에서 웹 애플리케이션 실행](https://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)
---
title: '방법: IIS 속성 설정 확인 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- IIS, property settings
- debugging Web applications, troubleshooting
- IIS administration tool
- Web applications, setting properties
- properties [debugger], setting with IIS administration tool
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3dd516151f7a3656da1bae195870e8cc29528cfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846430"
---
# <a name="how-to-verify-iis-property-settings"></a>방법: IIS 속성 설정 확인

IIS 관리 도구를 사용하여 웹 애플리케이션의 속성을 설정할 수 있습니다. 이러한 속성이 제대로 설정되어 있어야 애플리케이션이 실행되므로 일반적으로 문제를 해결하는 데는 이러한 설정을 확인하는 단계가 필요합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="to-check-iis-settings-for-the-web-application"></a>웹 애플리케이션에 대한 IIS 설정을 확인하려면

1. **관리 도구** 창을 엽니다. **시작** 메뉴에서 **프로그램**을 가리킨 다음 **관리 도구**를 클릭합니다. **관리 도구**가 **프로그램** 메뉴에 없으면 **제어판**에서 찾습니다.

   - Windows 2000에서는 **인터넷 서비스 관리자**를 선택합니다.

   - Windows XP에서는 **인터넷 정보 서비스**를 선택합니다.

   - Windows Server 2003에서는 **사용자 서버 관리**를 두 번 클릭합니다.

        **사용자 서버 관리** 창이 열립니다. **애플리케이션 서버**에서 **이 애플리케이션 서버 관리**를 클릭합니다.

        **애플리케이션 서버** 창이 열립니다. 왼쪽 창에서 **IIS(인터넷 정보 서비스) 관리자** 노드를 엽니다.

2. 대화 상자에서 현재 컴퓨터의 트리 컨트롤 노드를 클릭합니다. **웹 사이트** 노드를 클릭하고 웹 애플리케이션의 노드를 선택합니다. 이 노드는 웹 사이트 노드(**기본 웹 사이트** 노드의 형제 노드)이거나 기존 웹 사이트 노드 아래에 있는 가상 디렉터리 노드일 수 있습니다.

3. 웹 애플리케이션을 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **속성**을 클릭합니다.

4. 웹 애플리케이션에 대한 보안 설정을 확인합니다.

   1. 웹 애플리케이션의 **속성** 창에서 **디렉터리 보안** 탭을 클릭하고 **편집**을 클릭합니다.

   2. **인증 방법** 대화 상자에서 **익명 액세스 가능** 및 **Windows 통합 인증**이 선택되어 있지 않으면 이를 선택합니다.

   3. **확인**을 클릭하여 **인증 방법** 대화 상자를 닫습니다.

5. ATL 서버 애플리케이션의 경우 DEBUG 동사가 ISAPI 확장과 관련이 있는지 여부를 확인합니다. 자세한 내용은 [방법: DEBUG 동사를 확장과 연결](https://msdn.microsoft.com/library/50d261d3-4bd4-41c0-b44e-3591086f121e)을 참조하세요.

6. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션의 경우, 해당 애플리케이션의 가상 폴더에 **IIS(인터넷 정보 서비스) 관리자**, **인터넷 서비스 관리자** 또는 **인터넷 정보 서비스**에 설정된 애플리케이션 이름이 있는지 확인합니다.

   1. 웹 애플리케이션 **속성** 창에서, 애플리케이션이 가상 디렉터리에 있는 경우에는 **디렉터리** 탭을 선택하고 애플리케이션이 웹 사이트에 있는 경우에는 **홈 디렉터리** 탭을 선택합니다.

   2. **로컬 경로**의 이름이 애플리케이션이 실제로 배포된 디렉터리의 이름과 일치하는지 확인합니다.

   3. **애플리케이션 설정**에서 애플리케이션이 들어 있는 루트 디렉터리의 이름을 입력합니다.

   4. **확인**을 클릭하여 **속성** 대화 상자를 닫습니다.

7. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션의 경우, **ASP.NET** 탭을 클릭하여 올바른 버전의 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]가 지정되어 있는지 확인합니다.

8. **확인**을 클릭하여 **속성** 대화 상자를 닫습니다.

9. **확인**을 클릭하여 **IIS(인터넷 정보 서비스) 관리자**, **인터넷 서비스 관리자** 또는 **인터넷 정보 서비스** 대화 상자를 닫습니다.

## <a name="see-also"></a>참조

- [문제 해결](../debugger/debugging-web-applications-troubleshooting.md)
---
title: '방법: 제한 된 권한으로 ClickOnce 응용 프로그램 디버깅 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ClickOnce applications
- ClickOnce deployment, debugging
- ClickOnce applications, debugging
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d60f88c4d1532a03922f12f21bb9b455ef5d84d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153794"
---
# <a name="how-to-debug-a-clickonce-application-with-restricted-permissions"></a>How to: Debug a ClickOnce Application with Restricted Permissions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개발자는 대부분 완전 신뢰 사용 권한으로 개발 컴퓨터를 실행하므로, ClickOnce 애플리케이션을 디버그할 때 제한된 권한으로 실행하는 최종 사용자에게 표시될 수 있는 것과 동일한 보안 예외가 표시되지 않습니다.  
  
 이러한 예외를 catch하려면 최종 사용자와 동일한 사용 권한으로 애플리케이션을 디버그해야 합니다. **프로젝트 디자이너** 의 **보안**페이지에서 제한된 권한으로 디버그를 사용하도록 설정할 수 있습니다.  
  
 또한 웹 서비스를 호출하는 애플리케이션을 개발할 때 이러한 웹 서비스는 종종 개발 컴퓨터에 있습니다. 배포된 후 최종 사용자는 다른 URL에서 이러한 웹 서비스에 액세스합니다. 디버그하는 동안 최종 사용자 환경을 에뮬레이트하려면 URL을 지정할 수 있습니다. 그러면 디버거는 마치 해당 URL에서 호출된 것처럼 웹 서비스를 처리합니다.  
  
### <a name="to-enable-debugging-with-restricted-permissions"></a>제한된 권한으로 디버깅을 사용하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **프로젝트 디자이너**에서 **보안** 탭을 클릭합니다.  
  
3. **ClickOnce 보안 설정 사용** 확인란을 선택한 다음 **부분 신뢰 애플리케이션** 옵션 단추를 클릭합니다.  
  
4. **고급** 단추를 클릭합니다.  
  
5. **선택한 권한 집합으로 이 애플리케이션 디버그** 확인란을 선택한 다음 **확인**을 클릭합니다.  
  
     애플리케이션을 디버그할 때는 사용 권한 집합에 속하지 않는 권한에 액세스하려는 모든 시도가 보안 예외를 발생시킵니다.  
  
### <a name="to-specify-a-url-for-debugging"></a>디버깅에 대한 URL을 지정하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **프로젝트 디자이너**에서 **보안** 탭을 클릭합니다.  
  
3. **ClickOnce 보안 설정 사용** 확인란을 선택한 다음 **부분 신뢰 애플리케이션** 옵션 단추를 클릭합니다.  
  
4. **고급** 단추를 클릭합니다.  
  
5. **선택한 권한 집합으로 이 애플리케이션 디버그** 확인란을 선택한 다음 **확인**을 클릭합니다.  
  
6. **다음 URL에서 다운로드한 것처럼 이 애플리케이션을 디버그** 텍스트 상자에 URL 또는 네트워크 경로를 입력합니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: ClickOnce 응용 프로그램에 대 한 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 응용 프로그램에 대 한 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)

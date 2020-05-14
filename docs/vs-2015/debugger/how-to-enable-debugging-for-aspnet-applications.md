---
title: '방법: ASP.NET 응용 프로그램에 대 한 디버깅 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726e964a0db2fae1b902f54a14e206dbc03a148
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477005"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>방법: ASP.NET 애플리케이션에 디버깅 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

디버깅을 사용하려면 **프로젝트 속성** 페이지와 애플리케이션의 web.config 파일 둘 다에서 사용하도록 설정해야 합니다.  
  
> [!NOTE]  
> 활성 설정 또는 버전에 따라 표시되는 대화 상자 및 메뉴 명령이 도움말에 설명된 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](/previous-versions/zbhkx167(v=vs.140))을 참조하세요.  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>프로젝트 속성에서 ASP.NET 디버깅을 사용하도록 설정하려면(Visual Basic/C#)  
  
1. **솔루션 탐색기**에서 웹 프로젝트 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.  
  
2. 프로젝트 속성 페이지에서 **웹** 탭을 클릭합니다.  
  
3. **디버거**아래에서 **ASP.NET** 확인란을 선택합니다.  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>web.config 파일에서 디버깅을 사용하도록 설정하려면  
  
1. 표준 텍스트 편집기 또는 XML 파서를 사용하여 web.config 파일을 엽니다.  
  
    > [!NOTE]  
    > 그러나 웹 브라우저를 사용하여 원격으로 파일에 액세스할 수 없습니다. 보안상의 이유로 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 는 브라우저에서 Web.config 파일에 직접 액세스할 수 없도록 Microsoft IIS를 구성합니다. 브라우저를 사용하여 구성 파일에 액세스하려고 하면 HTTP 액세스 오류 403(사용할 수 없음)이 표시됩니다.  
  
2. Web.config는 XML 파일이므로 태그로 표시된 중첩된 섹션을 포함합니다. `configuration/system.web/compilation` 요소를 찾습니다. 컴파일 요소가 없는 경우 생성합니다.  
  
3. `compilation` 요소에 `debug` 특성이 없으면 요소에 특성을 추가합니다.  
  
4. `debug` 특성 값이 `true`로 설정되었는지 확인합니다.  
  
web.config 파일은 다음 예제와 같습니다. 구성 요소와 system.web 요소 사이에 섹션이 있을 수 있습니다.  
  
- 구성 요소와 system.web 요소 간의 요소 섹션  
  
- system.web 요소와 컴파일 요소 간의 요소 섹션  
  
- 컴파일 요소에는 다른 특성 및 요소가 포함될 수 있음  
  
## <a name="example"></a>예제  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]가 Web.config 파일의 변경 내용을 자동으로 검색하고 새 구성 설정을 적용합니다. 변경 내용을 적용하기 위해 컴퓨터를 다시 시작하거나 IIS 서버를 다시 시작할 필요가 없습니다.  
  
웹 사이트에는 여러 개의 가상 디렉터리 및 하위 디렉터리가 포함될 수 있으며 각 디렉터리에 Web.config 파일이 있을 수도 있습니다. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션은 URL 경로의 상위 수준에 있는 Web.config 파일에서 설정을 상속합니다. 계층적 구성 파일을 사용하면 계층 구조의 모든 하위 애플리케이션 등 여러 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션에 대한 설정을 동시에 변경할 수 있습니다. 그러나 `debug` 가 계층 구조의 하위 파일에서 설정된 경우 상위 값을 재정의합니다.  
  
예를 들어 `www.microsoft.com/aaa/Web.config`에서 `debug="true"`를 지정할 수 있으며 aaa 폴더 또는 aaa의 모든 하위 폴더에 있는 모든 응용 프로그램은 해당 설정을 상속 합니다. 따라서 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 응용 프로그램이 `www.microsoft.com/aaa/bbb`되는 경우 `www.microsoft.com/aaa/ccc`, `www.microsoft.com/aaa/ddd`등의 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 응용 프로그램에 따라 해당 설정이 상속 됩니다. 단, 해당 애플리케이션 중 하나가 고유한 하위 Web.config 파일을 통해 설정을 재정의하는 경우는 예외입니다.  
  
디버그 모드를 사용하도록 설정하면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션의 성능에 큰 영향을 줍니다. 릴리스 애플리케이션을 배포하거나 성능을 측정하기 전에 디버그 모드를 사용하지 않도록 설정해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
[ASP.NET 및 AJAX 애플리케이션 디버그](../debugger/debugging-aspnet-and-ajax-applications.md)  

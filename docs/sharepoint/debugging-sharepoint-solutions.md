---
title: SharePoint 솔루션 디버깅 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d83c8ffd4fe5ebb627b70fa07f010bdc713225dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72984484"
---
# <a name="debug-sharepoint-solutions"></a>SharePoint 솔루션 디버깅
  디버거를 사용 하 여 SharePoint 솔루션을 디버그할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 디버깅을 시작 하면에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트 파일을 sharepoint 서버에 배포한 다음 웹 브라우저에서 sharepoint 사이트의 인스턴스를 엽니다. 다음 섹션에서는에서 SharePoint 응용 프로그램을 디버깅 하는 방법을 설명 합니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [디버깅 사용](#enable-debugging)

- [F5 디버그 및 배포 프로세스](#f5-debug-and-deployment-process)

- [SharePoint 프로젝트 기능](#sharepoint-project-features)

- [워크플로 디버깅](#debug-workflows)

- [기능 이벤트 수신기 디버그](#debug-feature-event-receivers)

- [Ehanced 디버깅 정보 사용](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>디버깅 사용
 에서 SharePoint 솔루션을 처음 디버그할 때 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 대화 상자에서 web.config 파일이 디버깅을 사용 하도록 구성 되지 않은 것으로 경고 합니다. web.config 파일은 SharePoint server를 설치할 때 생성 됩니다. 자세한 내용은 [Web.config 파일 작업](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14))을 참조 하세요. 이 대화 상자에서는 디버깅을 사용 하도록 설정 하기 위해 web.config 파일을 디버깅 하거나 수정 하지 않고 프로젝트를 실행 하는 옵션을 제공 합니다. 첫 번째 옵션을 선택하면 프로젝트가 정상적으로 실행됩니다. 두 번째 옵션을 선택하면 web.config 파일이 다음과 같이 구성됩니다.

- 호출 스택 켜기 ( `CallStack="true"` )

- 에서 사용자 지정 오류 사용 안 함 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="Off" />` )

- 컴파일 디버깅 사용 ( `<compilation debug="true">` )

  결과 web.config 파일은 다음과 같습니다.

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <configuration>
        ...
        <SharePoint>
            <SafeMode MaxControls="200"
                CallStack="true"
                DirectFileDependencies="10"
                TotalFileDependencies="50"
                AllowPageLevelTrace="false">
                ...
            </SafeMode>
        ...
        </SharePoint>
        <system.web>
            ...
            <customErrors mode="Off" />
            ...
            <compilation debug="true">
            ...
            </compilation>
            ...
        </system.web>
        ...
    </configuration>
```

 변경 내용을 취소 하 고 디버깅을 사용 하지 않도록 설정 하려면 web.config 파일에서 다음을 변경 합니다 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] .

- 호출 스택 해제 ( `CallStack="false"` )

- 에서 사용자 지정 오류 사용 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="On" />` )

- 컴파일 디버깅 사용 안 함 ( `<compilation debug="false">` )

## <a name="f5-debug-and-deployment-process"></a>F5 디버그 및 배포 프로세스
 SharePoint 프로젝트를 디버그 모드에서 실행 하는 경우 SharePoint 배포 프로세스는 다음 작업을 수행 합니다.

1. 사용자 지정 가능한 배포 전 명령을 실행 합니다.

2. 명령을 사용 하 여 웹 솔루션 패키지 (.wsp) 파일을 만듭니다. [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] .Wsp 파일에는 필요한 모든 파일 및 기능이 포함 되어 있습니다. 자세한 내용은 [솔루션 개요](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14))를 참조 하세요.

3. SharePoint 솔루션이 팜 솔루션인 경우는 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 지정 된 사이트에 대 한 응용 프로그램 풀을 재생 합니다 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] . 이 단계에서는 작업자 프로세스에서 잠긴 파일을 해제 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 합니다.

4. 이전 버전의 패키지가 이미 있는 경우 .wsp 파일에서 이전 버전의 기능 및 파일을 취소 합니다. 이 단계에서는 기능을 비활성화 하 고, 솔루션 패키지를 제거한 다음, SharePoint 서버에서 솔루션 패키지를 삭제 합니다.

5. .Wsp 파일에 최신 버전의 기능 및 파일을 설치 합니다. 이 단계에서는 SharePoint 서버에 솔루션을 추가 하 고 설치 합니다.

6. 워크플로의 경우 워크플로 어셈블리를 설치 합니다. *어셈블리 위치* 속성을 사용 하 여 해당 위치를 변경할 수 있습니다.

7. 범위가 사이트 또는 웹 인 경우 SharePoint에서 프로젝트의 기능을 활성화 합니다. 팜 및 WebApplication 범위의 기능은 활성화 되지 않습니다.

8. 워크플로의 경우 **Sharepoint 사용자 지정 마법사**에서 선택한 sharepoint 라이브러리, 목록 또는 사이트에 워크플로를 연결 합니다.

   > [!NOTE]
   > 이 연결은 마법사에서 **워크플로를 자동으로 연결** 을 선택한 경우에만 발생 합니다.

9. 사용자 지정 가능한 배포 후 명령을 실행 합니다.

10. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]프로세스에 디버거를 연결 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 합니다 (*w3wp.exe*). 프로젝트 형식에서 *샌드박스가 적용 된 솔루션* 속성을 변경할 수 있고 해당 값이 **true**로 설정 된 경우 디버거는 다른 프로세스 (*SPUCWorkerProcess.exe*)에 연결 됩니다. 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

11. SharePoint 솔루션이 팜 솔루션인 경우 JavaScript 디버거를 시작 합니다.

12. 웹 브라우저에 적절 한 라이브러리, 목록 또는 사이트 페이지를 표시 합니다.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 각 작업이 완료 된 후에 출력 창에 상태 메시지를 표시 합니다. 작업을 완료할 수 없는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 오류 목록 창에 오류 메시지를 표시 합니다.

## <a name="sharepoint-project-features"></a>SharePoint 프로젝트 기능
 기능은 사이트 정의를 사용 하 여 사이트 수정을 간소화 하는 이식 가능 하 고 모듈화 된 기능 단위입니다. [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)]특정 범위에 대해 활성화할 수 있고 사용자가 특정 목표 또는 작업을 수행 하는 데 도움이 되는 WSS () 요소 패키지 이기도 합니다. 템플릿은 기능으로 배포 됩니다.

 디버그 모드에서 프로젝트를 실행 하는 경우 배포 프로세스는 *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*의 *기능* 디렉터리에 폴더를 만듭니다. 기능 이름의 형식은 *프로젝트 이름*_Feature*x*(예: TestProject_Feature1)입니다.

 기능 디렉터리의 솔루션 폴더에는 *기능 정의* 파일 및 *워크플로 정의* 파일이 포함 되어 있습니다. 기능 정의 파일 (Feature.xml)에서는 프로젝트 기능의 파일에 대해 설명 합니다. 프로젝트 정의 파일 (*Elements.xml*)은 프로젝트 템플릿을 설명 합니다. *Elements.xml* 는 **솔루션 탐색기**에서 찾을 수 있지만 솔루션 패키지를 만들 때 Feature.xml 생성 됩니다. 이러한 파일에 대 한 자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)을 참조 하세요.

## <a name="debug-workflows"></a>워크플로 디버깅
 워크플로 프로젝트를 디버깅할 때는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 해당 형식에 따라 워크플로 템플릿을 라이브러리 또는 목록에 추가 합니다. 그런 다음 워크플로 템플릿을 수동으로 시작 하거나 항목을 추가 하거나 업데이트할 수 있습니다. 그런 다음를 사용 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 하 여 워크플로를 디버그할 수 있습니다.

> [!NOTE]
> 다른 어셈블리에 대 한 참조를 추가 하는 경우 해당 어셈블리가 전역 어셈블리 캐시에 설치 되어 있는지 확인 [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] 합니다 (). 그렇지 않으면 워크플로 솔루션이 실패 합니다. 어셈블리를 설치 하는 방법에 대 한 자세한 내용은 [수동으로 문서 또는 항목에서 워크플로 시작](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)을 참조 하세요.

 그러나 배포 프로세스에서 워크플로를 시작 하지는 않습니다. SharePoint 웹 사이트에서 워크플로를 시작 해야 합니다. Microsoft Office Word 2010와 같은 클라이언트 응용 프로그램을 사용 하거나 별도의 서버 쪽 코드를 사용 하 여 워크플로를 시작할 수도 있습니다. **SharePoint 사용자 지정 마법사**에 지정 된 방법 중 하나를 사용 합니다.

 예를 들어 워크플로를 수동으로 시작할 수 있도록 지정한 경우 라이브러리나 목록의 항목에서 직접 워크플로를 시작 합니다. 워크플로를 수동으로 시작 하는 방법에 대 한 자세한 내용은 [수동으로 문서 항목에서 워크플로 시작](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963)을 참조 하세요.

## <a name="debug-feature-event-receivers"></a>기능 이벤트 수신기 디버그
 기본적으로 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sharepoint 응용 프로그램을 실행 하면 해당 기능이 sharepoint 서버에서 자동으로 활성화 됩니다. 그러나에서 기능을 활성화할 때 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거가 아닌 다른 프로세스에서 실행 되기 때문에이로 인해 기능 이벤트 수신기를 디버그할 때 문제가 발생 합니다. 즉, 중단점과 같은 일부 디버깅 기능이 제대로 작동 하지 않습니다.

 SharePoint에서 기능의 자동 활성화를 사용 하지 않도록 설정 하 고 기능 이벤트 수신기의 적절 한 디버깅을 허용 하려면 디버깅 하기 전에 프로젝트의 **활성 배포 구성** 속성 값을 **활성화 안 함** 으로 설정 합니다. 그런 다음 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 SharePoint 애플리케이션의 디버깅을 시작한 후 SharePoint에서 수동으로 기능을 활성화합니다. 기능을 활성화 하려면 SharePoint에서 **사이트 작업** 메뉴를 열고 **사이트 설정**을 선택한 다음 **사이트 기능 관리** 링크를 선택 하 고 기능 옆에 있는 **활성화** 단추를 선택 하 여 정상적으로 디버깅을 계속 합니다.

## <a name="enable-enhanced-debugging-information"></a>향상 된 디버깅 정보 사용
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]프로세스 (devenv.exe), [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sharepoint 호스트 프로세스 (*vssphost4.exe*), sharepoint 및 WCF 계층 간의 복잡 한 상호 작용으로 인해 빌드, 배포 등을 수행 하는 동안 발생 하는 오류를 진단 하는 것이 어려울 수 있습니다. 이러한 오류를 해결 하기 위해 향상 된 디버깅 정보를 사용할 수 있습니다. 이렇게 하려면 Windows 레지스트리에서 다음 레지스트리 키로 이동 합니다.

 **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\11.0\SharePointTools**

 "EnableDiagnostics" **REG_DWORD** 값이 아직 없는 경우 수동으로 만드십시오. "EnableDiagnostics" 값을 "1"로 설정 합니다.

 이 키 값을 1로 설정 하면에서를 실행 하는 동안 프로젝트 시스템 오류가 발생할 때마다 스택 추적 정보가 **출력** 창에 표시 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 됩니다. 고급 디버깅 정보를 사용하지 않도록 설정하려면 EnableDiagnostics를 다시 0으로 설정하거나 이 값을 삭제합니다.

 다른 SharePoint 레지스트리 키에 대 한 자세한 내용은 [Visual Studio의 sharepoint 도구에 대 한 디버그 확장](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 문제 해결](../sharepoint/troubleshooting-sharepoint-solutions.md)

---
title: SharePoint 솔루션 문제 해결 | Microsoft Docs
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Tools.SharePoint.Errors.Debugging
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fcb30056021a865d0b0e605de462ff72ced5a383
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73661892"
---
# <a name="troubleshoot-sharepoint-solutions"></a>SharePoint 솔루션 문제 해결
  디버거를 사용 하 여 SharePoint 솔루션을 디버그할 때 다음과 같은 문제나 경고가 발생할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 자세한 내용은 [SharePoint 2007 워크플로 솔루션 디버그](https://msdn.microsoft.com/3a5392f3-66f3-48be-956e-02de23fa6247)를 참조 하세요.

## <a name="token-restrictions-in-sandboxed-visual-web-parts"></a>샌드 박싱된 비주얼 웹 파트의 토큰 제한 사항
 샌드박스 솔루션의 비주얼 웹 파트는 SharePoint 런타임이 지원하는 $SPUrl과 같은 표준 토큰을 처리할 수 없습니다. 이에 따라 URL은 확인되지 않으며, 다음 예제와 같이 스크립트 요소에서 URL을 직접 참조하는 경우 비주얼 웹 파트 디자이너의 디자인 뷰에서 내용을 미리 볼 수 없습니다.

```xml
<script src="<% $SPUrl:~site/SiteAssets/ListOperations.js %>"></script>
```

 이 제한 사항을 해결하고 토큰을 확인하려면 리터럴을 사용하여 URL을 참조하십시오.

```xml
<asp:literal ID="Literal1" runat="server" Text="<script src='" />
<asp:literal ID="Literal2" runat="server" Text="<% $SPUrl:~site/SiteAssets/ListOperations.js %>" />
<asp:literal ID="Literal3" runat="server" Text="' type='text/javascript' ></script>" />
```

## <a name="character-restrictions-in-names-of-projects-and-project-items"></a>프로젝트 및 프로젝트 항목 이름의 문자 제한
 프로젝트와 프로젝트 항목의 이름에는 SharePoint 2010의 배포 경로에서 유효한 문자만 포함될 수 있습니다. 다른 문자는 허용 되지 않습니다.

### <a name="error-message"></a>오류 메시지
 "잘못 된 문자" 오류 메시지입니다.

### <a name="resolution"></a>해결 방법
 SharePoint 프로젝트 및 프로젝트 항목 이름의 경우 다음 문자만 사용합니다.

- 영숫자 ASCII 문자

- Space

- 마침표 (.)

- 쉼표(,)

- 밑줄 (_)

- 대시 (-)

- 백슬래시(\\)

  프로젝트가 패키지될 때 유효성 검사 규칙은 배포 중인 각 파일의 배포 경로 속성에 이러한 유효한 문자만 포함되어 있는지 확인합니다.

## <a name="errors-when-creating-custom-fields"></a>사용자 지정 필드를 만들 때 발생 하는 오류
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 사용자 지정 필드는 XML로 정의됩니다. 필드가 정의되어 있지 않거나 특정 형식을 사용하여 참조되는 경우 오류가 발생할 수 있습니다.

### <a name="error-message"></a>오류 메시지
 패키징 시 "잘못 된 문자" 오류 메시지입니다.

### <a name="resolution"></a>해결 방법
 필드 정의의 ID는 다음 예제와 같이 중괄호로 묶은 GUID여야 합니다.

```xml
<Field ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Type="Note"
    Name="PatientName"
    DisplayName="Patient Name"
    Group="A Custom Group">
</Field>.
```

 다음 예제에서 볼 수 있듯이, 콘텐츠 형식의 필드 참조는 \<FieldRef /> 시작/끝 요소 ()를 사용 하지 않고 빈 요소 형식 ()을 사용 하 여 정의 해야 합니다 \<FieldRef> \</FieldRef> .

```xml
<FieldRef ID="{5744d18c-305e-4632-8bd1-09d134f4830d}"
    Name="PatientName"
    DisplayName="Patient Name"
    Required="TRUE"/>
```

 필드의 소스 XML에 잘못된 형식이나 유효하지 않은 XML 파일과 같은 문제가 있는 경우 "파일을 구문 분석할 수 없음" 오류가 발생합니다.

## <a name="new-non-english-site-definitions-do-not-appear-in-site-creation-page-after-deployment"></a>배포 후 영어가 아닌 새 사이트 정의가 사이트 생성 페이지에 나타나지 않음
 영어가 아닌 버전의 (즉, 1033 이외의 로캘이 있는 버전)를 사용 하 여 사이트 정의를 만들고 배포한 후에는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] **sharepoint 사용자 지정** 탭이 **템플릿 선택** 상자에 나타나지 않고 새 사이트 템플릿이 **새 SharePoint 사이트** 페이지에 나타나지 않습니다.

### <a name="error-message"></a>오류 메시지
 없음

### <a name="resolution"></a>해결 방법
 이 문제는 *webtemp_SiteDefinitionProject1.xml*webtemp 사이트 정의 구성 파일의 **Path** 속성에 잘못 된 값이 있기 때문에 발생 합니다. **배포 위치**아래에 있는 webtemp 파일의 **Path** 속성에서 1033을 적절 한 로캘로 변경 합니다 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . 예를 들어, 일본어 로캘을 사용 하려면 값을 1041로 변경 합니다. 자세한 내용은 참조 [Microsoft에 의해 할당되는 로캘 ID](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c)를 참조하세요.

## <a name="error-appears-when-a-workflow-project-is-deployed-on-a-clean-system"></a>정상적인 시스템에 워크플로 프로젝트를 배포 하면 오류가 표시 됩니다.
 이 문제는 클린 시스템의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 워크플로 프로젝트를 배포하는 경우 발생합니다. 클린 시스템은 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 및 SharePoint를 새로 설치했지만 워크플로 프로젝트를 배포하지 않은 컴퓨터입니다.

### <a name="error-message"></a>오류 메시지
 SharePoint 목록을 찾을 수 없습니다. 워크플로 기록.

### <a name="resolution"></a>해결 방법
 이 오류는 워크플로 기록 목록 누락으로 인해 발생 합니다. 개발 환경은 깨끗 한 시스템 이므로 워크플로가 배포 되지 않으며 워크플로 기록 목록이 아직 존재 하지 않습니다. 이 문제를 해결 하려면 워크플로 마법사를 다시 엽니다. 이렇게 하면 워크플로 기록 목록이 생성 됩니다.

##### <a name="to-reenter-the-workflow-wizard"></a>워크플로 마법사를 다시 입력 하려면

1. **솔루션 탐색기**에서 워크플로 노드를 선택 합니다.

2. **속성** 창에서 줄임표 단추가 있는 모든 속성의 줄임표 (...) 단추를 선택 합니다.

## <a name="user-must-refresh-application-page-in-browser-while-debugging-to-view-updated-image"></a>업데이트 된 이미지를 보려면 디버그 하는 동안 브라우저에서 응용 프로그램 페이지를 새로 고쳐야 함
 이미지 컨트롤과 같은 이미지를 표시 하는 컨트롤을 사용 하 여 응용 프로그램 페이지를 포함 하는 SharePoint 솔루션을 디버깅 하는 경우에는 [!INCLUDE[TLA2#tla_html](../sharepoint/includes/tla2sharptla-html-md.md)] 브라우저에서 페이지를 새로 고쳐 이미지에 적용 된 변경 내용을 표시 해야 합니다.

## <a name="error-the-site-location-is-not-valid"></a>오류: 사이트 위치가 잘못 되었습니다.
 가 설치 되지 않은 경우이 문제가 발생할 수 있습니다 [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] . **Sharepoint 사용자 지정 마법사**에 지정 된 sharepoint 웹 사이트에 대 한 관리자 액세스 권한이 없는 경우에도 발생할 수 있습니다.

### <a name="error-message"></a>오류 메시지

- SharePoint 사이트 위치가 잘못 되었습니다.

### <a name="resolution"></a>해결 방법

- [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]설치

- SharePoint 웹 사이트에 대 한 관리자 액세스 권한이 있는지 확인 합니다. 자세한 내용은 [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] 온라인 문서 [SharePoint Server에서 서비스 응용 프로그램의 관리자 할당 또는 제거](/sharepoint/administration/assign-or-remove-administrators-of-service-applications)를 참조 하세요.

## <a name="site-deletion-web-event-does-not-occur-in-event-receiver-project"></a>사이트 삭제 웹 이벤트가 이벤트 수신기 프로젝트에서 발생 하지 않음
 이벤트 수신기 프로젝트를 만들 때 "사이트를 삭제 하 고 있습니다."와 같은 특정 웹 이벤트를 선택 하면 이벤트가 발생 하지 않습니다.

### <a name="error-message"></a>오류 메시지
 없음

### <a name="resolution"></a>해결 방법
 이 문제는 사이트 수준 이벤트를 처리 하기 위해 기능 범위가 "사이트" 여야 하지만 이벤트 수신기 프로젝트의 기본 기능 범위는 "Web" 이기 때문에 발생 합니다. 영향을 받는 웹 이벤트는 다음과 같습니다.

- 사이트를 삭제 하는 중 (WebDeleting)

- 사이트가 삭제 됨 (WebDeleted)

- 사이트를 이동 하는 중 (WebMoving)

- 사이트가 이동 됨 (웹 이동)

  문제를 해결 하려면 다음과 같이 이벤트 수신기의 기능 범위를 변경 합니다.

##### <a name="to-change-the-feature-scope-of-the-event-receiver"></a>이벤트 수신기의 기능 범위를 변경 하려면

1. **솔루션 탐색기**에서 파일을 두 번 클릭 하거나 바로 가기 메뉴를 연 다음 **열기**를 선택 하 여 **기능 디자이너** 에서 이벤트 수신기의 *기능* 파일을 엽니다.

2. **범위**옆의 화살표를 선택 하 고 표시 되는 목록에서 **사이트** 를 선택 합니다.

## <a name="deployment-error-appears-after-the-name-of-an-identifier-in-a-business-data-connectivity-model-project-is-changed"></a>비즈니스 데이터 연결 모델 프로젝트의 식별자 이름이 변경 된 후 배포 오류가 표시 됩니다.
 이 문제는 BDC (비즈니스 데이터 연결) 모델에서 엔터티의 식별자 이름을 변경한 후 솔루션을 배포 하려고 할 때 발생 합니다.

### <a name="error-messages"></a>오류 메시지

- \<*model name*> 다음 외부 콘텐츠 형식 활성화 오류가 있습니다.

- 이름이 ' ' 인 IMetadataObject의 \<*model name*> ' name ' 필드에 중복 된 값이 있습니다.

### <a name="resolution"></a>해결 방법
 이 문제를 해결 하려면 모델을 수동으로 삭제 한 다음 솔루션을 다시 배포 하십시오.  다음 도구 중 하나를 사용 하 여 모델을 삭제할 수 있습니다.

- SharePoint 2010 중앙 관리 자세한 내용은 Microsoft TechNet 웹 사이트의 [BDC 모델 관리](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)#delete-a-bdc-model) 를 참조 하십시오.

- Windows PowerShell. 명령 프롬프트에서 다음 명령을 입력 하 여 모델을 삭제할 수 있습니다. **SPBusinessDataCatalogModel**. 자세한 내용은 Microsoft TechNet 웹 사이트의 [일반 cmdlet (SharePoint Server 2010)](/powershell/module/sharepoint-server) 을 참조 하십시오.

## <a name="an-error-appears-when-you-try-to-view-a-visual-web-part-in-sharepoint"></a>SharePoint에서 비주얼 웹 파트를 보려고 하면 오류가 표시 됩니다.
 이 문제는 사용자 정의 컨트롤의 **Path** 속성이 "controltemplates" 문자열로 시작 하지 않는 경우에 발생 합니다 \\ .

### <a name="error-messages"></a>오류 메시지

- 파일 '/_CONTROLTEMPLATES/ *\<project name>* / *\<Web Part name>* / *\<user control name>* .ascx '가 없습니다.

- '/' 애플리케이션의 서버 오류.

### <a name="resolution"></a>해결 방법

##### <a name="to-resolve-this-issue"></a>이 문제를 해결하려면

1. **솔루션 탐색기**에서 파일 이름 확장명이 *.ascx*인 사용자 정의 컨트롤 파일을 선택 합니다.

2. 메뉴 모음에서 **보기**  >  **속성 창**을 선택 합니다.

3. **속성** 창에서 **배포 위치** 노드를 확장 합니다.

4. **Path** 속성의 값이 "controltemplates" 문자열로 시작 하는지 확인 \\ 합니다.

## <a name="error-appears-when-an-imported-reusable-workflow-that-contains-a-task-form-field-is-run"></a>작업 폼 필드를 포함 하는 가져온 재사용 가능한 워크플로를 실행 하면 오류가 표시 됩니다.
 이 문제는 필드가 있는 작업 양식이 포함 된 워크플로를 가져온 다음 가져온 동일한 시스템에서 새 워크플로를 실행 하는 경우에 발생 합니다.

### <a name="error-message"></a>오류 메시지
 배포 단계 ' 기능 활성화 '에서 오류가 발생 했습니다. [*guid*] 기능에 정의 된 Id가 [*guid*] 인 필드가 현재 사이트 모음 또는 하위 사이트에 있습니다.

### <a name="resolution"></a>해결 방법
 이 오류는에서 다시 사용할 수 있는 워크플로 가져오기 프로젝트가 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 작업 폼 필드 id를 변경 하지 않기 때문에 발생 하는 필드 id 충돌의 결과입니다. 가져온 워크플로를 원래 워크플로를 포함 하는 동일한 서버에 배포 하는 경우 필드 ID 충돌이 발생 합니다.

 이 문제를 해결 하려면 찾기 및 바꾸기 기능을 사용 하 여 가져온 모든 워크플로 파일에서 필드 ID 특성의 값을 변경 합니다.

## <a name="error-appears-when-a-renamed-imported-list-instance-is-run"></a>이름이 바뀐 가져온 목록 인스턴스가 실행 되 면 오류가 나타납니다.
 이 문제는 가져온 목록 인스턴스의 이름을 바꾼 다음에서 실행 하는 경우에 발생 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다.

### <a name="error-message"></a>오류 메시지
 빌드 오류: 배포 단계 ' 기능 활성화 '에서 오류가 발생 했습니다. 파일 템플릿 \ 기능 \\ [*프로젝트*<em>기능</em>*이름*가져오기] \Files\Lists \\ [*이전*<em>목록 이름</em>] \Schema.xml 존재 하지 않습니다.

### <a name="resolution"></a>해결 방법
 목록 인스턴스를 가져올 때 CustomSchema 라는 특성이 목록 인스턴스의 Elements.xml 파일에 추가 됩니다. Elements.xml 목록 인스턴스에 대 한 사용자 지정 schema.xml의 경로를 포함 합니다. 에서 목록 인스턴스의 이름을 바꾸면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 사용자 지정 schema.xml의 배포 경로가 변경 되지만 CustomSchema 특성의 경로 값은 업데이트 되지 않습니다. 따라서 목록 인스턴스는 기능이 활성화 될 때 CustomSchema 특성으로 지정 된 이전 경로에서 *schema.xml* 파일을 찾을 수 없습니다.

 이 문제를 해결 하려면 CustomSchema 특성에서 *schema.xml* 파일의 배포 위치 경로를 업데이트 합니다.

## <a name="sharepoint-debugging-session-terminated-by-iis"></a>IIS에서 종료 한 SharePoint 디버깅 세션
 이 문제는 SharePoint 솔루션에서 중단점을 설정 하 고 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **F5** 키를 선택 하 여 실행 한 다음 90 초 보다 긴 중단점에 유지 되는 경우에 발생 합니다.

### <a name="error-message"></a>오류 메시지
 디버깅 중인 웹 서버 프로세스가 인터넷 정보 서비스 (IIS)에 의해 종료 되었습니다. IIS에서 애플리케이션 풀 ping 설정을 구성하여 이 문제를 방지할 수 있습니다. 자세한 내용은 도움말을 참조 하십시오.

### <a name="resolution"></a>해결 방법
 기본적으로 IIS 응용 프로그램 풀은 응용 프로그램을 닫기 전에 응용 프로그램이 응답 하는 데 90 초 동안 대기 합니다. 이 프로세스를 응용 프로그램의 "ping" 이라고 합니다. 이 문제를 해결 하려면 대기 시간을 늘리거나 응용 프로그램 ping을 완전히 사용 하지 않도록 설정할 수 있습니다.

##### <a name="to-access-the-iis-app-pool-settings"></a>IIS 응용 프로그램 풀 설정에 액세스 하려면

1. IIS 관리자를 엽니다.

2. **연결** 창에서 SharePoint 서버 노드를 확장 한 다음 **응용 프로그램 풀** 노드를 선택 합니다.

3. **응용 프로그램 풀** 페이지에서 SharePoint 응용 프로그램 풀 (일반적으로 "sharepoint-80")을 선택한 다음 **동작** 창에서 **고급 설정** 링크를 선택 합니다.

4. IIS 제한 시간 전에 대기 시간을 늘리려면 **Ping 최대 응답 시간 (초)** 값을 90 초 보다 큰 값으로 변경 합니다.

5. IIS ping을 사용 하지 않도록 설정 하려면 **Ping 사용** 을 **False**로 설정 합니다.

## <a name="auto-retract-leaves-orphaned-list-instance-in-sharepoint"></a>자동 취소는 분리 된 목록 인스턴스를 SharePoint에 남겨 둡니다.
 이 문제는 다음 단계를 수행 하는 경우 발생 합니다.

1. 에 목록 인스턴스가 있는 목록 정의를 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. **F5** 키를 선택 하 여 솔루션을 실행 합니다.

3. 디버깅을 중지 하거나 SharePoint 사이트를 닫습니다.

4. SharePoint 사이트를 다시 열고 목록 인스턴스를 엽니다.

### <a name="error-message"></a>오류 메시지
 '/' 애플리케이션의 서버 오류.

### <a name="resolution"></a>해결 방법
 이는 SharePoint 솔루션의 디버그 세션을 닫은 후 자동 취소 기능이 솔루션을 취소 하기 때문에 발생 합니다. 취소는 SharePoint에서 목록 정의를 삭제 하지만 목록의 인스턴스를 삭제 하지는 않습니다. 기본 목록 정의는 목록 인스턴스에 필요 합니다.

 이 문제를 해결 하려면 메뉴 모음에서 **빌드**배포를 선택 하 여 솔루션을 배포  >  **Deploy**합니다. **F5** 키를 선택 하 여 솔루션을 디버깅 하지 마십시오. 그런 다음 SharePoint에서 목록 인스턴스를 삭제 합니다.

## <a name="original-sharepoint-solution-is-replaced-by-an-exported-version"></a>원래 SharePoint 솔루션은 내보낸 버전으로 대체 됩니다.
 SharePoint 솔루션을 내보내는 경우 솔루션을로 가져온 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 후 솔루션을 내보낸 사이트와 동일한 사이트에 다시 배포 하면 원래 SharePoint 솔루션이 대체 됩니다. 원본 솔루션이 활성화 되지 않은 서버에 솔루션을 배포 하는 경우에는이 문제가 발생 하지 않습니다.

### <a name="error-message"></a>오류 메시지
 없음

### <a name="resolution"></a>해결 방법
 내보낸 사이트의 솔루션을 덮어쓰지 않으려면 프로젝트에서 가져온 모든 기능의 솔루션에 대 한 Id와 기능 Id의 Guid를 변경 합니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

## <a name="error-appears-when-debugging-starts"></a>디버깅을 시작할 때 오류가 표시 됩니다.
 Visual Studio에서 SharePoint 솔루션의 디버깅을 시작할 때 지정한 키가 사전에 없기 때문에 Visual Studio에서 Web.config 파일을 로드할 수 없다는 오류가 발생합니다.

### <a name="error-message"></a>오류 메시지
 Web.config 구성 파일을 로드할 수 없습니다. 파일에 잘못 된 형식의 XML 요소가 있는지 확인 한 후 다시 시도 하십시오. 다음 오류가 발생 했습니다. 지정 된 키가 사전에 없습니다.

### <a name="resolution"></a>해결 방법
 이 문제를 해결하려면 Visual Studio에서 SharePoint 프로젝트의 사이트 URL 속성 값이 웹 애플리케이션의 대체 액세스 매핑에 대한 기본 영역에 할당된 URL과 일치하는지 확인합니다. 인트라넷 등의 다른 영역을 URL에 사용하여 오류를 해결할 수 없습니다. 프로젝트의 사이트 URL과 기본 영역의 URL은 일치해야 합니다. 대체 액세스 매핑에 액세스 하려면 SharePoint 2010 중앙 관리 유틸리티를 열고 **응용 프로그램 관리** 링크를 선택한 다음 **웹 응용 프로그램**에서 **대체 액세스 매핑 구성** 링크를 선택 합니다. 자세한 내용은 [웹 응용 프로그램에 대 한 영역 만들기](/previous-versions/office/sharepoint-2007-products-and-technologies/cc263087(v=office.12))를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [SharePoint 패키징 및 배포 문제 해결](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Visual Studio의 디버깅](../debugger/debugger-feature-tour.md)
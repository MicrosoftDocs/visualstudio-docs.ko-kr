---
title: SharePoint 솔루션 지역화 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0a7b04ab1f77eba15f2bc617f89514a8d0952674
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017141"
---
# <a name="localize-sharepoint-solutions"></a>SharePoint 솔루션 지역화

  전 세계에서 사용할 수 있도록 응용 프로그램을 준비 하는 프로세스를 지역화 라고 합니다. 지역화는 리소스를 특정 문화권으로 변환 합니다. 자세한 내용은 [응용 프로그램 전역화 및 지역화](../ide/globalizing-and-localizing-applications.md)를 참조 하세요. 이 항목에서는 SharePoint 솔루션을 지역화 하는 방법에 대 한 개요를 제공 합니다.

 솔루션을 지역화 하려면 하드 코드 된 문자열을 코드에서 제거 하 고 리소스 파일로 추상화 합니다. 리소스 파일은 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 확장명이 *.resx* 인 기반 파일입니다. 리소스 파일에는 솔루션에 사용 되는 문자열의 번역 된 버전이 포함 되어 있습니다. 자세한 내용은 [응용 프로그램의 리소스](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100))를 참조 하세요.

> [!NOTE]
> SharePoint 솔루션 리소스 파일에는 문자열 리소스만 추가 합니다. 리소스 편집기를 사용 하면 문자열이 아닌 리소스를 추가할 수 있지만 문자열이 아닌 리소스는 SharePoint에 배포 되지 않습니다.

## <a name="resource-files"></a>리소스 파일
 리소스 파일에는 기본, 언어 중립적인 및 언어별의 세 종류가 있습니다.

|리소스 파일 형식|Description|
|------------------------|-----------------|
|기본값|대체 (fallback) 리소스 라고도 하는 기본 리소스 파일에는 영어와 같은 기본 문화권에 대해 지역화 된 문자열이 포함 됩니다. 지정 된 언어에 대 한 지역화 된 리소스 파일을 찾을 수 없는 경우 사용 됩니다. 기본 리소스에는 별도의 파일이 없으며 주 응용 프로그램 어셈블리에 저장 됩니다.|
|언어 중립적|특정 문화권이 아닌 특정 언어에 대해 지역화 된 문자열을 포함 하는 리소스 파일입니다. 예를 들어 프랑스어의 경우 "fr"입니다.|
|언어별|언어와 문화권에 대해 지역화 된 문자열을 포함 하는 리소스 파일입니다. 예를 들어 프랑스어 (캐나다)의 경우 "fr-CA"입니다.|

 자세한 내용은 [지역화를 위한 리소스의 계층적 구성](../ide/globalizing-and-localizing-applications.md)을 참조 하세요.

 에서 개발 하는 SharePoint 프로젝트의 기본 리소스 파일을 지정 하려면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 리소스 파일을 추가할 때 **리소스 추가** 대화 상자의 문화권 목록에서 **고정 언어 (고정 국가)** 를 선택 합니다.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Visual Studio SharePoint 솔루션 지역화
 솔루션을 지역화할 때 솔루션이 사용자에 게 표시 하는 모든 텍스트 정보를 고려해 야 합니다. 정보 메시지, 오류 메시지 및 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 문자열을 변환 하 고 해당 번역을 리소스 파일에 배치 해야 합니다.

 리소스 파일의 모든 문자열에는 고유 식별자가 있습니다. 각 리소스 파일에서 번역 된 문자열에 동일한 식별자를 사용 합니다. 예를 들어, "String1"이 기본 리소스 파일의 첫 번째 문자열에 대 한 식별자 인 경우 언어별 리소스 파일의 첫 번째 문자열에 동일한 식별자를 사용 합니다.

 SharePoint 응용 프로그램에서 일반적으로 지역화 하는 세 가지 영역은 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 기능, ASPX 페이지 태그 및 코드입니다. 예시를 위해 다음 섹션에서는 독일어 및 일본어로 지역화 하려는 SharePoint 솔루션이 있다고 가정 합니다. 기본 언어는 한국어(Korean)입니다.

### <a name="localize-features"></a>기능 지역화
 기능을 지역화 하려면 기능에 대 한 하드 코드 된 제목 및 설명을 지역화 된 리소스 파일의 번역 된 제목 및 문자열을 참조 하는 식으로 바꾸어야 합니다. 의 **기능 디자이너** 에서이 변경을 수행 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 합니다. 자세한 내용은 [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)를 참조 하세요.

 영어 기능을 독일어 및 일본어로 지역화 하려면 영어, 독일어 및 일본어의 세 가지 리소스 파일 프로젝트 항목을 프로젝트에 추가 합니다. 기능 리소스 파일은 ASPX 태그 또는 코드를 지역화 하는 데 사용할 수 없습니다. 별도의 리소스 파일이 필요 합니다.

 기능 리소스 파일을 만든 후 번역 된 문자열을 추가 합니다. 다음 형식의 식을 사용 하 여 지역화 된 문자열에 액세스 합니다.

```aspx-csharp
$Resources:String ID
```

 의 기능 리소스 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 는 항상 리소스 라고 합니다. 고정 언어 이외의 언어를 선택 하면 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 리소스 파일 이름에 문화권이 추가 됩니다. 예를 들어 고정 언어 (기본값) 기능 리소스 파일을 추가 하는 경우이를 *리소스 .resx*라고 합니다. 일본어 (일본) 문화권을 선택 하 여 언어별 기능 리소스를 추가 하는 경우 파일은 *Resources. ja-jp*. 기능 리소스 파일 이름은 자동으로 할당 되며 변경할 수 없습니다.

 기능 리소스의 범위는 추가 된 기능에 대 한 로컬입니다. 솔루션의 모든 기능 또는 요소 파일에서 사용할 수 있는 리소스를 만들려면 기능 리소스 파일 대신 **전역 리소스 파일** 프로젝트 항목을 추가 합니다. **전역 리소스 파일** 프로젝트 항목은 **새 항목 추가** 대화 상자의 **SharePoint** 아래 **2010** 폴더에 있습니다. 전역 리소스 파일은 SharePoint 루트 폴더의 \Resources 폴더에 배포 됩니다.

### <a name="localize-aspx-page-markup"></a>ASPX 페이지 태그 지역화
 페이지를 지역화 하려면 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 영어, 독일어 및 일본어의 세 가지 리소스 파일 프로젝트 항목을 프로젝트에 추가 합니다. 태그 외에 코드를 지역화할 필요가 없는 경우에는 대신 전역 리소스 파일을 추가할 수 있습니다.

 기본 언어 리소스 파일의 이름을 제공 합니다. 지역화 된 리소스 파일에 언어별 문화권과 추가 된 동일한 이름을 지정 합니다 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . 예를 들어 독일어의 경우 *MyAppResources.de* 이 고 일본어의 경우 *MyAppResources입니다.*

 각 리소스 파일의 **배포 유형** 속성을 **appglobalresource**로 설정 합니다. 이렇게 하면 리소스 파일이 App_GlobalResources 폴더에 배포 되므로 솔루션의 모든 ASPX 페이지 및 컨트롤에서 해당 파일을 사용할 수 있습니다. App_GlobalResources 폴더는 C:\inetpub\wwwroot\wss\VirtualDirectories \\<포트 번호 \> \ App_GlobalResources에 있습니다.

> [!NOTE]
> 비전역 리소스 파일을 사용 하는 경우 프로젝트 항목 폴더로 이동 하 여 배포 유형 속성과 기타 SharePoint 관련 속성을 사용 하도록 설정 합니다.

 ASPX 태그 리소스 파일을 사용 하 여 코드를 지역화할 수도 있습니다. 리소스를 사용 하 여 ASPX 태그 외에도 코드를 지역화 하는 경우 각 파일의 빌드 작업 속성을 포함 리소스로 설정 하 여 리소스를 위성 어셈블리로 컴파일해야 합니다. 그러나 리소스 파일만 사용 하 여 태그를 지역화 하는 경우에는 필요에 따라 빌드 작업을 내용으로 변경 하 여 파일이 주 응용 프로그램 어셈블리로 컴파일되지 않도록 할 수 있습니다.

 ASPX 페이지의 하드 코드 된 모든 속성 문자열을 다음 형식의 식으로 컨트롤 태그를 바꿉니다.

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 예:

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 텍스트인 ASPX의 경우 다음 형식의 식을 사용 합니다.

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 예:

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 자세한 내용은 [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)를 참조 하세요.

### <a name="localize-code"></a>코드 지역화
 기능 문자열과 태그를 지역화 하는 것 외에 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 도 솔루션 코드에 표시 되는 메시지 문자열 및 오류 문자열을 지역화 해야 합니다. 지역화 된 정보 및 오류 메시지는 위성 어셈블리에 포함 됩니다. 위성 어셈블리에는 [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 텍스트 및 예외와 같은 출력 메시지와 같이 사용자에 게 표시 되는 문자열이 포함 됩니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]표준 .NET Framework 허브 및 스포크 모델을 사용 합니다. 허브 또는 주 프로그램 어셈블리는 기본 언어 리소스를 포함 합니다. 스포크 또는 위성 어셈블리에는 언어별 리소스가 포함 되어 있습니다. 자세한 내용은 [리소스 패키지 및 배포](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100))를 참조하세요. 위성 어셈블리는 리소스 (*.resx*) 파일에서 컴파일됩니다. 프로젝트 및 솔루션 패키지에 언어별 리소스 파일을 추가 하면에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 리소스 파일을 *{project Name} .resources.dll*라는 위성 어셈블리로 컴파일합니다.

 ASPX 태그와 마찬가지로 프로젝트에 별도의 리소스 파일 프로젝트 항목을 추가 하 여 SharePoint 응용 프로그램 코드를 지역화 합니다. 기본 언어 및 지역화 된 각 언어에 대 한 하나입니다. 그러나 앞에서 설명한 것 처럼 ASPX 태그를 지역화 하기 위한 리소스 파일이 이미 있는 경우 코드를 지역화 하는 데 사용할 수 있습니다. 리소스 파일을 만들어야 하는 경우에는 기본 언어 리소스 파일에 *.resx* 확장명을 사용 하 여 추가한 이름을 지정 합니다. 지역화 된 리소스 파일의 이름을 언어별 문화권과 함께 추가 합니다 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . 각 리소스 파일의 빌드 작업 속성을 포함 리소스로 설정 하 여 위성 리소스 어셈블리를 만들 수 있도록 합니다.

 위성 어셈블리를 만들려면 프로젝트를 빌드한 다음 **패키지 디자이너**의 **고급** 탭을 통해 파일을 추가 어셈블리로 추가 합니다. 어셈블리를 추가할 때 de-de [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] * \\ {Project Item Name} .resources.dll*와 같은 위치 경로에 문화권 폴더를 추가 합니다. 이를 통해 패키지는 이름이 같은 파일을 포함할 수 있습니다.

 코드에서 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 다음 구문을 사용 하 여 하드 코드 된 문자열을 메서드에 대 한 호출로 바꿉니다.

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 자세한 내용은 [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)를 참조 하세요.

#### <a name="web-part-code-localization"></a>웹 파트 코드 지역화
 웹 파트에는 WebDisplayName, Category, Webdisplayname 등 하드 코드 된 문자열을 사용 하는 코드 특성을 포함 하는 사용자 지정 속성 편집기 기능이 포함 되어 있습니다. 이러한 특성에 대 한 문자열 값을 바꾸려면 특성의 클래스에서 파생 되는 별도의 클래스를 만듭니다. 이러한 클래스에서 특성의 속성을 설정 합니다. 특성 속성은 기본 클래스에 종속 됩니다. 예를 들어 WebDisplayName 특성 속성은 DisplayNameValue이 고 Webdisplayname 특성 속성은 description Value입니다.

 파생 클래스에서 리소스 파일 및 ResourceManager 개체의 문자열 ID를 참조 하 여 문자열 ID의 지역화 된 값을 가져옵니다. 이 값을 속성 편집기 특성에 반환 합니다.

## <a name="see-also"></a>참고 항목
- [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)
- [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)
- [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)
- [방법: 리소스 파일 추가](../sharepoint/how-to-add-a-resource-file.md)
- [방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한 지정](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)

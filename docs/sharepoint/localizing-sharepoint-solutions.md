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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017141"
---
# <a name="localize-sharepoint-solutions"></a>SharePoint 솔루션 지역화

  전 세계에서 사용할 수 있도록 애플리케이션을 준비하는 프로세스를 지역화라고 합니다. 지역화는 리소스를 특정 문화권으로 번역합니다. 자세한 내용은 [애플리케이션 전역화 및 지역화](../ide/globalizing-and-localizing-applications.md)를 참조하세요. 이 항목에서는 SharePoint 솔루션을 지역화하는 방법을 개괄적으로 설명합니다.

 솔루션을 지역화하려면 하드 코드된 문자열을 코드에서 제거하고 리소스 파일로 추상화합니다. 리소스 파일은 *.resx* 확장명을 사용하는 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 기반 파일입니다. 리소스 파일에는 솔루션에서 사용되는 문자열의 번역된 버전이 포함되어 있습니다. 자세한 내용은 [애플리케이션의 리소스](/previous-versions/dotnet/netframework-4.0/f45fce5x(v=vs.100))를 참조하세요.

> [!NOTE]
> SharePoint 솔루션 리소스 파일에는 문자열 리소스만 추가합니다. 리소스 편집기를 사용하면 문자열이 아닌 리소스를 추가할 수 있지만, 문자열이 아닌 리소스는 SharePoint에 배포되지 않습니다.

## <a name="resource-files"></a>리소스 파일
 리소스 파일에는 기본, 언어 중립적, 언어별의 세 가지 종류가 있습니다.

|리소스 파일 형식|설명|
|------------------------|-----------------|
|기본값|대체 리소스라고도 하는 기본 리소스 파일에는 영어와 같은 기본 문화권으로 지역화된 문자열이 포함되어 있습니다. 지정한 언어로 지역화된 리소스 파일을 찾을 수 없는 경우에 사용됩니다. 기본 리소스에는 별도의 파일이 없으며, 주 애플리케이션 어셈블리에 저장됩니다.|
|언어 중립적|특정 문화권이 아닌 언어로 지역화된 문자열을 포함하는 리소스 파일입니다. 예를 들어 프랑스어의 경우 “fr”입니다.|
|언어별|언어와 문화권으로 지역화된 문자열을 포함하는 리소스 파일입니다. 예를 들어 프랑스어(캐나다)의 경우 “fr-CA”입니다.|

 자세한 내용은 [지역화를 위한 리소스의 계층적 구성](../ide/globalizing-and-localizing-applications.md)을 참조하세요.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 개발하는 SharePoint 프로젝트의 기본 리소스 파일을 지정하려면 리소스 파일을 추가할 때 **리소스 추가** 대화 상자의 문화권 목록에서 **고정 언어(고정 국가)** 를 선택합니다.

## <a name="localize-visual-studio-sharepoint-solutions"></a>Visual Studio SharePoint 솔루션 지역화
 솔루션을 지역화하는 경우 솔루션에서 사용자에게 표시하는 모든 텍스트 정보를 고려해야 합니다. 정보 메시지, 오류 메시지, [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 문자열을 번역하고 해당 번역을 리소스 파일에 저장해야 합니다.

 리소스 파일의 모든 문자열에는 고유 식별자가 있습니다. 각 리소스 파일의 번역된 문자열에 동일한 식별자를 사용합니다. 예를 들어 “String1”이 기본 리소스 파일에 있는 첫 번째 문자열의 식별자인 경우 언어별 리소스 파일의 첫 번째 문자열에 동일한 식별자를 사용합니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 애플리케이션에서 일반적으로 지역화하는 세 가지 영역은 기능, ASPX 페이지 태그, 코드입니다. 예시를 위해 다음 섹션에서는 독일어와 일본어로 지역화하려는 SharePoint 솔루션이 있다고 가정합니다. 기본 언어는 한국어(Korean)입니다.

### <a name="localize-features"></a>기능 지역화
 기능을 지역화하려면 하드 코드된 기능 제목 및 설명 대신 지역화된 리소스 파일의 번역된 제목 및 문자열을 참조하는 식을 사용해야 합니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]의 **기능 디자이너**에서 이 변경 작업을 수행합니다. 자세한 내용은 [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)를 참조하세요.

 영어 기능을 독일어와 일본어로 지역화하려면 영어, 독일어, 일본어의 세 가지 리소스 파일 프로젝트 항목을 프로젝트에 추가합니다. 기능 리소스 파일은 ASPX 태그 또는 코드를 지역화하는 데 사용할 수 없습니다. 별도의 리소스 파일이 필요합니다.

 기능 리소스 파일을 만든 후 번역된 문자열을 추가합니다. 다음 형식의 식을 사용하여 지역화된 문자열에 액세스합니다.

```aspx-csharp
$Resources:String ID
```

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]의 기능 리소스 이름은 항상 Resources로 지정됩니다. 고정 언어가 아닌 다른 언어를 선택하면 문화권 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]가 리소스 파일 이름에 추가됩니다. 예를 들어 고정 언어(기본) 기능 리소스 파일을 추가하는 경우 파일 이름은 *Resources.resx*가 됩니다. 일본어(일본) 문화권을 선택하여 언어별 기능 리소스를 추가하는 경우 파일 이름은 *Resources.ja-JP.resx*가 됩니다. 기능 리소스 파일 이름은 자동으로 할당되며, 변경할 수 없습니다.

 기능 리소스의 범위는 리소스가 추가된 기능의 로컬 범위입니다. 솔루션의 모든 기능 또는 요소 파일에서 사용할 수 있는 리소스를 만들려면 기능 리소스 파일 대신 **전역 리소스 파일** 프로젝트 항목을 추가합니다. **전역 리소스 파일** 프로젝트 항목은 **새 항목 추가** 대화 상자에서 **SharePoint** 아래의 **2010** 폴더에 있습니다. 전역 리소스 파일은 SharePoint 루트 폴더의 \Resources 폴더에 배포됩니다.

### <a name="localize-aspx-page-markup"></a>ASPX 페이지 태그 지역화
 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 페이지를 지역화하려면 영어, 독일어, 일본어의 세 가지 리소스 파일 프로젝트 항목을 프로젝트에 추가합니다. 태그 외에 코드를 지역화할 필요가 없는 경우 전역 리소스 파일을 대신 추가할 수 있습니다.

 기본 언어 리소스 파일의 이름을 지정합니다. 지역화된 리소스 파일에는 언어별 문화권 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]를 추가해서 동일한 이름을 지정합니다. 예를 들어 독일어의 경우 *MyAppResources.de-DE.resx*를 지정하고, 일본어의 경우 *MyAppResources.ja-JP.resx*를 지정합니다.

 각 리소스 파일의 **배포 유형** 속성을 **AppGlobalResource**로 설정합니다. 그러면 리소스 파일이 App_GlobalResources 폴더에 배포되어, 솔루션의 모든 ASPX 페이지와 컨트롤에서 해당 파일을 사용할 수 있습니다. App_GlobalResources 폴더는 C:\inetpub\wwwroot\wss\VirtualDirectories\\<port number\>\App_GlobalResources에 있습니다.

> [!NOTE]
> 비전역 리소스 파일을 사용하는 경우 배포 유형 속성과 기타 SharePoint 관련 속성을 사용하려면 프로젝트 항목 폴더로 이동합니다.

 ASPX 태그 리소스 파일을 사용하여 코드를 지역화할 수도 있습니다. 리소스를 사용하여 ASPX 태그 외에 코드도 지역화하는 경우 각 파일의 빌드 작업 속성 설정을 포함 리소스로 유지하여 리소스가 위성 어셈블리로 컴파일되도록 합니다. 그러나 리소스 파일을 사용하여 태그만 지역화하는 경우에는 필요에 따라 빌드 작업을 콘텐츠로 변경하여 파일이 주 애플리케이션 어셈블리로 컴파일되지 않도록 할 수 있습니다.

 ASPX 페이지 및 컨트롤 태그의 하드 코드된 모든 속성 문자열을 다음 형식의 식으로 바꿉니다.

```aspx-csharp
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 예를 들면 다음과 같습니다.

```aspx-csharp
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>
```

 텍스트인 ASPX의 경우 다음 형식의 식을 사용합니다.

```aspx-csharp
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />
```

 예를 들면 다음과 같습니다.

```aspx-csharp
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />
```

 자세한 내용은 [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)를 참조하세요.

### <a name="localize-code"></a>코드 지역화
 기능 문자열과 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] 태그 지역화뿐 아니라 솔루션 코드에 표시되는 메시지 문자열과 오류 문자열도 지역화해야 합니다. 지역화된 정보 및 오류 메시지는 위성 어셈블리에 포함됩니다. 위성 어셈블리는 예외 등의 출력 메시지, [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 텍스트와 같이 사용자에게 표시되는 문자열을 포함합니다.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서는 표준 .NET Framework 허브 및 스포크 모델을 사용합니다. 허브 또는 주 프로그램 어셈블리는 기본 언어 리소스를 포함합니다. 스포크 또는 위성 어셈블리는 언어별 리소스를 포함합니다. 자세한 내용은 [리소스 패키지 및 배포](/previous-versions/dotnet/netframework-4.0/sb6a8618(v=vs.100))를 참조하세요. 위성 어셈블리는 리소스( *.resx*) 파일에서 컴파일됩니다. 프로젝트 및 솔루션 패키지에 언어별 리소스 파일을 추가하면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 리소스 파일을 *{Project Name}.resources.dll*이라는 위성 어셈블리로 컴파일합니다.

 ASPX 태그와 마찬가지로 기본 언어와 지역화된 각 언어에 하나씩, 별도의 리소스 파일 프로젝트 항목을 프로젝트에 추가하여 SharePoint 애플리케이션 코드를 지역화합니다. 그러나 앞서 설명한 것처럼 ASPX 태그를 지역화하기 위한 리소스 파일이 이미 있는 경우에는 코드를 지역화하는 데 재사용할 수 있습니다. 리소스 파일을 만들어야 하는 경우, 선택한 이름에 *.resx* 확장명을 추가해서 기본 언어 리소스 파일에 지정합니다. 지역화된 리소스 파일에는 언어별 문화권 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]를 추가해서 동일한 이름을 지정합니다. 위성 리소스 어셈블리를 만들 수 있게 하려면 각 리소스 파일의 빌드 작업 속성을 포함 리소스로 설정합니다.

 위성 어셈블리를 만들려면 프로젝트를 빌드한 다음, **패키지 디자이너**의 **고급** 탭을 통해 파일을 다른 어셈블리로 추가합니다. 어셈블리를 추가하는 경우 *de-DE\\{Project Item Name}.resources.dll*과 같이 위치 경로 앞에 문화권 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] 폴더를 추가합니다. 그러면 패키지에 동일한 이름의 파일을 포함할 수 있습니다.

 코드에서 다음 구문을 사용하여 하드 코드된 문자열을 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 메서드 호출로 바꿉니다.

```aspx-csharp
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")
```

 자세한 내용은 [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)를 참조하세요.

#### <a name="web-part-code-localization"></a>웹 파트 코드 지역화
 웹 파트에는 WebDisplayName, Category, Webdisplayname 등의 하드 코드된 문자열을 사용하는 코드 특성을 포함하는 사용자 지정 속성 편집기 기능이 포함되어 있습니다. 이러한 특성의 문자열 값을 바꾸려면 특성 클래스에서 파생되는 별도의 클래스를 만듭니다. 해당 클래스에서 특성 속성을 설정합니다. 특성 속성은 기본 클래스에 따라 달라집니다. 예를 들어 WebDisplayName 특성 속성은 DisplayNameValue이고, WebDescription 특성 속성은 DescriptionValue입니다.

 파생 클래스에서 리소스 파일의 문자열 ID 및 ResourceManager 개체를 참조하여 문자열 ID의 지역화된 값을 가져옵니다. 이 값을 속성 편집기 특성에 반환합니다.

## <a name="see-also"></a>추가 정보
- [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)
- [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)
- [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)
- [방법: 리소스 파일 추가](../sharepoint/how-to-add-a-resource-file.md)
- [방법: 리소스 파일을 사용하여 지역화된 이름, 속성, 사용 권한 지정](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)

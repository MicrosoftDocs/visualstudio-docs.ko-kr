---
title: '방법: ASPX 태그 지역화 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 63bd8ee614a78752069002820689a2cc6c0be783
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016284"
---
# <a name="how-to-localize-aspx-markup"></a>방법: ASPX 태그 지역화
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)](.aspx) 페이지는 일반적으로 하드 코드 된 문자열 값을 사용 합니다. 이러한 문자열을 지역화 하려면 지역화 된 리소스를 참조 하는 식으로 대체 합니다.

## <a name="localize-aspx-markup"></a>ASPX 태그 지역화

#### <a name="to-localize-aspx-markup"></a>ASPX 태그를 지역화 하려면

1. 별도의 리소스 파일을 추가 합니다. 하나는 기본 언어이 고 다른 하나는 지역화 된 언어에 대 한 파일입니다.

     코드만이 아닌 태그를 지역화 하는 경우에는 전역 리소스 파일 프로젝트 항목을 추가 합니다. 코드와 태그를 지역화 하는 경우 리소스 파일 프로젝트 항목을 추가 합니다.

    1. 전역 리소스 파일을 추가 하려면 **솔루션 탐색기**에서 SharePoint 프로젝트 항목의 바로 가기 메뉴를 열고 **Add**  >  **새 항목**추가를 선택 합니다. SharePoint **2010** 노드에서 **전역 리소스 파일** 템플릿을 선택 합니다.

    2. 리소스 파일을 추가 하려면 **솔루션 탐색기**에서 SharePoint 프로젝트 항목의 바로 가기 메뉴를 열고 **Add**  >  **새 항목**추가를 선택 합니다. **Visual Basic** 또는 **Visual c #** 노드 아래에서 **리소스 파일** 템플릿을 선택 합니다.

    > [!NOTE]
    > 배포 유형 속성을 사용 하도록 설정 하려면 SharePoint 프로젝트 항목에 리소스 파일을 추가 해야 합니다. 이 속성은이 절차의 뒷부분에서 필요 합니다. 솔루션에 SharePoint 프로젝트 항목이 없으면 빈 SharePoint 프로젝트를 추가 하 고 해당 기본 *Elements.xml* 파일을 제거할 수 있습니다.

2. MyAppResources와 같이 *.resx* 확장명을 사용 하 여 선택한 사용자의 이름을 기본 언어 리소스 파일에 제공 합니다. 지역화된 각 리소스 파일에 동일한 기본 이름을 사용하지만 문화권 [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]를 추가합니다. 예를 들어 독일어로 지역화 된 리소스의 이름을 *MyAppResources.de로*합니다.

3. 각 리소스 파일의 **배포 유형** 속성 값을 **appglobalresource** 로 변경 하 여 서버의 App_GlobalResources 폴더에 배포 합니다.

4. 리소스를 사용 하 여 ASPX 태그 외에도 코드를 지역화 하는 경우 각 파일의 **빌드 작업** 속성 값을 **포함 리소스로**둡니다. 리소스 파일을 사용 하 여 태그를 지역화 하는 경우 필요에 따라 파일의 속성 값을 **내용**으로 변경할 수 있습니다. 자세한 내용은 [SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)를 참조 하세요.

5. 각 리소스 파일을 열고 각 파일에서 동일한 문자열 Id를 사용 하 여 지역화 된 문자열을 추가 합니다.

6. [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]ASPX 페이지 또는 컨트롤에 대 한 태그에서 하드 코드 된 문자열을 다음 형식을 사용 하는 값으로 바꿉니다.

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     예를 들어 응용 프로그램 페이지에서 레이블 컨트롤의 텍스트를 지역화 하려면 다음과 같이 변경 합니다.

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     to

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. **F5** 키를 선택 하 여 응용 프로그램을 빌드하고 실행 합니다.

8. SharePoint에서 표시 언어를 기본값에서 변경 합니다.

     지역화 된 문자열이 응용 프로그램에 표시 됩니다. 지역화 된 리소스를 표시 하려면 SharePoint 서버에 리소스 파일의 문화권과 일치 하는 언어 팩이 설치 되어 있어야 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)
- [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)
- [방법: 리소스 파일 추가](../sharepoint/how-to-add-a-resource-file.md)
- [방법: 코드 지역화](../sharepoint/how-to-localize-code.md)

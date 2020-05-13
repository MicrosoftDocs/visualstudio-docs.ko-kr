---
title: 코딩된 UI 테스트를 사용하여 SharePoint 2010 애플리케이션 테스트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0ec4c0a9594202b6755500d683c426238264aec3
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586976"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>코딩된 UI 테스트를 사용하여 SharePoint 2010 애플리케이션 테스트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SharePoint 애플리케이션에 코딩된 UI 테스트를 포함하면 해당 UI 컨트롤을 포함해서 전체 애플리케이션이 올바르게 작동하는지 확인할 수 있습니다. 코딩된 UI 테스트는 또한 사용자 인터페이스에서 값 및 논리의 유효성을 검사할 수 있습니다.

 **요구 사항**

- Visual Studio Enterprise

## <a name="what-else-should-i-know-about-coded-ui-tests"></a>코딩된 UI 테스트에 대해 그 밖에 알아야 할 내용
 코딩된 UI 테스트를 사용할 때의 이점에 대한 자세한 내용은 [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md) 및 [Visual Studio 2012를 사용한 연속 배달 테스트 – 5장 시스템 테스트 자동화](https://msdn.microsoft.com/library/jj159335.aspx)를 참조하세요.

 **참고 사항**

- ![Prereq](../test/media/prereq.png "필수 구성 요소") SharePoint 응용 프로그램에 대 한 코딩 된 UI 테스트는 SharePoint 2010 에서만 지원 됩니다.

- ![Prereq](../test/media/prereq.png "필수 구성 요소") SharePoint 응용 프로그램에서 Visio 및 PowerPoint 2010 컨트롤은 지원 되지 않습니다.

## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>SharePoint 응용 프로그램에 대해 코딩된 UI 테스트 만들기
 SharePoint 2010 애플리케이션에 대한[코딩된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) 는 다른 유형의 애플리케이션에 대해 테스트 만들기와 동일합니다. 기록 및 재생은 웹 편집 인터페이스의 모든 컨트롤에 대해 지원됩니다. 범주 및 웹 파트 선택 인터페이스는 모두 표준 웹 컨트롤입니다.

 ![SharePoint 웹 파트](../test/media/cuit-sharepoint.png "CUIT_SharePoint")

> [!NOTE]
> 작업을 기록하는 경우 코드를 생성하기 전에 작업의 유효성을 검사합니다. 마우스를 위로 가져가는 것과 관련해서는 몇 가지 동작이 있으므로 기본적으로 설정됩니다. 코딩된 UI 테스트에서 중복된 위로 가져가기는 제거할 때 주의가 필요합니다. 이렇게 하려면 테스트에 대한 코드를 편집하거나 [코딩된 UI 테스트 편집기](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)를 사용합니다.

## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>SharePoint 응용 프로그램 내에 Office 2010 컨트롤 테스트 포함
 SharePoint 응용 프로그램에서 일부 Office 2010 웹 파트에 대해 자동화를 설정하려면 코드를 약간 수정해야 합니다.

> [!WARNING]
> Visio 및 PowerPoint 2010 컨트롤은 지원되지 않습니다.

### <a name="excel-2010-cell-controls"></a>Excel 2010 셀 컨트롤
 Excel 셀 컨트롤을 포함하려면 코딩된 UI 테스트의 코드에서 일부 항목을 변경해야 합니다.

> [!WARNING]
> 화살표 작업 후 Excel 셀에 텍스트를 입력하는 작업은 올바르게 기록되지 않습니다. 마우스를 사용해서 셀을 선택하세요.

 빈 셀에 대한 작업을 기록할 때는 셀을 두 번 클릭하고 텍스트 설정 작업을 수행하여 코드를 수정해야 합니다. 셀을 클릭하고 키보드 작업을 수행하면 셀 내에서 `textarea` 가 활성화되기 때문에 이 작업이 필요합니다. 빈 셀에서 단순히 `setvalue` 를 기록하면 셀을 클릭할 때까지 제공되지 않은 `editbox` 가 검색됩니다. 다음은 그 예입니다. 

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

 비어 있지 않은 셀에서 작업을 기록할 때는 셀에 텍스트를 입력하는 순간 셀의 자식으로 새로운 \<div> 컨트롤이 추가되기 때문에 기록이 조금 더 복잡해집니다. 새로운 \<div> 컨트롤에는 사용자가 방금 입력한 텍스트가 포함됩니다. 레코더는 새로운 \<div> 컨트롤에서 작업을 기록해야 하지만 테스트를 입력할 때까지는 새로운 \<div> 컨트롤이 존재하지 않기 때문에 그렇게 할 수 없습니다. 이 문제를 해결하기 위해서는 다음과 같이 코드를 직접 변경해야 합니다.

1. 셀 초기화로 이동하고 `RowIndex` 및 `ColumnIndex` 를 주 속성으로 지정합니다.

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. 셀의 `HtmlDiv` 자식을 찾습니다.

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }

    ```

3. `HtmlDiv`에서 마우스 두 번 클릭 작업에 대한 코드를 추가합니다.

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. `TextArea`에서 텍스트를 설정하는 코드를 추가합니다.

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ```

## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>SharePoint 2010 응용 프로그램에서 Silverlight 웹 파트의 코딩된 UI 테스트 사용
 Visual Studio 2012 이상에서는 Silverlight 테스트가 지원되지 않습니다. 그러나 SharePoint 2010 앱에서 Silverlight 웹 파트를 테스트하려면 Visual Studio 갤러리에서 별도의 Silverlight 플러그 인을 설치할 수 있습니다.

#### <a name="setting-up-your-machine"></a>컴퓨터 설정

1. Visual Studio 2012.1 이상이 설치되어 있는지 확인합니다.

2. [Silverlight용 Microsoft Visual Studio UI 테스트 플러그인](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudioUITestPluginforSilverlight)을 설치합니다.

3. [Fiddler](http://www.fiddler2.com/fiddler2/)를 설치합니다. 이 도구는 단순히 HTTP 트래픽을 캡처하고 기록하는 도구입니다.

4. [fiddlerXap 프로젝트](https://40jajy3iyl373v772m19fybm-wpengine.netdna-ssl.com/wp-content/uploads/sites/6/2019/02/FiddlerXapProxy.zip)를 다운로드합니다. 파일의 압축을 풀고, 빌드하고, “CopySLHelper.bat” 스크립트를 실행하여 Fiddler 도구를 사용할 때 Silverlight 웹 파트를 테스트하는 데 필요한 도우미 DLL을 설치합니다.

   컴퓨터를 설정한 후 Silverlight 웹 파트에서 SharePoint 2010 응용 프로그램 테스트를 시작하려면 다음 단계를 수행합니다.

#### <a name="testing-silverlight-web-parts"></a>Silverlight 웹 파트 테스트

1. Fiddler를 시작합니다.

2. 브라우저 캐시를 지웁니다. Silverlight UI 자동화 도우미 DLL을 포함하는 XAP 파일은 일반적으로 캐시에 저장되기 때문에 이 과정이 필요합니다. 브라우저 캐시를 지울 수 있도록 수정된 XAP 파일이 선택되었는지 확인해야 합니다.

3. 웹 페이지를 엽니다.

4. 레코더를 시작하고 일반 웹 애플리케이션 테스트와 마찬가지로 코드를 생성합니다.

5. 생성된 코드가 Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll을 참조하는지 확인해야 합니다.

     자세한 내용은 [Visual Studio 2012에서 SharePoint 2010 UI 테스트](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/)를 참조하세요.

## <a name="external-resources"></a>외부 리소스

### <a name="blogs"></a>블로그
 [Visual Studio 2012에서 SharePoint 2010 UI 테스트](https://devblogs.microsoft.com/devops/ui-testing-sharepoint-2010-with-visual-studio-2012/)

 [코딩된 UI 테스트에서 Silverlight 컨트롤에 대한 검색 논리 이해](https://tapas-techsnips.blogspot.com/)

 [Silverlight 컨트롤의 속성 페치](https://tapas-techsnips.blogspot.com/)

 [코딩된 UI 테스트에 대한 콘텐츠 인덱스](https://blogs.msdn.microsoft.com/mathew_aniyan/2013/02/18/content-index-for-coded-ui-test/)

### <a name="guidance"></a>지침
 [Visual Studio 2012을 사용한 연속 배달 테스트 – 5 장 시스템 테스트 자동화](https://msdn.microsoft.com/library/jj159335.aspx)

### <a name="forum"></a>포럼
 [Visual Studio ALM + Team Foundation Server 블로그](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)

## <a name="see-also"></a>참고 항목
 [UI 자동화를 사용 하 여 코드 테스트](../test/use-ui-automation-to-test-your-code.md) [웹 성능 테스트 및 부하 테스트 sharepoint 2010 및 2013 응용 프로그램](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) [sharepoint](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) [코드 확인 및 디버깅](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c) sharepoint [솔루션 빌드 및 디버깅 Sharepoint 솔루션 빌드 및 디버깅](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) sharepoint [응용 프로그램의 성능 프로 파일링](https://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)

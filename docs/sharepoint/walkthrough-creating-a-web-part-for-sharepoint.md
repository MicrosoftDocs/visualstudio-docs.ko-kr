---
title: '연습: SharePoint 용 웹 파트 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d8b5e05fb234e9997bce615f7b2de1d790c1ae0
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014577"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>연습: SharePoint 용 웹 파트 만들기

웹 파트를 사용 하면 사용자가 브라우저를 사용 하 여 SharePoint 사이트 페이지의 콘텐츠, 모양 및 동작을 직접 수정할 수 있습니다. 이 연습에서는 Visual Studio 2010에서 **웹 파트** 항목 템플릿을 사용 하 여 웹 파트를 만드는 방법을 보여 줍니다.

웹 파트는 직원을 데이터 표에 표시 합니다. 사용자는 직원 데이터를 포함 하는 파일의 위치를 지정 합니다. 사용자는 관리자 인 직원이 목록에만 표시 되도록 데이터 표를 필터링 할 수도 있습니다.

이 연습에서는 다음 작업을 수행합니다.

- Visual Studio **웹 파트** 항목 템플릿을 사용 하 여 웹 파트를 만듭니다.

- 웹 파트의 사용자가 설정할 수 있는 속성을 만듭니다. 이 속성은 employee 데이터 파일의 위치를 지정 합니다.

- 웹 파트 컨트롤 컬렉션에 컨트롤을 추가 하 여 웹 파트에서 콘텐츠를 렌더링 합니다.

- 렌더링 된 웹 파트의 동사 메뉴에 나타나는 *동사* 라고 하는 새 메뉴 항목을 만듭니다. 동사를 사용 하면 사용자가 웹 파트에 표시 되는 데이터를 수정할 수 있습니다.

- SharePoint에서 웹 파트 테스트

    > [!NOTE]
    > 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- Visual Studio 2017 또는 Azure DevOps Services입니다.

## <a name="create-an-empty-sharepoint-project"></a>빈 SharePoint 프로젝트 만들기

먼저 빈 SharePoint 프로젝트를 만듭니다. 나중에 **웹 파트** 항목 템플릿을 사용 하 여 프로젝트에 웹 파트를 추가 합니다.

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **관리자 권한으로 실행** 옵션을 사용 하 여 시작 합니다.

2. 남자 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다.

3. **새 프로젝트** 대화 상자에서 사용 하려는 언어 아래의 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. **템플릿** 창에서 **SharePoint 2010 프로젝트**를 선택한 다음 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다. 이 마법사를 사용 하 여 프로젝트를 디버깅 하는 데 사용할 사이트와 솔루션의 신뢰 수준을 선택할 수 있습니다.

5. **팜 솔루션으로 배포** 옵션 단추를 선택한 다음 **마침** 단추를 선택 하 여 기본 로컬 SharePoint 사이트를 적용 합니다.

## <a name="add-a-web-part-to-the-project"></a>프로젝트에 웹 파트 추가

프로젝트에 **웹 파트** 항목을 추가 합니다. 웹 **파트** 항목은 웹 파트 코드 파일을 추가 합니다. 나중에 웹 파트 코드 파일에 웹 파트의 콘텐츠를 렌더링 하는 코드를 추가 합니다.

1. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

2. **새 항목 추가** 대화 상자의 **설치 된 템플릿** 창에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. SharePoint 템플릿 목록에서 **웹 파트** 템플릿을 선택 하 고 **추가** 단추를 선택 합니다.

     **웹 파트** 항목이 **솔루션 탐색기**에 나타납니다.

## <a name="rendering-content-in-the-web-part"></a>웹 파트에서 콘텐츠 렌더링

웹 파트 클래스의 controls 컬렉션에 웹 파트를 추가 하 여 웹 파트에 표시할 컨트롤을 지정할 수 있습니다.

1. **솔루션 탐색기**에서 *WebPart1* (Visual Basic) 또는 *WebPart1.cs* (c #)를 엽니다.

     웹 파트 코드 파일이 코드 편집기에서 열립니다.

2. 웹 파트 코드 파일의 맨 위에 다음 지시문을 추가 합니다.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. `WebPart1` 클래스에 다음 코드를 추가합니다. 이 코드는 다음 필드를 선언 합니다.

   - 웹 파트에 직원을 표시 하는 데이터 표

   - 데이터 표를 필터링 하는 데 사용 되는 컨트롤에 표시 되는 텍스트입니다.

   - 데이터 표에서 데이터를 표시할 수 없는 경우 오류를 표시 하는 레이블입니다.

   - 직원 데이터 파일의 경로를 포함 하는 문자열입니다.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. `WebPart1` 클래스에 다음 코드를 추가합니다. 이 코드는 이라는 사용자 지정 속성을 `DataFilePath` 웹 파트에 추가 합니다. 사용자 지정 속성은 SharePoint에서 사용자가 설정할 수 있는 속성입니다. 이 속성은 데이터 그리드를 채우는 데 사용 되는 XML 데이터 파일의 위치를 가져오고 설정 합니다.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. `CreateChildControls` 메서드를 다음 코드로 바꿉니다. 이 코드는 다음 작업을 수행합니다.

   - 이전 단계에서 선언한 데이터 표 및 레이블을 추가 합니다.

   - 데이터 표를 직원 데이터를 포함 하는 XML 파일에 바인딩합니다.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. `WebPart1` 클래스에 다음 메서드를 추가합니다. 이 코드는 다음 작업을 수행합니다.

   - 렌더링 된 웹 파트의 웹 파트 동사 메뉴에 나타나는 동사를 만듭니다.

   - 사용자가 동사 메뉴에서 동사를 선택할 때 발생하는 이벤트를 처리합니다. 이 코드는 데이터 표에 표시 되는 직원 목록을 필터링 합니다.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>웹 파트 테스트

프로젝트를 실행 하면 SharePoint 사이트가 열립니다. 웹 파트는 SharePoint의 웹 파트 갤러리에 자동으로 추가 됩니다. 웹 파트를 웹 파트 페이지에 추가할 수 있습니다.

1. 다음 XML을 메모장 파일에 붙여 넣습니다. 이 XML 파일에는 웹 파트에 표시 되는 샘플 데이터가 포함 되어 있습니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. 메모장의 메뉴 모음에서 **파일**다른  >  **이름으로 저장**을 선택 합니다.

3. 다른 이름 **으로 저장** 대화 상자의 파일 **형식** 목록에서 **모든 파일**을 선택 합니다.

4. **파일 이름** 상자에 **data.xml**을 입력 합니다.

5. 폴더 **찾아보기** 단추를 사용 하 여 폴더를 선택한 다음 **저장** 단추를 선택 합니다.

6. Visual Studio에서 **F5** 키를 선택 합니다.

     SharePoint 사이트가 열립니다.

7. **사이트 작업** 메뉴에서 **기타 옵션**을 선택 합니다.

8. **만들기** 페이지에서 **웹 파트 페이지** 유형을 선택한 다음 **만들기** 단추를 선택 합니다.

9. **새 웹 파트 페이지** 페이지에서 **SampleWebPartPage**페이지의 이름을 지정한 다음 **만들기** 단추를 선택 합니다.

     웹 파트 페이지가 표시 됩니다.

10. 웹 파트 페이지에서 영역을 선택 합니다.

11. 페이지 위쪽에서 **삽입** 탭을 선택한 다음 **웹 파트** 단추를 선택 합니다.

12. **범주** 창에서 **사용자 지정** 폴더를 선택 하 고 **WebPart1** 웹 파트를 선택한 다음 **추가** 단추를 선택 합니다.

     웹 파트가 페이지에 표시 됩니다.

## <a name="test-the-custom-property"></a>사용자 지정 속성 테스트

웹 파트에 표시 되는 데이터 표를 채우려면 각 직원에 대 한 데이터가 포함 된 XML 파일의 경로를 지정 합니다.

1. 웹 파트의 오른쪽에 나타나는 화살표를 선택한 다음 나타나는 메뉴에서 **웹 파트 편집** 을 선택 합니다.

     웹 파트의 속성을 포함 하는 창이 페이지의 오른쪽에 표시 됩니다.

2. 창에서 **기타** 노드를 확장 하 고 이전에 만든 XML 파일의 경로를 입력 한 다음 **적용** 단추를 선택 하 고 **확인** 단추를 선택 합니다.

     직원 목록이 웹 파트에 표시 되는지 확인 합니다.

## <a name="test-the-web-part-verb"></a>웹 파트 동사 테스트

웹 파트 동사 메뉴에 표시 되는 항목을 클릭 하 여 관리자가 아닌 직원을 표시 하 고 숨깁니다.

1. 웹 파트의 오른쪽에 나타나는 화살표를 선택한 다음 나타나는 메뉴에서 **관리자만 표시** 를 선택 합니다.

     관리자 인 직원만 웹 파트에 표시 됩니다.

2. 화살표를 다시 선택한 다음 표시 되는 메뉴에서 **모든 직원 표시** 를 선택 합니다.

     모든 직원이 웹 파트에 표시 됩니다.

## <a name="see-also"></a>참고 항목

SharePoint 용 웹 [파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [방법: SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 [연습: 디자이너를 사용 하 여 SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)

---
title: '방법: 코드 지역화 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c1963ff0b6ef317dfa1a2c8154a1628710dc562
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016691"
---
# <a name="how-to-localize-code"></a>방법: 코드 지역화
  지역화 되지 않은 코드는 하드 코드 된 문자열 값을 사용 합니다. 코드 문자열을 지역화 하려면 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 지역화 된 리소스를 참조 하는 메서드인에 대 한 호출로 대체 합니다.

## <a name="localize-code"></a>코드 지역화

#### <a name="to-localize-code"></a>코드를 지역화 하려면

1. **솔루션 탐색기**에서 프로젝트 항목에 대 한 바로 가기 메뉴를 열고 모듈 **추가**를 선택  >  **Module**합니다.

     **리소스 파일** 템플릿을 선택 합니다.

    > [!NOTE]
    > 배포 유형 속성을 사용할 수 있도록 SharePoint 프로젝트 항목에 리소스 파일을 추가 해야 합니다. 이 속성은이 절차의 뒷부분에서 필요 합니다.

2. *MyAppResources*와 같이 *.resx* 확장명을 사용 하 여 선택한 사용자의 이름을 기본 언어 리소스 파일에 제공 합니다.

3. 1단계와 2단계를 반복하여 지역화된 언어마다 하나씩 별도의 리소스 파일을 SharePoint 프로젝트 항목에 추가합니다.

     지역화 된 각 리소스 파일에 대해 동일한 기본 이름을 사용 하지만 문화권 ID를 추가 합니다. 예를 들어 독일어로 지역화 된 리소스의 이름을 *MyAppResources.de로*합니다.

4. 각 리소스 파일을 열고 지역화 된 문자열을 추가 합니다. 각 파일에서 동일한 문자열 ID를 사용합니다.

5. 각 리소스 파일의 **배포 유형** 속성 값을 **appglobalresource** 로 변경 하 여 각 파일이 서버의 App_GlobalResources 폴더에 배포 되도록 합니다.

6. 각 파일의 **빌드 작업** 속성 값을 **포함 리소스로**둡니다.

     포함 리소스는 프로젝트의 DLL로 컴파일됩니다.

7. 프로젝트를 빌드하여 리소스 위성 Dll을 만듭니다.

8. **패키지 디자이너**에서 **고급** 탭을 선택한 후 위성 어셈블리를 추가 합니다.

9. **위치** 상자에서 *-de \\ \<Project Item Name>.resources.dll*와 같은 위치 경로에 문화권 ID 폴더를 추가 합니다.

10. 솔루션이 System.web 어셈블리를 아직 참조 하지 않는 경우 해당 어셈블리에 대 한 참조를 추가 하 고 코드의 지시문을에 추가 <xref:System.Web> 합니다.

11. 사용자에게 표시되는 코드에서 UI 텍스트, 오류 및 메시지 텍스트와 같은 하드 코딩된 모든 문자열을 찾습니다. 다음 구문을 사용하여 <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> 메서드를 호출하여 이러한 문자열을 바꿉니다.

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. **F5** 키를 선택 하 여 응용 프로그램을 빌드하고 실행 합니다.

13. SharePoint에서 표시 언어를 기본값에서 변경 합니다.

     지역화 된 문자열이 응용 프로그램에 표시 됩니다. 지역화 된 리소스를 표시 하려면 SharePoint 서버에 리소스 파일의 문화권과 일치 하는 언어 팩이 설치 되어 있어야 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)
- [방법: 기능 지역화](../sharepoint/how-to-localize-a-feature.md)
- [방법: ASPX 태그 지역화](../sharepoint/how-to-localize-aspx-markup.md)
- [방법: 리소스 파일 추가](../sharepoint/how-to-add-a-resource-file.md)

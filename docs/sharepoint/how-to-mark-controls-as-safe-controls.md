---
title: '방법: 컨트롤을 안전 컨트롤로 표시 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, safe controls
- SharePoint development in Visual Studio, advanced packaging tools
- safe controls [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd7ed13504d3d91f4239a8ea070454e1c31b1114
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016261"
---
# <a name="how-to-mark-controls-as-safe-controls"></a>방법: 컨트롤을 안전 컨트롤로 표시
  보안을 위해 SharePoint는 스크립트 삽입에 대해 보호 되는 웹 컨트롤과 그렇지 않은 웹 컨트롤을 구별 합니다. 신뢰할 수 없는 사용자가 보호 된 컨트롤 또는 *안전 컨트롤*에 액세스할 수 있습니다. 패키지에 어셈블리를 추가할 때 SharePoint 프로젝트 항목 또는 **패키지 디자이너** 의 안전 컨트롤 항목 속성에서 컨트롤을 안전한 것으로 표시할 수 있습니다. 자세한 내용은 다음을 참조하세요.

- [web.config 파일 설정을 변경](/previous-versions/office/developer/sharepoint-2007/bb802890(v=office.12)) 하 고 [웹 파트 어셈블리를 안전 컨트롤로 등록](/previous-versions/office/developer/sharepoint2003/dd587360(v=office.11))합니다.

> [!IMPORTANT]
> 이러한 절차는 설명을 위한 목적으로 제공 됩니다. 컨트롤을 안전 하 게 보호 하는 경우에만 컨트롤을 안전 하 게 표시 합니다.

## <a name="marking-safe-controls-in-the-safe-control-entries-property"></a>Safe 컨트롤 항목 속성에서 Safe 컨트롤 표시

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-safe-control-entries-property"></a>안전 컨트롤 항목 속성에서 컨트롤을 safe 또는 unsafe로 표시 하려면

1. 시각적 웹 파트 프로젝트를 사용 하 여 SharePoint 솔루션을 만듭니다.

2. 텍스트 상자와 단추 라는 두 개의 컨트롤을 웹 파트에 추가 합니다. 기본값은 각각 TextBox1 및 Button1의 기본값을 유지 합니다.

3. 웹 파트의 **안전 컨트롤 항목** 속성에 두 개의 항목을 추가 합니다. 이렇게 하려면 **속성** 창에서 **안전 컨트롤 항목** 속성 옆에 있는 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 선택 합니다.

     **안전 컨트롤 항목** 대화 상자가 나타납니다.

4. **안전 컨트롤 항목** 대화 상자에서 **추가** 단추를 두 번 선택 하 여 두 개의 안전 컨트롤 항목을 **멤버** 창에 추가 합니다. 하나는 단추이 고 다른 하나는 텍스트 상자에 추가 합니다.

5. 첫 번째 안전 컨트롤 항목을 선택 하 고 **safe** 속성의 값을 **false**로 변경 하 고, 해당 **형식 이름** 속성을 **Button1**로, **스크립트에 대해 safe** 속성을 **false**로 변경 합니다.

     이 단계에서는 단추 컨트롤을 안전 하지 않은 컨트롤로 식별 합니다.

6. 목록에서 두 번째 안전 컨트롤 항목을 선택합니다. **Safe** 속성의 값을 **true** 로 유지 하 고 해당 **형식 이름** 속성을 **TextBox1** 로 설정 하 고 스크립트 속성에 **대 한 보안** 을 **true**로 설정 합니다.

     이제 텍스트 상자 컨트롤이 스크립트 삽입에 대 한 안전한 컨트롤로 표시 됩니다.

7. **확인** 단추를 선택하여 대화 상자를 닫습니다.

## <a name="marking-safe-controls-in-the-package-designer"></a>패키지 디자이너에서 안전 컨트롤 표시

#### <a name="to-mark-controls-as-safe-or-unsafe-in-the-package-designer"></a>패키지 디자이너에서 컨트롤을 safe 또는 unsafe로 표시 하려면

1. 시각적 웹 파트 프로젝트를 사용 하 여 SharePoint 솔루션을 만듭니다.

2. 텍스트 상자와 단추 라는 두 개의 컨트롤을 웹 파트에 추가 합니다. 기본값은 각각 TextBox1 및 Button1의 기본값을 유지 합니다.

     컨트롤의 네임 스페이스는 나중에 사용 되기 때문에 기록해 둡니다.

3. 메뉴 모음에서 빌드 **Build**  >  **솔루션** 빌드를 선택 하 여 프로젝트를 빌드합니다.

4. 다른 SharePoint 솔루션을 만듭니다.

5. **솔루션 탐색기**에서 *패키지 파일에* 대 한 바로 가기 메뉴를 열고 **열기** 를 선택 하 여 **패키지 디자이너**를 엽니다.

6. **패키지 디자이너**에서 **고급** 탭을 선택 합니다.

7. **추가 어셈블리**에서 **추가** 단추를 선택한 다음 목록에서 **기존 어셈블리 추가** 를 선택 합니다.

8. **기존 어셈블리 추가** 대화 상자에서 **소스 경로**옆에 있는 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 선택 합니다.

9. 1 단계에서 만든 SharePoint 솔루션에서 어셈블리를 선택한 다음 **열기** 단추를 선택 합니다.

10. 이 예에서는 **배포 대상** 옵션을 GlobalAssemblyCache로 그대로 둡니다.

     이 단계를 수행 하면 어셈블리가 시스템 GAC (전역 어셈블리 캐시)에 배포 됩니다. 어셈블리를 웹 응용 프로그램 (Bin) 폴더에 배포 하려면 해당 옵션을 대신 선택 합니다. 자세한 내용은 [SharePoint Foundation에서 웹 파트 배포](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14))를 참조 하세요.

11. **안전 컨트롤** 상자에서 **새 항목을 추가 하려면 여기를 클릭** 하십시오. 단추를 선택 합니다.

12. 다음 표에서 속성의 값을 입력 합니다.

    |속성 이름|값|
    |-------------------|-----------|
    |네임스페이스|컨트롤의 정규화 된 네임 스페이스 (예: **BdcModelProject1. VisualWebPart1**)입니다.|
    |유형 이름|Button1|
    |어셈블리 이름|강력한 어셈블리 이름 (예: 14.0.0.0, Version =, Culture = 중립, PublicKeyToken = 71e9bce111e9429c).|
    |안전|**안전** 확인란의 선택을 취소 합니다.|
    |스크립트에 대해 안전|스크립트를 **안전** 하 게 유지 확인란을 선택 취소 합니다.|

    > [!NOTE]
    > **패키지 디자이너** 의 **고급** 탭을 통해 추가 된 어셈블리의 **어셈블리 이름** 값은 토큰이 될 수 없으며 강력한 이름의 어셈블리 여야 합니다. 자세한 내용은 [강력한 이름의 어셈블리 만들기 및 사용](/previous-versions/dotnet/netframework-4.0/xwb8f617(v=vs.100))을 참조하세요.

13. **Tab** 키를 선택 하 여 다른 안전 컨트롤 항목을 만듭니다.

14. **새 항목을 추가 하려면 여기를 클릭** 하십시오. 단추를 다시 선택 합니다.

15. 다음 표에서 속성의 값을 입력 합니다.

    |속성 이름|값|
    |-------------------|-----------|
    |네임스페이스|컨트롤의 정규화 된 네임 스페이스 (예: **BdcModelProject1. VisualWebPart1**)입니다.|
    |유형 이름|TextBox1|
    |어셈블리 이름|강력한 어셈블리 이름 (예: 14.0.0.0, Version =, Culture = 중립, PublicKeyToken = 71e9bce111e9429c).|
    |안전|**안전** 확인란을 선택 합니다.|
    |스크립트에 대해 안전|**스크립트에 대해 안전** 확인란을 선택 합니다.|

16. **Tab** 키를 선택 하 고 **확인** 단추를 선택 하 여 대화 상자를 닫습니다.

## <a name="see-also"></a>참고 항목
- [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

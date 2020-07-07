---
title: MSBuild 대상을 사용 하 여 SharePoint 솔루션 패키지 사용자 지정
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6570b1e3c16f1935813682e2c29051c4ac7d64a
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016882"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>방법: MSBuild 대상을 사용 하 여 SharePoint 솔루션 패키지 사용자 지정
  명령 프롬프트에서 MSBuild 대상을 사용 하 여 Visual Studio에서 SharePoint 패키지 파일 (*.wsp*)을 만드는 방법을 사용자 지정할 수 있습니다. 예를 들어 MSBuild 속성을 사용자 지정하여 패키징 중간 디렉터리 및 열거되는 파일을 지정하는 MSBuild 항목 그룹을 변경할 수 있습니다.

## <a name="customize-and-run-msbuild-targets"></a>MSBuild 대상 사용자 지정 및 실행
 BeforeLayout 및 AfterLayout 대상을 사용자 지정하는 경우 패키지 레이아웃 전에 패키지될 파일의 추가, 제거, 수정 등의 작업을 수행할 수 있습니다.

#### <a name="to-customize-the-beforelayout-target"></a>BeforeLayout 대상을 사용자 지정 하려면

1. 메모장과 같은 편집기를 열고 다음 코드를 추가합니다.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    이 예제에서는 이 대상의 패키징 전에 메시지를 표시합니다.

2. 파일의 이름을 **Customlayout. groove**로 지정한 다음 sharepoint 프로젝트의 폴더에 저장 합니다.

3. 프로젝트를 열고 바로 가기 메뉴를 연 다음 **프로젝트 언로드**를 선택 합니다.

4. **솔루션 탐색기**에서 프로젝트에 대 한 바로 가기 메뉴를 연 다음 * \<ProjectName> .vbproj* **편집** 또는 * \<ProjectName> .csproj* **편집** 을 선택 합니다.

5. 프로젝트 파일의 끝 부분에 있는 `Import` 행 뒤에 다음 줄을 추가합니다.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. 프로젝트 파일을 저장한 후 닫습니다.

7. **솔루션 탐색기**에서 프로젝트에 대 한 바로 가기 메뉴를 연 다음 **프로젝트 다시 로드**를 선택 합니다.

   프로젝트를 게시할 때 패키징이 시작되기 전에 메시지가 출력에 나타납니다.

#### <a name="to-customize-the-afterlayout-target"></a>AfterLayout 대상을 사용자 지정 하려면

1. 메뉴 모음에서 **파일**파일 열기를 선택  >  **Open**  >  **File**합니다.

2. **파일 열기** 대화 상자에서 프로젝트 폴더로 이동 하 고 customlayout. 대상 파일을 선택한 다음 **열기** 단추를 선택 합니다.

3. `</Project>` 태그 바로 앞에 다음 코드를 추가합니다.

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    이 예제에서는 이 대상이 패키지된 후 메시지를 표시합니다.

4. 대상 파일을 저장한 후 닫습니다.

5. Visual Studio를 다시 시작한 다음 프로젝트를 엽니다.

   프로젝트를 게시하면 패키징이 시작되기 전에 BeforeLayout 메시지가 나타나고 패키징이 완료된 후 AfterLayout 메시지가 나타납니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

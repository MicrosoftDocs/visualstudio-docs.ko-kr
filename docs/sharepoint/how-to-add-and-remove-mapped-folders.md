---
title: '방법: 매핑된 폴더 추가 및 제거 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80fbd3e18b8d440eae2873c73013ad7468073640
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014649"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>방법: 매핑된 폴더 추가 및 제거
  SharePoint에서 이미지 및 레이아웃과 같은 일반적으로 사용 되는 일부 폴더는 파일 계층 구조에 포함 됩니다. 이러한 폴더를 SharePoint 프로젝트에 매핑하여 더 쉽게 액세스할 수 있습니다. 매핑된 폴더는 sharepoint Server 설치 시 파일의 물리적 위치에 해당 하는 SharePoint 프로젝트의 폴더입니다.

 SharePoint 응용 프로그램을 배포 하면 매핑된 폴더와 모든 하위 폴더의 내용이 솔루션 패키지 (.wsp)에 의해 sharepoint 폴더 트리의 지정 된 위치에 있는 SharePoint를 실행 하는 서버로 복사 됩니다. 이 위치는 매핑된 폴더에 대해 설정 된 **배포 위치** 속성에 의해 결정 됩니다. 매핑된 폴더의 모든 하위 폴더는 매핑된 폴더의 **배포 위치** 를 기준으로 합니다. 매핑된 폴더 이름이 아니라 **배포 위치** 속성은 항목을 배포할 위치를 결정 합니다.
메뉴 모음이 나 프로젝트에 대 한 바로 가기 메뉴의 명령을 사용 하 여 프로젝트에 매핑된 폴더를 추가할 수 있습니다. **Sharepoint "이미지" 매핑된 폴더** 및 **sharepoint "레이아웃" 폴더** 추가 명령을 사용 하 여 가장 자주 사용 되는 매핑된 폴더를 추가할 수 있습니다. 바로 가기 메뉴에서 **Sharepoint 매핑된 폴더 추가** 명령을 사용 하 고 **Sharepoint 매핑된 폴더 추가** 대화 상자에서 폴더를 지정 하 여 사용 가능한 다른 SharePoint 폴더를 프로젝트에 매핑할 수 있습니다.

## <a name="add-mapped-folders-to-a-project"></a>프로젝트에 매핑된 폴더 추가
 다음 절차에서는 두 개의 매핑된 폴더를 시각적 웹 파트 프로젝트에 추가 하는 방법에 대해 설명 합니다. 시작 하려면 시각적 웹 파트 프로젝트를 만듭니다.

#### <a name="to-add-mapped-folders-to-a-project"></a>프로젝트에 매핑된 폴더를 추가 하려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

2. **새 프로젝트** 대화 상자에서 **Visual Basic** 또는 **Visual c #** 노드를 확장 하 고 **Office/SharePoint** 노드를 확장 한 다음 **sharepoint 솔루션** 노드를 선택 합니다.

3. 프로젝트 템플릿 목록에서 **SharePoint 2013 비주얼 웹 파트** 템플릿을 선택 합니다.

4. **이름** 상자에 **TestProject1**를 입력 하 고 **확인** 단추를 선택 합니다.

5. **SharePoint 사용자 지정 마법사**에서 **마침** 단추를 선택 하 여 기본 설정을 유지 합니다.

6. **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **SharePoint "이미지 추가" 매핑된 폴더**를 선택 합니다.

     이름이 **이미지** 인 폴더가 프로젝트에 표시 되 고 이름이 TestProject1 인 하위 폴더가 포함 됩니다. 이 매핑된 폴더에는 시각적 웹 파트 프로젝트의 이미지가 포함 됩니다.

7. **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **sharepoint 매핑된 폴더 추가** 를 선택 하 여 **sharepoint 매핑된 폴더 추가** 대화 상자를 표시 합니다.

8. 매핑에 사용할 수 있는 폴더의 트리 보기에서 **리소스** 폴더를 선택한 다음 **확인** 단추를 선택 합니다.

     **리소스** 라는 폴더가 프로젝트에 표시 됩니다. 이 폴더는 문자열 리소스 파일과 같은 항목을 저장할 수 있습니다. 하위 폴더는 매핑된 폴더의 콘텐츠를 구성 하는 데 유용할 수 있지만, **SharePoint 매핑된 폴더 추가** 명령을 사용 하 여 매핑된 폴더를 추가할 때 자동으로 생성 되지 않습니다. 하위 폴더를 추가 하려면 **리소스** 폴더를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **새 폴더**를 선택 합니다.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>매핑된 폴더의 배포 위치를 변경 합니다.
 기본적으로 매핑된 폴더는 토큰이 나타내는 SharePoint 루트 설치 경로를 기준으로 특정 위치에 추가 됩니다 \<SharePointRoot> . 그러나 매핑된 폴더의 **배포 위치** 속성을 변경 하 여이 위치를 변경할 수 있습니다. 각 매핑된 폴더에는 고유한 **배포 위치** 속성이 있습니다.

#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>매핑된 폴더의 배포 위치를 변경 하려면

1. 이전에 만든 프로젝트에서 매핑된 폴더를 선택 합니다.

2. **속성** 창의 **배포 위치** 속성에서 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 선택 합니다.

3. **SharePoint 매핑된 폴더 추가** 대화 상자에서 매핑된 폴더를 가리킬 폴더로 이동 합니다.

4. 노드를 선택한 다음 **확인** 단추를 선택 합니다.

## <a name="rename-or-remove-mapped-folders"></a>매핑된 폴더 이름 바꾸기 또는 제거

#### <a name="to-rename-or-remove-a-mapped-folder"></a>매핑된 폴더의 이름을 바꾸거나 제거 하려면

1. 이전에 만든 프로젝트에서 매핑된 폴더를 선택 합니다.

2. 매핑된 폴더의 이름을 바꾸려면 해당 바로 가기 메뉴를 열고 **이름 바꾸기**를 선택한 다음 새 이름을 입력 하 고 enter 키를 선택 합니다.

     또는 이름을 바꿀 매핑된 폴더를 선택 하 고 **속성** 창을 연 다음 **폴더 이름** 속성의 값을 새 이름으로 설정할 수 있습니다.

3. 프로젝트에서 매핑된 폴더를 제거 하려면 해당 바로 가기 메뉴를 열고 **삭제**를 선택한 다음 대화 상자에서 **확인** 단추를 선택 하 여 제거를 확인 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)

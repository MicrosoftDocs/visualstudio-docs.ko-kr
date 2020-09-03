---
title: '방법: 모듈을 사용 하 여 파일 포함 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1ada86be30e207e36c7e0d84d3fd5dd877605e4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016293"
---
# <a name="how-to-include-files-by-using-a-module"></a>방법: 모듈을 사용 하 여 파일 포함
  *모듈 (* 모듈과 혼동 하지 않음 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] )은 ASPX 마스터 페이지, 텍스트 파일 또는 이미지와 같은 파일을 SharePoint에 배포할 수 있는 컨테이너입니다.

 문서 라이브러리 또는 문서 라이브러리 외부의 일반 파일 (예: default.aspx)에 파일을 배포 하도록 선택할 수 있습니다. 문서 라이브러리에 파일을 추가 하려면 `Type="GhostableInLibrary"` **파일** 요소에서를 특성으로 지정 합니다. 이 설정은 SharePoint가 라이브러리에 추가 될 때 파일에 사용할 목록 항목을 만들도록 지시 합니다. 문서 라이브러리 외부에 파일을 배포 하려면 `Type="Ghostable"` **Type** 특성만 지정 하거나 생략 합니다.

## <a name="add-a-module-to-a-sharepoint-solution"></a>SharePoint 솔루션에 모듈 추가

#### <a name="to-add-a-module"></a>모듈을 추가 하려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 SharePoint 프로젝트를 열거나 만듭니다.

     자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)을 참조 하세요.

2. **솔루션 탐색기**에서 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

     **새 항목 추가** 대화 상자가 열립니다.

3. SharePoint 템플릿 목록에서 **모듈** 템플릿을 선택한 다음 **추가** 단추를 선택 합니다.

     이 단계에서는 프로젝트에서 Module1이라는 노드를 만듭니다.

4. Module1에서 *Sample.txt* 파일을 삭제 합니다.

     Sample.txt은 목적에 따라 모든 새 모듈에 포함 되며 필요 하지 않습니다. 파일을 삭제 하면 모듈의 *Elements.xml* 파일 에서도 해당 항목이 제거 됩니다.

5. 파일이 SharePoint의 특정 폴더 구조에 배포 되도록 하려면 Module1 노드를 선택 하 여의 Module1 아래에 해당 폴더를 만든 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음 메뉴 모음에서 **프로젝트**, **새 폴더**를 선택 합니다.

6. 파일을 추가할 폴더를 선택한 다음 메뉴 모음에서 **프로젝트**, **기존 항목 추가**를 선택 합니다.

7. SharePoint에 배포 하려는 파일을 하나 이상 선택한 다음 **추가** 단추를 선택 합니다.

     프로젝트에 파일을 추가 하면 해당 항목이 모듈의 Elements.xml 파일에 자동으로 추가 됩니다. 프로젝트를 배포할 때 파일은 프로젝트의 루트 디렉터리를 기준으로 하 여 SharePoint server에 복사 됩니다 .이 디렉터리는 **파일** 요소의 **Url** 특성 (예:)에 의해 지정 됩니다 `Url="Module1/New Folder/SomeFile.doc` . 파일의 배포 위치를 변경 하려면 **솔루션 탐색기** 의 다른 폴더로 이동 하거나 해당 **Url** 설정을 변경 합니다.

8. 문서 라이브러리에 표시할 모든 파일의 경우 `Type="GhostableInLibrary"` *Elements.xml*의 해당 항목에 특성을 추가 합니다. 예를 들면 다음과 같습니다.

    ```xml
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />
    ```

9. 프로젝트를 배포합니다.

     파일이 SharePoint의 지정 된 위치에 복사 됩니다.

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)

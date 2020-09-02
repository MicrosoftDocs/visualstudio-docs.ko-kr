---
title: URL 선택 대화 상자 (SharePoint 개발)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 991693c3379e008a2a907efd3127290c7e804c22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66261938"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL 선택 대화 상자 (Visual Studio에서 SharePoint 개발)
  URL 선택기 대화 상자에서 프로젝트에 있거나 SharePoint를 실행하는 로컬 서버에 있는 마스터 페이지 파일 또는 이미지 파일과 같은 파일을 선택할 수 있습니다.

 이 대화 상자는 속성을 설정하기 위해 파일을 선택하는 옵션이 있는 경우에 표시됩니다. **속성** 창에서 다양 한 속성 옆에 있는 줄임표 단추 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 선택 하 여이 대화 상자를 열 수 있습니다. 줄임표 단추는 또한 디자이너의 **소스** 뷰에서 특정 특성에 값을 할당 하면 IntelliSense 프롬프트로 표시 됩니다.

## <a name="uielement-list"></a>UI 요소 목록
 **프로젝트 폴더** 프로젝트 또는 SharePoint를 실행 하는 로컬 서버에 정의 된 폴더 목록을 표시 합니다. 확장 단추를 선택하여 하위 폴더를 표시합니다.

 **프로젝트 노드를** 확장 하 여 프로젝트에서 파일을 선택 합니다. 대화 상자에서 선택할 수 있는 것으로 표시 하려면 프로젝트의 파일이 다음 조건을 충족 해야 합니다.

- 파일은 매핑된 폴더에 포함 되어야 합니다.

- 이 파일은 솔루션 패키지에 추가 해야 합니다.

- 다른 프로젝트에서 파일을 찾을 수 없습니다.

  이러한 조건을 충족 하지 않는 파일을 참조 하려는 경우 파일 경로를 수동으로 입력 해야 합니다.

  **서버** 노드를 확장 하 여 SharePoint를 실행 하는 로컬 서버에 있는 파일을 선택 합니다. 대화 상자에서 선택할 수 있는 것으로 표시 하려면 이러한 파일이 다음 조건을 충족 해야 합니다.

- 이 파일은 **이미지**, **레이아웃**또는 **controltemplates**의 다음 매핑된 폴더 중 하나에 있어야 합니다.

- SharePoint 콘텐츠 데이터베이스에서 파일을 찾을 수 없습니다.

  이러한 조건을 충족 하지 않는 파일을 참조 하려는 경우 파일 경로를 수동으로 입력 해야 합니다.

  **폴더 내용** 선택한 폴더에 있는 파일의 목록을 표시 합니다. 파일을 선택한 다음 **확인** 단추를 선택 하 여 대화 상자를 닫고 선택한 항목을 호출한 프로세스로 보냅니다.

  **파일 형식** 수행 중인 작업에 적절 한 파일 목록에서 선택할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [SharePoint에 대 한 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
- [웹 파트 또는 응용 프로그램 페이지의 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

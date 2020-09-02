---
title: '방법: 프로젝트 출력 참조 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bea0f39ae161d8b695f872cb634c35d0cb205c91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016749"
---
# <a name="how-to-add-a-project-output-reference"></a>방법: 프로젝트 출력 참조 추가
  Sharepoint에 비 SharePoint 프로젝트 어셈블리 (또는 .xap 파일)를 SharePoint에 배포 하려면 해당 어셈블리를 프로젝트 출력 참조로 추가 합니다.

 이 프로세스는 두 프로젝트 간에 솔루션 빌드 종속성을 만듭니다. 프로젝트 출력 참조와 연결 된 프로젝트는 SharePoint 프로젝트가 빌드되고 배포 되기 전에 빌드됩니다.

### <a name="to-add-a-project-output-reference"></a>프로젝트 출력 참조를 추가 하려면

1. 하나 이상의 SharePoint 프로젝트와 SharePoint 프로젝트가 아닌 프로젝트를 포함 하는 솔루션을 로드 합니다.

2. **솔루션 탐색기**에서 SharePoint 프로젝트 노드의 항목을 선택 합니다.

3. **속성** 창에서 **프로젝트 출력 참조** 속성을 선택한 후 옆에 있는 줄임표 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 선택 합니다.

4. **프로젝트 출력 참조** 대화 상자에서 **추가** 단추를 선택 합니다.

5. 속성 창에서 **배포 유형** 속성 옆의 화살표를 선택한 다음 참조 하는 비 SharePoint 항목 (예: **elementfile**)에 적절 한 값을 선택 합니다.

6. **프로젝트 이름**옆에 있는 화살표를 선택 하 고 비 SharePoint 프로젝트 항목의 이름을 선택한 다음 **확인** 단추를 선택 합니다.

## <a name="see-also"></a>추가 정보
- [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [방법: 컨트롤을 안전 컨트롤로 표시](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)

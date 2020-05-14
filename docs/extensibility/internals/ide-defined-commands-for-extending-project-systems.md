---
title: 프로젝트 시스템 확장을 위한 IDE 정의 명령 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, project systems
- project systems, environment-defined commands
ms.assetid: 0e33b8e9-16fa-4400-a941-e92d56120e7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61c0b2924548f50ad650389e3ad81759be1986a4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707727"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>프로젝트 시스템 확장을 위한 IDE 정의 명령
프로젝트 시스템을 확장하려는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에서 제공하는 명령 및 명령 그룹을 사용할 수 있습니다.

 다음 섹션에서는 프로젝트 시스템을 확장하는 데 특히 유용한 명령 항목을 나열합니다.

## <a name="command-menus"></a>명령 메뉴
 다음 표에서는 프로젝트 extender를 호출하는 상위 수준 명령을 넣을 수 있는 유용한 위치인 명령 메뉴를 보여 줍니다.

|명령 메뉴|설명|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**프로젝트** 최상위 메뉴입니다.|
|IDM_VS_TOOL_PROJWIN|**솔루션 탐색기** 도구 모음입니다.|

## <a name="shortcut-menus"></a>바로 가기 메뉴
 다음 표에서는 **솔루션 탐색기에서**단일 노드를 선택하거나 **솔루션 탐색기에서**여러 개의 동종 선택 항목이 있는 경우 적용되는 바로 가기 메뉴를 보여 줍니다.

|바로 가기 메뉴|설명|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|프로젝트 노드를 선택한 경우에 적용됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|파일을 선택할 때 적용됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|폴더를 선택한 경우에 적용됩니다.|
|IDM_VS_CTXT_WEBREFFOLDER|웹 참조 폴더를 선택한 경우에 적용됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"참조"라는 참조 루트 노드가 선택된 경우에 적용됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|참조 노드를 선택할 때 적용됩니다. 여기에는 어셈블리, COM 및 프로젝트 참조만 포함됩니다. 웹 참조는 포함되지 않습니다.|

 다음 표에서는 **솔루션 탐색기의** 선택이 여러 계층에 걸쳐 있을 때 적용되는 바로 가기 메뉴를 보여 줍니다.

|바로 가기 메뉴|설명|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|현재 선택 영역에 솔루션 노드 및 루트 프로젝트 노드가 포함된 경우에 적용됩니다.|
|IDM_VS_CTXT_XPROJ_SLNITEM|현재 선택 영역에 솔루션 노드 및 프로젝트 항목이 포함된 경우에 적용됩니다.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|현재 선택이 여러 루트 프로젝트 노드로만 구성된 경우에 적용됩니다.|
|IDM_VS_CTXT_XPROJ_PROJITEM|현재 선택 영역에 루트 프로젝트 노드와 프로젝트 항목이 혼합된 경우에 적용됩니다. 또한 선택 영역에 솔루션 노드가 포함될 수 있습니다.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|현재 선택 영역에 솔루션의 여러 프로젝트의 프로젝트 항목이 포함되어 있거나 동일한 프로젝트에서 다른 유형의 항목이 선택된 경우에 적용됩니다.|

## <a name="command-groups"></a>명령 그룹
 다음 표에서는 프로젝트를 확장할 때 사용할 수 있는 명령 그룹과 <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> 바로 가기 메뉴를 통해 액세스할 수 있는 명령 그룹을 보여 줍니다.

|명령 그룹|설명|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|프로젝트를 빌드, 다시 빌드 및 배포하기 위한 명령입니다.|
|IDG_VS_CTXT_COMPILELINK|프로젝트를 컴파일하고 연결하기 위한 명령입니다.|
|IDG_VS_CTXT_PROJECT_CONFIG|프로젝트 구성 및 빌드 순서를 설정하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_ADD|프로젝트에 항목을 추가하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_START|F5 키와 연결된 시작 프로젝트를 설정하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_SAVE|프로젝트 항목을 저장하기 위한 명령입니다.|
|IDG_VS_CTXT_PROJECT_DEBUG|디버깅에 대한 명령입니다.|
|IDG_VS_CTXT_PROJECT_SCC|소스 제어에 대한 명령입니다.|
|IDG_VS_CTXT_PROJECT_TRANSFER|잘라내기, 복사 및 붙여넣기 작업에 대한 명령입니다.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|**프로젝트 속성** 대화 상자에 대한 액세스를 제공하는 명령입니다.|

## <a name="see-also"></a>참조

- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [다시 사용할 수 있는 단추 그룹 만들기](../../extensibility/creating-reusable-groups-of-buttons.md)

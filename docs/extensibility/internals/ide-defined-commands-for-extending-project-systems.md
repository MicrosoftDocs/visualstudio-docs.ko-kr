---
title: 프로젝트 시스템 확장을 위한 IDE 정의 명령 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707727"
---
# <a name="ide-defined-commands-for-extending-project-systems"></a>프로젝트 시스템 확장을 위한 IDE 정의 명령
프로젝트 시스템을 확장 하려는 경우 IDE에서 제공 하는 명령 및 명령 그룹을 사용할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 다음 섹션에서는 프로젝트 시스템을 확장 하는 데 특히 유용한 명령 항목을 나열 합니다.

## <a name="command-menus"></a>명령 메뉴
 다음 표에서는 프로젝트 extender를 호출 하는 고급 명령을 입력할 수 있는 유용한 위치인 명령 메뉴를 보여 줍니다.

|명령 메뉴|설명|
|------------------|-----------------|
|IDM_VS_MENU_PROJECT|**프로젝트** 최상위 메뉴입니다.|
|IDM_VS_TOOL_PROJWIN|**솔루션 탐색기** 도구 모음입니다.|

## <a name="shortcut-menus"></a>바로 가기 메뉴
 다음 표에서는 **솔루션 탐색기**에서 단일 노드를 선택 하거나 선택 **솔루션 탐색기**된 모든 노드가 같은 유형인 경우에 적용 되는 바로 가기 메뉴를 보여 줍니다.

|바로 가기 메뉴|설명|
|-------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE>|프로젝트 노드를 선택 하는 경우에 적용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_ITEMNODE>|파일이 선택 된 경우에 적용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_FOLDERNODE>|폴더를 선택할 때 적용 됩니다.|
|IDM_VS_CTXT_WEBREFFOLDER|웹 참조 폴더가 선택 된 경우에 적용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCEROOT>|"참조" 라는 참조 루트 노드가 선택 된 경우에 적용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_REFERENCE>|참조 노드가 선택 된 경우에 적용 됩니다. 여기에는 어셈블리, COM 및 프로젝트 참조만 포함 됩니다. 웹 참조를 포함 하지 않습니다.|

 다음 표에서는 **솔루션 탐색기** 의 선택이 여러 계층에 걸쳐 있을 때 적용 되는 바로 가기 메뉴를 보여 줍니다.

|바로 가기 메뉴|설명|
|-------------------|-----------------|
|IDM_VS_CTXT_XPROJ_SLNPROJ|현재 선택 영역에 솔루션 노드 및 루트 프로젝트 노드가 포함 된 경우 적용 됩니다.|
|IDM_VS_CTXT_XPROJ_SLNITEM|현재 선택 영역에 솔루션 노드와 프로젝트 항목이 포함 된 경우 적용 됩니다.|
|IDM_VS_CTXT_XPROJ_MULTIPROJ|현재 선택 영역이 여러 루트 프로젝트 노드만 구성 된 경우에 적용 됩니다.|
|IDM_VS_CTXT_XPROJ_PROJITEM|현재 선택 영역에 루트 프로젝트 노드와 프로젝트 항목이 혼합 되어 있는 경우에 적용 됩니다. 또한 선택 영역에 솔루션 노드가 포함 될 수도 있습니다.|
|IDM_VS_CTXT_XPROJ_MULTIITEM|현재 선택 영역에 솔루션에 있는 여러 프로젝트의 프로젝트 항목이 포함 되어 있거나 동일한 프로젝트에서 다른 형식의 항목이 선택 된 경우에 적용 됩니다.|

## <a name="command-groups"></a>명령 그룹
 다음 표에서는 프로젝트를 확장할 때 사용할 수 있는 명령 그룹과 바로 가기 메뉴를 통해 액세스할 수 있는 명령 그룹을 보여 줍니다 <xref:Microsoft.VisualStudio.Shell.VsMenus.IDM_VS_CTXT_PROJNODE> .

|명령 그룹|설명|
|-------------------|-----------------|
|IDG_VS_CTXT_PROJECT_BUILD|프로젝트를 빌드, 다시 빌드 및 배포 하기 위한 명령입니다.|
|IDG_VS_CTXT_COMPILELINK|프로젝트를 컴파일하고 연결 하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_CONFIG|프로젝트 구성 및 빌드 순서를 설정 하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_ADD|프로젝트에 항목을 추가 하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_START|F5 키와 연결 된 시작 프로젝트를 설정 하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_SAVE|프로젝트 항목을 저장 하는 명령입니다.|
|IDG_VS_CTXT_PROJECT_DEBUG|디버깅을 위한 명령입니다.|
|IDG_VS_CTXT_PROJECT_SCC|원본 제어에 대 한 명령입니다.|
|IDG_VS_CTXT_PROJECT_TRANSFER|잘라내기, 복사 및 붙여넣기 작업을 위한 명령입니다.|
|IDG_VS_CTXT_PROJECT_PROPERTIES|**프로젝트 속성** 대화 상자에 대 한 액세스를 제공 하는 명령입니다.|

## <a name="see-also"></a>추가 정보

- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [다시 사용할 수 있는 단추 그룹 만들기](../../extensibility/creating-reusable-groups-of-buttons.md)

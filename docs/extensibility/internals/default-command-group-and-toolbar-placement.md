---
title: 기본 명령, 그룹 및 도구 모음 배치 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708887"
---
# <a name="default-command-group-and-toolbar-placement"></a>기본 명령, 그룹 및 도구 모음 배치
제품 균일성 및 안정성을 위해 UI는 기본적으로 특정 명령 그룹을 표시 하 고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령 및 명령 그룹에 대 한 정의를 제공 합니다. Vspackage는 표준 명령과 명령 그룹을 사용할 수도 있습니다.

 기본 명령 그룹은 IDE 명령, 제품 명령 및 편집기 명령 이라는 세 가지 범주로 나뉩니다.

## <a name="default-ide-commands"></a>기본 IDE 명령
 기본 IDE 도구 모음에는에 포함 된 모든 제품에서 공유 하는 명령이 포함 되어 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 여기에는 **저장** 명령과 같은 일반 프로젝트 작업과 관련 된 명령과 **항목 추가** 명령이 포함 됩니다. Vspackage는이 도구 모음에서 추가 하거나 뺄 수 없습니다. 한 가지 예외가 있습니다. product 또는 VSPackage가 새 도구 창을 추가 하는 경우 **보기** 메뉴의 사용 가능한 도구 창 목록에 해당 창이 추가 됩니다. 새 제품 또는 Vspackage 자체 도구 모음을 추가할 수 있습니다.

## <a name="default-product-commands"></a>기본 제품 명령
 각 제품은 중요 하 고 자주 사용 되는 명령을 포함 하는 자체 기본 도구 모음을 IDE에 제공할 수 있습니다. 그러나 가능 하면 기존 메뉴와 도구 모음을 사용 하 고 필요에 따라 다른 작업별 도구 모음을 보완 하는 것이 가장 좋습니다.

 도구 모음의 우선 순위 필드는 행 배치를 결정 합니다. 우선 순위가 0 인 경우 세 번째 행 (행 3)이 메뉴 모음 (행 1)과 **표준** 도구 모음 (2 행) 아래에 배치 됩니다. 따라서 다른 도구 모음은 행 (우선 순위 + 3)에 표시 됩니다. 공간이 있는 경우 후속 도구 모음이 동일한 행에 배치 됩니다. 그렇지 않으면 자동으로 다음 행으로 이동 합니다.

## <a name="default-editor-commands"></a>기본 편집기 명령
 사용자 지정 편집기를 제공 하는 VSPackage는 해당 편집기에서 가장 중요 하 고 자주 사용 되는 명령을 포함 하는 기본 도구 모음을 제공 해야 합니다. 편집기가 활성화 되어 있으면 편집기 도구 모음이 표시 되 고 편집기가 활성화 되어 있지 않으면 숨겨집니다. 이 표시 유형은 `VisibilityConstraints` *. vsct* 파일의 요소에서 제어 됩니다.

 편집기 도구 모음은 IDE 및 제품 도구 모음 아래에 배치 해야 합니다.

## <a name="see-also"></a>추가 정보
- [IDE 정의 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

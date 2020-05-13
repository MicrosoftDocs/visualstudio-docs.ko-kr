---
title: 기본 명령, 그룹 및 도구 모음 배치 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708887"
---
# <a name="default-command-group-and-toolbar-placement"></a>기본 명령, 그룹 및 도구 모음 배치
제품 균일성과 안정성을 위해 UI는 기본적으로 특정 명령 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 그룹을 표시하고 명령 및 명령 그룹에 대한 정의를 제공합니다. VSPackage는 표준 명령 및 명령 그룹을 사용할 수도 있습니다.

 기본 명령 그룹은 IDE 명령, 제품 명령 및 편집기 명령의 세 가지 범주로 나뉩니다.

## <a name="default-ide-commands"></a>기본 IDE 명령
 기본 IDE 도구 모음에는 에 포함된 모든 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]제품에서 공유하는 명령이 포함됩니다. 여기에는 **항목 저장** 명령 및 **항목 추가** 명령과 같은 일반 프로젝트 작업과 관련된 명령이 포함됩니다. VSPackages는 제품 또는 VSPackage가 새 도구 창을 추가하는 경우 **보기** 메뉴에서 사용 가능한 도구 창 목록에 창을 추가하거나 빼지 않아야 합니다. 새 제품 또는 VSPackage는 자체 도구 모음을 추가할 수 있습니다.

## <a name="default-product-commands"></a>기본 제품 명령
 각 제품은 중요하고 자주 사용하는 명령을 포함하는 자체 기본 도구 모음을 IDE에 제공할 수 있습니다. 그러나 가능하면 기존 메뉴와 도구 모음을 사용하고 필요에 따라 다른 작업 별 도구 모음으로 보완하는 것이 가장 좋습니다.

 도구 모음의 우선 순위 필드에 행 배치가 결정됩니다. 우선 순위가 0인 경우 도구 모음이 세 번째 행(행 3)에 메뉴 막대(행 1) 및 **표준** 도구 모음(행 2) 아래에 배치됩니다. 따라서 다른 도구 모음이 행에 나타납니다(우선 순위 + 3). 후속 도구 모음은 공간이 있는 경우 동일한 행에 배치됩니다. 그렇지 않으면 자동으로 다음 행으로 이동됩니다.

## <a name="default-editor-commands"></a>기본 편집기 명령
 사용자 지정 편집기제공 VSPackage는 해당 편집기에서 가장 중요하고 자주 사용되는 명령을 포함하는 기본 도구 모음을 제공해야 합니다. 편집기 도구 모음은 편집기가 활성 상태일 때 나타나야 하며 편집기가 활성화되지 않은 경우 숨춰져야 합니다. 이 가시성은 `VisibilityConstraints` *.vsct* 파일의 요소에서 제어됩니다.

 편집기 도구 모음은 IDE 및 제품 도구 모음 아래에 배치해야 합니다.

## <a name="see-also"></a>참조
- [IDE 정의 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

---
title: 명령 배치 지침 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709564"
---
# <a name="command-placement-guidelines"></a>명령 배치 지침
Visual Studio 통합 개발 환경(IDE)에서 명령을 배치하는 모범 사례는 명령 집합의 크기에 따라 다릅니다. 명령은 *.vsct* 파일의 정보에 따라 정의되고 배치됩니다.

## <a name="best-practices-for-all-command-sets"></a>모든 명령 집합에 대한 모범 사례
 모든 명령 집합에 대해 다음 지침을 따르십시오.

- 명령 구조의 차트를 미리 준비합니다. 두 개 이상의 위치에서 사용할 명령, 콤보 상자, 명령 그룹 및 바로 가기 메뉴를 식별합니다.

- 동일한 그룹에 나타나는 명령은 관련이 있어야 합니다.

- 명령이 하나만 포함된 그룹은 허용됩니다.

- 패키지는 기존 Visual Studio 메뉴에 많은 명령을 추가해서는 안 됩니다. 대신 새 명령을 호스트하는 메뉴 또는 하위 메뉴를 만들어야 합니다.

- 기존 메뉴에 명령을 넣을 때 명령의 용도가 명확하고 기존 명령과 혼동되지 않도록 명령의 이름을 지정합니다.

## <a name="best-practices-for-small-command-sets"></a>작은 명령 집합에 대한 모범 사례
 몇 가지 명령만 있는 VSPackage를 개발하는 경우 다음 지침도 따르십시오.

- 가능하면 명령, 콤보 상자, 그룹 또는 자식 메뉴의 [부모](../../extensibility/parent-element.md) 요소를 사용하여 적절한 그룹에 배치합니다.

- VSPackage에서 표시되는 메뉴에 이러한 그룹을 할당합니다.

- 자식 메뉴 또는 명령의 부모는 [그룹](../../extensibility/group-element.md) 요소여야 합니다. 명령에 하위 메뉴를 그룹에 할당한 다음 상위 메뉴에 그룹을 할당합니다.

- 명령 정의 다음에 [CommandPlacements](../../extensibility/commandplacements-element.md) 요소 섹션을 추가한 다음 각 추가 그룹에 대해 명령 `CommandPlacements` 위치 요소 요소를 요소에 추가하여 추가 그룹에 [명령을](../../extensibility/commandplacement-element.md) 넣을 수 있습니다.

## <a name="best-practices-for-large-command-sets"></a>대규모 명령 집합에 대한 모범 사례
 VSPackage에 여러 컨텍스트에 표시되는 많은 명령이 있는 경우 다음 지침을 따르십시오.

- 메뉴, 그룹 및 명령을 자체 육아로 만듭니다. 즉, 항목 의 정의에 `Parent` 요소를 할당하지 마십시오.

- 요소 `CommandPlacement` 섹션의 `CommandPlacements` 요소 항목을 사용하여 메뉴, 그룹 및 명령을 부모 메뉴 및 그룹에 배치합니다.

- `CommandPlacements` 요소 섹션에서 지정된 메뉴 또는 그룹을 채우는 항목은 서로 인접해야 합니다. 이렇게 하면 가독성이 `Priority` 향상되고 순위를 쉽게 확인할 수 있습니다.

## <a name="see-also"></a>참조
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

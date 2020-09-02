---
title: 명령 배치 지침 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709564"
---
# <a name="command-placement-guidelines"></a>명령 배치 지침
Visual Studio IDE (통합 개발 환경)에서 명령의 위치를 지정 하는 모범 사례는 명령 집합의 크기에 따라 달라 집니다. 명령은 *vsct* 파일의 정보에 따라 정의 되 고 배치 됩니다.

## <a name="best-practices-for-all-command-sets"></a>모든 명령 집합에 대 한 모범 사례
 모든 명령 집합에 대해 다음 지침을 따릅니다.

- 명령 구조의 차트를 미리 준비 합니다. 둘 이상의 위치에서 사용 되는 명령, 콤보 상자, 명령 그룹 및 바로 가기 메뉴를 식별 합니다.

- 동일한 그룹에 나타나는 명령은 서로 관련 되어야 합니다.

- 명령을 하나만 포함 하는 그룹을 사용할 수 있습니다.

- 패키지는 기존 Visual Studio 메뉴에 많은 명령을 추가 하면 안 됩니다. 대신 새 명령을 호스트 하는 메뉴 또는 하위 메뉴를 만들어야 합니다.

- 기존 메뉴에 명령을 넣을 때 해당 용도를 명확 하 게 하 고 기존 명령과 혼동 하지 않도록 명령의 이름을로 바꿉니다.

## <a name="best-practices-for-small-command-sets"></a>작은 명령 집합에 대 한 모범 사례
 몇 가지 명령만 포함 하는 VSPackage를 개발 하는 경우 다음 지침을 따르세요.

- 가능 하면 명령, 콤보 상자, 그룹 또는 자식 메뉴의 [부모](../../extensibility/parent-element.md) 요소를 사용 하 여 해당 그룹에 배치 합니다.

- 이러한 그룹을 VSPackage 표시 되는 메뉴에 할당 합니다.

- 자식 메뉴 또는 명령의 부모는 [그룹](../../extensibility/group-element.md) 요소 여야 합니다. 명령 및 자식 메뉴를 그룹에 할당 한 다음 부모 메뉴에 그룹을 할당 합니다.

- 명령 정의 뒤에 [Commandplacements](../../extensibility/commandplacements-element.md) 요소 섹션을 추가 하 고 `CommandPlacements` 각 추가 그룹에 대해 [commandplacements](../../extensibility/commandplacement-element.md) 요소를 요소에 추가 하 여 명령을 추가 그룹에 배치할 수 있습니다.

## <a name="best-practices-for-large-command-sets"></a>대량 명령 집합에 대 한 모범 사례
 여러 컨텍스트에 표시 될 많은 명령이 VSPackage에 있는 경우 다음 지침을 따르세요.

- 메뉴, 그룹 및 명령을 자체 부모로 만듭니다. 즉, `Parent` 항목 정의에 요소를 할당 하지 마십시오.

- `CommandPlacement`요소 섹션에서 요소 항목을 사용 `CommandPlacements` 하 여 메뉴, 그룹 및 명령을 부모 메뉴 및 그룹에 배치할 수 있습니다.

- `CommandPlacements`요소 섹션에서 지정 된 메뉴 또는 그룹을 채우는 항목이 서로 인접해 야 합니다. 이렇게 하면 가독성을 높이고 `Priority` 순위를 보다 쉽게 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Visual Studio 명령 테이블 (.vvsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

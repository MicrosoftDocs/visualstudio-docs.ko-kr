---
title: 메뉴 및 명령 확장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfcedd3f1b4cb48631541f1726556dab766402ab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711808"
---
# <a name="extend-menus-and-commands"></a>메뉴 및 명령 확장
명령은 Visual Studio에 작업 및 프로세스를 추가하는 방법입니다. 대부분의 경우 명령은 메뉴 또는 도구 모음에 표시됩니다. VSPackage 프로젝트 템플릿은 매우 기본적인 명령을 구현하는 방법을 보여줍니다. 약간 더 길지만 여전히 기본적인 구현의 경우 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

 Visual Studio 명령, 메뉴 및 도구 모음에 대한 자세한 내용은 [명령, 메뉴 및 도구 모음을](../extensibility/internals/commands-menus-and-toolbars.md)참조하십시오.

 명령, 메뉴 및 도구 모음은 VSPackage 프로젝트의 일부인 *.vsct* 파일에 정의됩니다. [VSPackage사용자 인터페이스 요소를 추가하는 방법에서](../extensibility/internals/how-vspackages-add-user-interface-elements.md)Visual Studio IDE 및 *.vsct* 파일에 대한 정보를 찾을 수 있습니다.

 다음 항목에서는 다양한 종류의 명령, 메뉴 및 도구 모음을 추가하는 방법을 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [비주얼 스튜디오 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 상단 의 Visual Studio 메뉴 모음에 메뉴를 추가하는 방법을 설명합니다.

- [키보드 단축키를 메뉴 항목에 바인딩](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) 메뉴 항목에 키보드 단축키(예: CTRL + 3)를 추가하는 방법을 설명합니다.

- [메뉴에 하위 메뉴 추가](../extensibility/adding-a-submenu-to-a-menu.md) 상단 메뉴에 하위 메뉴를 추가하는 방법을 설명합니다.

- [하위 메뉴에 가장 최근에 사용한 목록 추가](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) 가장 최근에 사용한 목록을 추가하는 방법에 대해 설명합니다.

- [재사용 가능한 단추 그룹 만들기](../extensibility/creating-reusable-groups-of-buttons.md) 명령 항목을 여러 메뉴에 포함할 수 있도록 그룹화하는 방법을 설명합니다.

- [메뉴 명령에 아이콘 추가](../extensibility/adding-icons-to-menu-commands.md) 도구 모음과 메뉴 모두에서 명령에 아이콘을 추가하는 방법을 설명합니다.

- [메뉴 명령의 텍스트 변경](../extensibility/changing-the-text-of-a-menu-command.md) 메뉴 항목을 동적으로 `TextChanges` 변경할 수 있도록 플래그를 사용하는 방법을 설명합니다.

- [명령의 모양 변경](../extensibility/changing-the-appearance-of-a-command.md) 명령을 동적으로 활성화하거나 사용하지 않도록 설정하는 방법에 대해 설명합니다.

- [사용자 인터페이스 업데이트](../extensibility/updating-the-user-interface.md) 사용자 인터페이스의 업데이트를 강제로 사용하여 최근 변경 내용을 반영하는 방법을 설명합니다.

- [메뉴 명령 지역화](../extensibility/localizing-menu-commands.md) 메뉴 명령을 지역화하는 방법을 설명합니다.

---
title: 메뉴 및 명령 확장 | Microsoft Docs
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
ms.openlocfilehash: c344d996c70012ef1516fa2bebe52394739bea35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768583"
---
# <a name="extend-menus-and-commands"></a>메뉴 및 명령 확장
명령은 Visual Studio에 작업 및 프로세스를 추가 하는 방법입니다. 대부분의 경우 명령이 메뉴 또는 도구 모음에 표시 됩니다. VSPackage 프로젝트 템플릿은 매우 기본적인 명령을 구현 하는 방법을 보여 줍니다. 약간 더 길고 기본 구현에 대해서는 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

 Visual Studio 명령, 메뉴 및 도구 모음에 대 한 자세한 내용은 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)을 참조 하세요.

 명령, 메뉴 및 도구 모음은 VSPackage 프로젝트의 일부인 *vsct* 파일에 정의 됩니다. [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)에서 VISUAL Studio IDE 및 *vsct* 파일에 대 한 정보를 찾을 수 있습니다.

 다음 항목에서는 다양 한 종류의 명령, 메뉴 및 도구 모음을 추가 하는 방법에 대해 설명 합니다.

## <a name="in-this-section"></a>섹션 내용
- [Visual Studio 메뉴 모음에 메뉴 추가](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) 최상위 Visual Studio 메뉴 모음에 메뉴를 추가 하는 방법을 설명 합니다.

- [메뉴 항목에 바로 가기 키 바인딩](../extensibility/binding-keyboard-shortcuts-to-menu-items.md) 메뉴 항목에 바로 가기 키 (예: CTRL + 3)를 추가 하는 방법을 설명 합니다.

- [메뉴에 하위 메뉴 추가](../extensibility/adding-a-submenu-to-a-menu.md) 최상위 메뉴에 하위 메뉴를 추가 하는 방법을 설명 합니다.

- [가장 최근에 사용한 목록을 하위 메뉴에 추가](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md) 가장 최근에 사용한 목록을 추가 하는 방법에 대해 설명 합니다.

- [다시 사용할 수 있는 단추 그룹 만들기](../extensibility/creating-reusable-groups-of-buttons.md) 여러 메뉴에 포함 될 수 있도록 명령 항목을 그룹화 하는 방법을 설명 합니다.

- [메뉴 명령에 아이콘 추가](../extensibility/adding-icons-to-menu-commands.md) 도구 모음과 메뉴 모두에서 명령에 아이콘을 추가 하는 방법에 대해 설명 합니다.

- [메뉴 명령의 텍스트를 변경 합니다](../extensibility/changing-the-text-of-a-menu-command.md) . 플래그를 사용 하 여 `TextChanges` 메뉴 항목을 동적으로 변경할 수 있도록 하는 방법을 설명 합니다.

- [명령 모양 변경](../extensibility/changing-the-appearance-of-a-command.md) 명령을 동적으로 사용 하거나 사용 하지 않도록 설정 하는 방법을 설명 합니다.

- [사용자 인터페이스 업데이트](../extensibility/updating-the-user-interface.md) 최근 변경 내용을 반영 하기 위해 사용자 인터페이스를 강제로 업데이트 하는 방법을 설명 합니다.

- [메뉴 명령 지역화](../extensibility/localizing-menu-commands.md) 메뉴 명령을 지역화 하는 방법을 설명 합니다.

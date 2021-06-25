---
title: Visual Studio 명령의GUID 및 | Microsoft Docs
description: Visual Studio IDE(통합 개발 환경)에 포함된 명령의 GUID 및 ID 값을 찾는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8442e6430ead8f28d2afc7f51d14968b6999fcd9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898281"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio 명령의GUID 및 ID
Visual Studio IDE(통합 개발 환경)에 포함된 명령의 GUID 및 ID 값은 Visual Studio SDK의 일부로 설치된 .vsct 파일에 정의됩니다. 자세한 내용은 [IDE 정의 명령, 메뉴 및 그룹을 참조하세요.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 *.vsct* 파일에 정의된 IDE 개체로 작업하는 방법에 대한 자세한 내용은 [메뉴 및 명령 확장을 참조하세요.](../../extensibility/extending-menus-and-commands.md)

## <a name="find-a-command-definition"></a>명령 정의 찾기
 Visual Studio 1000개 이상의 명령을 정의하므로 여기에 모두 나열하는 것은 실용적이지 않습니다. 대신 다음 단계에 따라 명령의 정의를 찾습니다.

### <a name="to-locate-a-command-definition"></a>명령 정의를 찾으려면

1. Visual Studio *<Visual Studio SDK 설치 경로 \> \VisualStudioIntegration\Common\Inc \\* 폴더에서 *SharedCmdDef.vsct , ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Edmenu.vsct* 파일을 엽니다. 

    대부분의 Visual Studio 명령은 *SharedCmdDef.vsct* 및 *ShellCmdDef.vsct* 에 정의되어 있습니다. *VsDbgCmdUsed.vsct는* 디버거와 관련된 명령을 정의하고, *Definemenu.vsct는* 웹 개발과 관련된 명령을 정의합니다.

2. 명령이 메뉴 항목인 경우 메뉴 항목의 정확한 텍스트를 기록해 둡다. 명령이 도구 모음의 단추인 경우 일시 중지할 때 나타나는 도구 설명 텍스트를 기록해 둡니다.

3. **Ctrl** + **F를** 눌러 **찾기** 대화 상자를 엽니다.

4. 찾을 **내용** 상자에 2단계에서 적어 두는 텍스트를 입력합니다.

5. 모든 **열린 문서가** 찾는 위치에 표시되는지 **확인합니다.**

6. 단추 요소의 섹션에서 텍스트가 선택될 때까지 **다음 찾기** `<Strings>` [단추를](../../extensibility/button-element.md)클릭합니다.

    `<Button>`명령이 표시되는 요소는 명령 정의입니다.

   명령 정의를 찾은 경우 명령과 동일한 및 값을 가진 [CommandPlacement 요소를](../../extensibility/commandplacement-element.md) 만들어 명령의 복사본을 다른 메뉴 또는 도구 모음에 배치할 수 `guid` `id` 있습니다. 자세한 내용은 [재사용 가능한 단추 그룹 만들기를 참조하세요.](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>특수 사례
 다음 경우 메뉴 텍스트 또는 도구 설명 텍스트가 명령 정의에 있는 텍스트와 정확히 일치하지 않을 수 있습니다.

- *P에* 밑줄이 그어지는 **파일** 메뉴의 **인쇄** 명령과 같이 밑줄이 그어지는 문자를 포함하는 메뉴 항목입니다.

     메뉴 항목 이름에서 앰퍼샌드(&) 문자 앞에 오는 문자는 밑줄로 표시됩니다. 그러나 *.vsct* 파일은 XML로 작성됩니다. 이 XML은 앰퍼샌드(&) 문자를 사용하여 특수 문자를 나타내고 앰퍼샌드를 표시하려면 *&amp; 앰퍼샌드의* 철자를 amp; 로 지정해야 합니다. 따라서 *.vsct* 파일에서 **Print** 명령은 *&amp; 앰프로 표시됩니다. 를 인쇄합니다.*

- **저장과** 같은 동적 \<Current Filename\> 텍스트와 동적으로 생성된 메뉴 항목(예: **최근 파일** 목록의 항목)이 있는 명령입니다.

     동적 텍스트를 검색하는 신뢰할 수 있는 방법은 없습니다. 대신 Visual Studio [메뉴의GUID 및](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ID 또는 Visual Studio [도구 모음의 ID와](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)ID를 참조하여 원하는 명령을 호스트하는 그룹을 찾고 해당 그룹의 ID를 검색합니다. 명령 정의에 [해당 Parent 요소로](../../extensibility/parent-element.md)그룹이 없는 경우 명령의 부모를 설정하는 요소에 대해 *SharedCmdPlace.vsct* 및 *ShellCmdPlace.vsct(또는* 디버거 명령의 경우 *VsDbgCmdPlace.vsct)를* 검색합니다. `<CommandPlacement>` *SharedCmdPlace.vsct,* *ShellCmdPlace.vsct* 및 *VsDbgCmdPlace.vsct는* *\<Visual Studio SDK installation path\> \VisualStudioIntegration\Common\Inc \\* 폴더에 있습니다.

## <a name="see-also"></a>참조

- [Visual Studio 명령 테이블(.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)

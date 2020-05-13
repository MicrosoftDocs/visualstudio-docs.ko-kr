---
title: 비주얼 스튜디오 명령의 GUID 및 아이디 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708248"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>비주얼 스튜디오 명령의 GUID 및 아이디
Visual Studio 통합 개발 환경(IDE)에 포함된 명령의 GUID 및 ID 값은 Visual Studio SDK의 일부로 설치된 .vsct 파일에 정의되어 있습니다. 자세한 내용은 [IDE 정의 명령, 메뉴 및 그룹을](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)참조하십시오.

 *.vsct* 파일에 정의된 IDE 개체로 작업하는 방법에 대한 자세한 내용은 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)을 참조하십시오.

## <a name="find-a-command-definition"></a>명령 정의 찾기
 Visual Studio는 1000개 이상의 명령을 정의하므로 여기에 모두 나열하는 것은 비실용적입니다. 대신 다음 단계를 수행하여 명령의 정의를 찾습니다.

### <a name="to-locate-a-command-definition"></a>명령 정의를 찾으려면

1. 비주얼 스튜디오에서, *<비주얼 스튜디오 SDK 설치 경로에서\>다음 파일을 엽니\\ 다 VisualStudioIntegration\Common\Inc* 폴더: *SharedCmdDef.vsct,* *ShellCmdDef.vsct,* *VsDbgCmdUsed.vsct,* *Venusmenu.vsct*.

    대부분의 비주얼 스튜디오 명령은 *SharedCmdDef.vsct* 및 *ShellCmdDef.vsct에*정의되어 있습니다. *VsDbgCmdUsed.vsct는* 디버거와 관련된 명령을 *정의하고, Venusmenu.vsct는* 웹 개발과 관련된 명령을 정의합니다.

2. 명령이 메뉴 항목인 경우 메뉴 항목의 정확한 텍스트를 기록합니다. 명령이 도구 모음의 단추인 경우 일시 중지할 때 나타나는 도구 설명 텍스트를 기록합니다.

3. **Ctrl**+**F를** 눌러 대화 **상자 찾기를** 엽니다.

4. 어떤 상자 **찾기에서** 2단계에서 언급한 텍스트를 입력합니다.

5. 열려 있는 **모든 문서가** **보기** 상자에 표시되는지 확인합니다.

6. [단추 요소의](../../extensibility/button-element.md)섹션에서 텍스트가 선택될 `<Strings>` 때까지 다음 **찾기** 단추를 클릭합니다.

    명령이 표시되는 `<Button>` 요소는 명령 정의입니다.

   명령 정의를 찾은 경우 명령과 동일한 `guid` `id` 값을 가진 [CommandPlacement 요소를](../../extensibility/commandplacement-element.md) 만들어 다른 메뉴 또는 도구 모음에 명령의 복사본을 넣을 수 있습니다. 자세한 내용은 [재사용 가능한 단추 그룹 만들기를](../../extensibility/creating-reusable-groups-of-buttons.md)참조하십시오.

### <a name="special-cases"></a>특수 사례
 다음 경우 메뉴 텍스트 또는 도구 설명 텍스트가 명령 정의에 있는 텍스트와 정확히 일치하지 않을 수 있습니다.

- **파일** 메뉴의 **인쇄** 명령과 같이 밑줄이 그어진 문자가 포함된 메뉴 항목으로, *P에* 밑줄이 그어져 있습니다.

     메뉴 항목 이름의 앰퍼샌드(&) 문자 앞에 오는 문자는 밑줄로 표시됩니다. 그러나 *.vsct* 파일은 앰퍼샌드 (&) 문자를 사용하여 특수 문자를 나타내기 위해 XML로 작성되며 앰퍼샌드를 * &amp;표시해야합니다.* 따라서 *.vsct* 파일에서 **인쇄** * &amp;명령이 amp로 나타납니다. 인쇄합니다.*

- 현재 파일 이름\> **저장과** \<같은 동적 텍스트가 있는 명령과 **최근 파일** 목록의 항목과 같이 동적으로 생성된 메뉴 항목입니다.

     동적 텍스트를 검색하는 신뢰할 수 있는 방법은 없습니다. 대신 Visual Studio 메뉴 또는 GUID 및 Visual Studio 도구 [모음의 GUID 및](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) ID를 참조하여 원하는 명령을 [호스팅하는](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)그룹을 찾아 해당 그룹의 ID를 검색합니다. 명령 정의에 [그룹이 상위 요소로](../../extensibility/parent-element.md)없는 경우 명령의 부모를 설정하는 `<CommandPlacement>` 요소에 대해 *SharedCmdPlace.vsct* 및 *ShellCmdPlace.vsct(또는* 디버거 명령에 대한 *VsDbgCmdPlace.vsct)를* 검색합니다. *SharedCmdPlace.vsct,* *ShellCmdPlace.vsct*및 *VsDbgCmdPlace.vsct는* * \<비주얼 스튜디오 SDK 설치 경로\>\VisualStudioIntegration\Common\Inc\\ * 폴더에 있습니다.

## <a name="see-also"></a>참조

- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)

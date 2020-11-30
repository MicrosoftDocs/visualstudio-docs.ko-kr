---
title: XML 명령 테이블을 디자인 합니다. Vsct) 파일 | Microsoft Docs
description: 단추, 콤보 상자, 메뉴 및 도구 모음을 포함 하 여 명령 항목의 레이아웃과 모양을 설명 하는 XML 명령 테이블 (.vvsct) 파일을 디자인 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1ccab1eddf38e2f93cb00f1f5fdea6ce09f2f05
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328433"
---
# <a name="design-xml-command-table-vsct-files"></a>XML 명령 테이블 (.vvsct) 파일 디자인
XML 명령 테이블 (*.vvsct*) 파일은 VSPackage에 대 한 명령 항목의 레이아웃과 모양을 설명 합니다. 명령 항목에는 단추, 콤보 상자, 메뉴, 도구 모음 및 명령 항목 그룹이 있습니다. 이 문서에서는 XML 명령 테이블 파일, 명령 항목 및 메뉴에 영향을 주는 방법 및 해당 파일을 만드는 방법을 설명 합니다.

## <a name="commands-menus-groups-and-the-vsct-file"></a>명령, 메뉴, 그룹 및. vsct 파일
 *. Vsct* 파일은 명령, 메뉴 및 명령 그룹을 중심으로 구성 됩니다. *. Vsct* 파일의 XML 태그는 명령 단추, 명령 배치 및 비트맵과 같은 연결 된 다른 항목과 함께 이러한 각 항목을 나타냅니다.

 패키지 템플릿을 실행 하 여 새 VSPackage를 만드는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 선택한 항목에 따라 템플릿에서 메뉴 명령, 도구 창 또는 사용자 지정 편집기에 필요한 요소를 포함 하는 *vsct* 파일을 생성 합니다. 그런 *다음이 파일* 을 수정 하 여 특정 VSPackage의 요구 사항을 충족할 수 있습니다. *. Vsct* 파일을 수정 하는 방법에 대 한 예제는 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)을 참조 하세요.

 비어 있는 새 *vsct* 파일을 만들려면 [방법: *vsct* 파일 만들기](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)를 참조 하세요. 만든 후에는 XML 요소, 특성 및 값을 파일에 추가 하 여 명령 항목 레이아웃을 설명 합니다. 자세한 XML 스키마는 [Vsct xml 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)를 참조 하세요.

## <a name="differences-between-ctc-and-vsct-files"></a>Ctc와 .vsct 파일의 차이점
 *.Cvsct* 파일의 XML 태그 뒤에 있는 의미는 현재 사용 되지 않는 *. ctc* 파일 형식의 태그와 동일 하지만 해당 구현은 약간 다릅니다.

- 새 **\<extern>** 태그는 도구 모음에 대 한 파일과 같이 컴파일할 다른 *.h* 파일을 참조 하는 위치입니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

- *Vsct* 파일은 **/include** 문을 지원 하지만 *ctc* 파일은 새 요소를 갖추고 있습니다. **\<import>** 차이점은 **/include** 는 *모든* 정보를 제공 하는 반면는 이름만을 가져오는 것입니다 **\<import>** .

- 그러나 *ctc* 파일에는 전처리기 지시문을 정의 하는 헤더 파일이 필요 합니다. *vsct* 파일에는 필요 하지 않습니다. 대신, **\<Symbol>** *vsct* 파일의 아래쪽에 있는 요소에 있는 기호 테이블에 지시문을 배치 합니다.

- *. vsct* 파일은 **\<Annotation>** 메모 또는 심지어 사진과 같이 원하는 정보를 포함할 수 있는 태그입니다.

- 값은 항목의 특성으로 저장 됩니다.

- 명령 플래그는 개별적으로 또는 누적 되어 저장할 수 있습니다.  그러나 IntelliSense는 누적 명령 플래그에서 작동 하지 않습니다. 명령 플래그에 대 한 자세한 내용은 [Commandflag 요소](../../extensibility/command-flag-element.md)를 참조 하세요.

- 분할 드롭다운, combos 등의 여러 형식을 지정할 수 있습니다.

- Guid는 유효성을 검사 하지 않습니다.

- 각 UI 요소는 표시 되는 텍스트를 나타내는 문자열을 포함 합니다.

- 부모는 선택 사항입니다. 생략 하면 *Unknown 값 그룹이* 사용 됩니다.

- *Icon* 인수는 선택 사항입니다.

- Bitmap 섹션:이 섹션은 *.ctc* 파일의 경우와 동일 합니다. 단, 이제 컴파일 시간에 *vsct.exe* 컴파일러가 가져올 Href를 통해 파일 이름을 지정할 수 있습니다.

- Resid로: 이전 비트맵 리소스 ID를 사용할 수 있으며,이 ID는 *.ctc* 파일의 경우와 동일 하 게 작동 합니다.

- HRef: 비트맵 리소스의 파일 이름을 지정할 수 있도록 하는 새 메서드입니다. 사용 되는 것으로 가정 하므로 사용 된 섹션을 생략할 수 있습니다. 컴파일러는 먼저 파일에 대 한 로컬 리소스를 검색 한 다음 모든 net 공유 및 **/i** 스위치로 정의한 모든 리소스를 검색 합니다.

- Keybinding: 더 이상 에뮬레이터를 지정할 필요가 없습니다. 이를 지정 하는 경우 컴파일러는 편집기와 에뮬레이터가 동일한 것으로 가정 합니다.

- Keychord: Keychord가 삭제 되었습니다. 새 형식은 *Key1, Mod1, Key2, Mod2* 입니다.  문자, 16 진수 또는 VK 상수를 지정할 수 있습니다.

새 컴파일러 *vsct.exe* 는 *ctc* 및 *.cvsct* 파일을 모두 컴파일합니다. 그러나 이전 *ctc.exe* 컴파일러는 *vsct* 파일을 인식 하거나 컴파일하지 않습니다.

*vsct.exe* 컴파일러를 사용 하 여 기존 *.cto* 파일을 *.vsct* 파일로 변환할 수 있습니다. 자세한 내용은 [방법: 기존. cto 파일에서 .vsct 파일 만들기](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)를 참조 하세요.

## <a name="the-vsct-file-elements"></a>. Vsct 파일 요소
 명령 테이블에는 다음과 같은 계층 구조 및 요소가 있습니다.

- [Commandtable 요소](../../extensibility/commandtable-element.md): VSPackage와 연결 된 모든 명령, 메뉴 그룹 및 메뉴를 나타냅니다.

- [Extern 요소](../../extensibility/extern-element.md): *. vsct* 파일과 병합 하려는 외부 .h 파일을 참조 합니다.

- [Include 요소](../../extensibility/include-element.md): *. vsct* 파일과 함께 컴파일하려는 추가 헤더 파일 (.h)을 참조 합니다. *. Vsct* 파일은 IDE 또는 다른 VSPackage에서 제공 하는 명령, 메뉴 그룹 및 메뉴를 정의 하는 상수를 포함 하는 *.h* 파일을 포함할 수 있습니다.

- [Commands 요소](../../extensibility/commands-element.md): 실행할 수 있는 모든 개별 명령을 나타냅니다. 각 명령에는 다음과 같은 네 개의 자식 요소가 있습니다.

- [Menus 요소](../../extensibility/menus-element.md): VSPackage의 모든 메뉴와 도구 모음을 나타냅니다. 메뉴는 명령 그룹의 컨테이너입니다.

- [Groups 요소](../../extensibility/groups-element.md): VSPackage의 모든 그룹을 나타냅니다. 그룹은 개별 명령의 모음입니다.

- [Buttons 요소](../../extensibility/buttons-element.md): VSPackage의 모든 명령 단추 및 메뉴 항목을 나타냅니다. 단추는 명령에 연결할 수 있는 시각적 컨트롤입니다.

- [비트맵 요소](../../extensibility/bitmaps-element.md): VSPackage 모든 단추의 모든 비트맵을 나타냅니다. 비트맵은 컨텍스트에 따라 명령 단추 옆에 표시 되는 그림입니다.

- [Commandplacements 요소](../../extensibility/commandplacements-element.md): VSPackage의 메뉴에 개별 명령을 배치 해야 하는 추가 위치를 나타냅니다.

- [VisibilityConstraints 요소](../../extensibility/visibilityconstraints-element.md): 명령이 항상 표시 되는지 아니면 특정 대화 상자 또는 창이 표시 되는 경우와 같은 특정 컨텍스트에서만 표시 되는지를 지정 합니다. 이 요소에 대 한 값이 있는 메뉴와 명령은 지정 된 컨텍스트가 활성 상태인 경우에만 표시 됩니다. 기본 동작은 항상 명령을 표시 하는 것입니다.

- [KeyBindings 요소](../../extensibility/keybindings-element.md): 명령의 키 바인딩을 지정 합니다. 즉, **Ctrl** S와 같이 명령을 실행 하기 위해 눌러야 하는 키 조합이 하나 이상 + **S** 있습니다.

- [UsedCommands 요소](../../extensibility/usedcommands-element.md): 지정 된 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령이 다른 코드에 의해 구현 되더라도 현재 VSPackage 활성 상태인 경우 명령 구현을 제공 한다는 것을 환경에 알립니다.

- [기호 요소](../../extensibility/symbols-element.md): 패키지의 모든 명령에 대 한 기호 이름 및 GUID id를 포함 합니다.

## <a name="vsct-file-design-guidelines"></a>. vsct 파일 디자인 지침
 *Vsct* 파일을 성공적으로 디자인 하려면 다음 지침을 따르세요.

- 명령은 그룹에만 배치할 수 있으며 그룹은 메뉴에만 배치할 수 있으며 메뉴는 그룹에만 배치할 수 있습니다. 메뉴만 실제로 IDE에 표시 되 고 그룹 및 명령은 표시 되지 않습니다.

- 하위 메뉴를 메뉴에 직접 할당할 수는 없지만 그룹에 할당 해야 합니다. 그러면 메뉴에 할당 됩니다.

- 명령, 하위 메뉴 및 그룹은 정의 지시문의 부모 필드를 사용 하 여 하나의 부모 그룹이 나 메뉴에 할당할 수 있습니다.

- 지시문의 부모 필드를 통해서만 명령 테이블을 구성 하는 경우에는 상당한 제한이 있습니다. 개체를 정의 하는 지시문은 부모 인수를 하나만 사용할 수 있습니다.

- 명령, 그룹 또는 하위 메뉴를 다시 사용 하려면 새 지시문을 사용 하 여 고유한 쌍으로 개체의 새 인스턴스를 만들어야 합니다 `GUID:ID` .

- 각 `GUID:ID` 쌍은 고유 해야 합니다. 예를 들어, 메뉴, 도구 모음 또는 상황에 맞는 메뉴에 있는 명령 재사용은 인터페이스에 의해 처리 됩니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- 명령 및 하위 메뉴는 여러 그룹에 할당 될 수도 있으며 [commands 요소](../../extensibility/commands-element.md)를 사용 하 여 여러 메뉴에 그룹을 할당할 수 있습니다.

## <a name="vsct-file-notes"></a>. vsct 파일 정보
 모든 파일을 컴파일하고 네이티브 위성 DLL에 배치한 후에 *vsct* 파일을 변경 하는 경우 **devenv.exe/s/nosetupvstemplates** 을 실행 해야 합니다. 이렇게 하면 실험적 레지스트리에 지정 된 VSPackage 리소스를 다시 읽을 수 있으며,이를 설명 하는 내부 데이터베이스를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다시 작성할 수 있습니다.

 개발 중에 IDE에서 혼란 스 러 울 수 있는 실험적 레지스트리 하이브에 여러 VSPackage 프로젝트를 만들고 등록할 수 있습니다. 이 문제를 해결 하려면 실험적 hive를 기본 설정으로 다시 설정 하 여 등록 된 모든 Vspackage 및 IDE에 적용 되었을 수 있는 모든 변경 내용을 제거 합니다. 실험적 hive를 다시 설정 하려면 Visual Studio SDK와 함께 제공 되는 CreateExpInstance.exe 도구를 사용 합니다. 다음 위치에서 찾을 수 있습니다.

 *% PROGRAMFILES (x86)% \ Visual Studio \\ \<version> SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe*

 **Createexpinstance/Reset** 명령을 사용 하 여 도구를 실행 합니다. 이 도구는 일반적으로와 함께 설치 되지 않은 모든 등록 된 Vspackage를 실험적 hive에서 제거 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>참조
- [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)

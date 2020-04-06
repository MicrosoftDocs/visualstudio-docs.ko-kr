---
title: XML 명령 테이블 디자인(. Vsct) 파일 | 마이크로 소프트 문서
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
ms.openlocfilehash: fcd29aee98139bb151c87590b256df6b8370abff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708747"
---
# <a name="design-xml-command-table-vsct-files"></a>XML 명령 테이블(.vsct) 파일 디자인
XML 명령 테이블 *(.vsct)* 파일은 VSPackage에 대한 명령 항목의 레이아웃과 모양을 설명합니다. 명령 항목에는 단추, 콤보 상자, 메뉴, 도구 모음 및 명령 항목 그룹이 포함됩니다. 이 문서에서는 XML 명령 테이블 파일, 명령 항목 및 메뉴에 미치는 영향 및 파일을 만드는 방법에 대해 설명합니다.

## <a name="commands-menus-groups-and-the-vsct-file"></a>명령, 메뉴, 그룹 및 .vsct 파일
 *.vsct* 파일은 명령, 메뉴 및 명령 그룹을 중심으로 구성됩니다. *.vsct* 파일의 XML 태그는 명령 단추, 명령 배치 및 비트맵과 같은 다른 관련 항목과 함께 이러한 각 항목을 나타냅니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 패키지 템플릿을 실행하여 새 VSPackage를 만들 때 템플릿은 선택 항목에 따라 메뉴 명령, 도구 창 또는 사용자 지정 편집기에 필요한 요소가 있는 *.vsct* 파일을 생성합니다. 이 *.vsct* 파일은 특정 VSPackage의 요구 사항을 충족하도록 수정할 수 있습니다. *.vsct* 파일을 수정하는 방법의 예는 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)을 참조하십시오.

 빈 *.vsct* 새 파일을 만들려면 [ *.vsct* 파일 만들기 방법을 참조하세요.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md) 생성되면 명령에 따라 항목 레이아웃을 설명하기 위해 파일에 XML 요소, 특성 및 값을 추가합니다. 자세한 XML 스키마는 [VSCT XML 스키마 참조를](../../extensibility/vsct-xml-schema-reference.md)참조하십시오.

## <a name="differences-between-ctc-and-vsct-files"></a>.ctc 파일과 .vsct 파일 간의 차이점
 *.vsct* 파일의 XML 태그 뒤에 있는 의미는 현재 사용되지 않는 *.ctc* 파일 형식의 태그와 동일하지만 구현은 약간 다릅니다.

- 새로운 ** \<extern>** 태그는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 도구 모음에 대한 해당 파일과 같이 컴파일할 다른 *.h* 파일을 참조하는 곳입니다.

- *.vsct 파일은* *.ctc* 파일처럼 **/include** 문을 지원하지만 새 ** \<가져오기>** 요소도 있습니다. 차이점은 **/include** *모든* 정보를 가져오고 ** \<가져오기>** 이름만 가져온다는 것입니다.

- *.ctc* 파일에는 사전 처리기 지시문을 정의하는 헤더 파일이 필요하지만 *.vsct* 파일에는 필요하지 않습니다. 대신 *.vsct* 파일 의 맨 아래에 있는 ** \<기호>** 요소에 있는 기호 테이블에 지시문을 배치합니다.

- *.vsct* 파일에는 ** \<메모나** 사진과 같이 원하는 정보를 포함할 수>태그가 있습니다.

- 값은 항목에 특성으로 저장됩니다.

- 명령 플래그는 개별적으로 저장하거나 누적할 수 있습니다.  그러나 IntelliSense는 누적된 명령 플래그에서 작동하지 않습니다. 명령 플래그에 대한 자세한 내용은 [CommandFlag 요소를](../../extensibility/command-flag-element.md)참조하십시오.

- 분할 드롭다운, 콤보 등과 같은 여러 유형을 지정할 수 있습니다.

- GUID는 유효성을 검사하지 않습니다.

- 각 UI 요소에는 함께 표시되는 텍스트를 나타내는 문자열이 있습니다.

- 부모는 선택 사항입니다. 생략된 경우 *알 수 없는* 값이 사용됩니다.

- *아이콘* 인수는 선택 사항입니다.

- 비트맵 섹션: 이 섹션은 *.ctc* 파일과 동일하지만 컴파일 타임에 *vsct.exe* 컴파일러에서 끌어올 Href를 통해 파일 이름을 지정할 수 있습니다.

- ResID: 이전 비트맵 리소스 ID를 사용할 수 있으며 *.ctc* 파일과 동일하게 작동합니다.

- HRef: 비트맵 리소스에 대한 파일 이름을 지정할 수 있는 새 메서드입니다. 모두 사용된다고 가정하므로 Used 섹션을 생략할 수 있습니다. 컴파일러는 먼저 파일에 대한 로컬 리소스를 검색한 다음 모든 순 공유 및 **/I** 스위치에 의해 정의된 모든 리소스를 검색합니다.

- 키 바인딩: 더 이상 에뮬레이터를 지정할 필요가 없습니다. 하나를 지정하면 컴파일러는 편집기와 에뮬레이터가 동일하다고 가정합니다.

- 키코드: 키코드가 삭제되었습니다. 새로운 형식은 *Key1, Mod1, Key2, Mod2입니다.*  문자, 육각형 또는 VK 상수를 지정할 수 있습니다.

새 컴파일러 *인 vsct.exe는* *.ctc* 및 *.vsct* 파일을 모두 컴파일합니다. 그러나 이전 *ctc.exe* 컴파일러는 *.vsct* 파일을 인식하거나 컴파일하지 않습니다.

*vsct.exe* 컴파일러를 사용하여 기존 *.cto* 파일을 *.vsct* 파일로 변환할 수 있습니다. 자세한 내용은 [기존 .cto 파일에서 .vsct 파일 만들기 방법을 참조하세요.](../../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)

## <a name="the-vsct-file-elements"></a>.vsct 파일 요소
 명령 테이블에는 다음과 같은 계층 구조 및 요소가 있습니다.

- [명령 테이블 요소](../../extensibility/commandtable-element.md): VSPackage와 연결된 모든 명령, 메뉴 그룹 및 메뉴를 나타냅니다.

- [Extern 요소](../../extensibility/extern-element.md): *.vsct* 파일과 병합하려는 외부 .h 파일을 참조합니다.

- [요소 포함](../../extensibility/include-element.md): *.vsct* 파일과 함께 컴파일할 추가 헤더(.h) 파일을 참조합니다. *.vsct* 파일에는 IDE 또는 다른 VSPackage에서 제공하는 명령, 메뉴 그룹 및 메뉴를 정의하는 상수가 포함된 *.h* 파일이 포함될 수 있습니다.

- [명령 요소](../../extensibility/commands-element.md): 실행할 수 있는 모든 개별 명령을 나타냅니다. 각 명령에는 다음과 같은 네 가지 자식 요소가 있습니다.

- [메뉴 요소](../../extensibility/menus-element.md): VSPackage의 모든 메뉴 및 도구 모음을 나타냅니다. 메뉴는 명령 그룹에 대한 컨테이너입니다.

- [그룹 요소](../../extensibility/groups-element.md): VSPackage의 모든 그룹을 나타냅니다. 그룹은 개별 명령의 컬렉션입니다.

- [단추 요소](../../extensibility/buttons-element.md): VSPackage의 모든 명령 단추 및 메뉴 항목을 나타냅니다. 단추는 명령과 연결할 수 있는 시각적 컨트롤입니다.

- [비트맵 요소](../../extensibility/bitmaps-element.md): VSPackage의 모든 단추에 대한 모든 비트맵을 나타냅니다. 비트맵은 컨텍스트에 따라 명령 단추 옆이나 위에 표시되는 그림입니다.

- [명령 위치 요소](../../extensibility/commandplacements-element.md): 개별 명령이 VSPackage의 메뉴에 배치되어야 하는 추가 위치를 나타냅니다.

- 가시성 제약 요소 : 명령이 항상 표시되는지 또는 특정 대화 상자 나 창이 표시되는 경우와 같은 특정 컨텍스트에서만 표시할지 여부를 [지정합니다.](../../extensibility/visibilityconstraints-element.md) 이 요소에 대한 값이 있는 메뉴 및 명령은 지정된 컨텍스트가 활성 상태일 때만 표시됩니다. 기본 동작은 항상 명령을 표시하는 것입니다.

- [키 바인딩 요소](../../extensibility/keybindings-element.md): 명령에 대한 모든 키 바인딩을 지정합니다. 즉, **Ctrl**+**S와**같은 명령을 실행하기 위해 누를 필요가 있는 하나 이상의 키 조합입니다.

- [UsedCommands 요소](../../extensibility/usedcommands-element.md): [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 지정된 명령이 다른 코드에 의해 구현되지만 현재 VSPackage가 활성 상태일 때 명령 구현을 제공한다는 것을 환경에 알립니다.

- [기호 요소](../../extensibility/symbols-element.md): 패키지의 모든 명령에 대한 기호 이름과 GUID ID를 포함합니다.

## <a name="vsct-file-design-guidelines"></a>.vsct 파일 디자인 지침
 *.vsct* 파일을 성공적으로 디자인하려면 다음 지침을 따르십시오.

- 명령은 그룹에만 배치할 수 있으며, 그룹은 메뉴에만 배치할 수 있으며 메뉴는 그룹으로만 배치할 수 있습니다. 메뉴만 실제로 IDE에 표시되며 그룹 및 명령은 표시되지 않습니다.

- 하위 메뉴는 메뉴에 직접 할당할 수 없지만 그룹에 할당되어야 하며, 이 메뉴는 메뉴에 할당됩니다.

- 명령, 하위 메뉴 및 그룹은 정의 지시의 부모 필드를 사용하여 하나의 상위 그룹 또는 메뉴에 할당할 수 있습니다.

- 지시문의 부모 필드를 통해서만 명령 테이블을 구성하는 것은 상당한 제한이 있습니다. 개체를 정의하는 지시문은 하나의 부모 인수만 사용할 수 있습니다.

- 명령, 그룹 또는 하위 메뉴를 다시 사용하려면 새 지시문을 사용하여 자체 `GUID:ID` 쌍으로 개체의 새 인스턴스를 만들어야 합니다.

- 각 `GUID:ID` 쌍은 고유해야 합니다. 예를 들어 메뉴, 도구 모음 또는 컨텍스트 메뉴에 배치된 명령을 다시 사용하는 것은 인터페이스에서 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 처리됩니다.

- 명령 및 하위 메뉴를 여러 그룹에 할당할 수도 있으며 명령 요소를 사용하여 여러 메뉴에 그룹을 할당할 수 [있습니다.](../../extensibility/commands-element.md)

## <a name="vsct-file-notes"></a>.vsct 파일 노트
 .vsct 파일을 모두 컴파일하고 네이티브 위성 DLL에 배치한 후 *변경한* 경우 **devenv.exe /setup /nosetupvstemplates를**실행해야 합니다. 이렇게 하면 실험 레지스트리에 지정된 VSPackage 리소스를 다시 읽고 다시 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 빌드할 내부 데이터베이스를 강제로 다시 읽습니다.

 개발 하는 동안 여러 VSPackage 프로젝트를 만들고 IDE에 혼란 혼란으로 이어질 수 있는 실험 레지스트리 하이브에 등록 될 수 있습니다. 이 문제를 해결하려면 실험 하이브를 기본 설정으로 재설정하여 등록된 모든 VSPackage 및 IDE에 변경한 내용을 제거할 수 있습니다. 실험용 하이브를 재설정하려면 Visual Studio SDK와 함께 제공되는 CreateExpInstance.exe 도구를 사용합니다. 다음에서 찾을 수 있습니다.

 *%PROGRAMFILES(x86)%\비주얼\\\<스튜디오 버전> SDK\VisualStudio통합\도구\빈\CreateExpInstance.exe*

 **CreateExpInstance /재설정**명령을 사용하여 도구를 실행합니다. 이 도구는 일반적으로 설치되지 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]않은 등록된 모든 VSPackage를 실험 하이브에서 제거합니다.

## <a name="see-also"></a>참조
- [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)

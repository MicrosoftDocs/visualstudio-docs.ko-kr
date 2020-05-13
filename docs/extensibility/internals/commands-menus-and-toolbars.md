---
title: 명령, 메뉴 및 도구 모음 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709498"
---
# <a name="commands-menus-and-toolbars"></a>명령, 메뉴 및 도구 모음
메뉴 및 도구 모음은 사용자가 VSPackage에서 명령에 액세스하는 방법입니다. 명령은 문서 인쇄, 보기 새로 고침 또는 새 파일 만들기 등의 작업을 수행하는 함수입니다. 메뉴 및 도구 모음은 사용자에게 명령을 제공하는 편리한 그래픽 방법입니다. 일반적으로 관련 명령은 동일한 메뉴 또는 도구 모음에 함께 클러스터됩니다.

- 메뉴는 일반적으로 IDE(통합 개발 환경) 또는 도구 창의 맨 위에 한 단어 문자열이 연속으로 클러스터되어 표시됩니다. 메뉴를 마우스 오른쪽 단추 클릭 이벤트의 결과로 표시할 수도 있으며, 해당 컨텍스트에서는 바로 가기 메뉴라고 합니다. 클릭하면 메뉴가 확장되어 하나 이상의 명령을 표시합니다. 명령을 클릭하여 작업을 수행하거나 추가 명령이 포함된 하위 메뉴를 시작할 수 있습니다. 일부 잘 알려진 메뉴 이름은 **파일,** **편집,** **보기**및 **창**입니다. 자세한 내용은 [메뉴 및 명령 확장](../../extensibility/extending-menus-and-commands.md)을 참조하십시오.

- 일반적으로 도구 모음은 단추와 콤보 상자, 목록 상자, 텍스트 상자 및 메뉴 컨트롤러와 같은 다른 컨트롤의 행입니다. 모든 도구 모음 컨트롤은 명령과 연결됩니다. 도구 모음 단추를 클릭하면 연결된 명령이 활성화됩니다. 인쇄 명령의 프린터와 같이 일반적으로 도구 모음 단추에는 기본 명령을 나타내는 아이콘이 있습니다. 드롭다운 목록 컨트롤에서 목록의 각 항목은 다른 명령과 연결됩니다. 메뉴 컨트롤러는 컨트롤의 한 쪽은 도구 모음 단추이고 다른 쪽은 클릭할 경우 추가 명령을 표시하는 아래쪽 화살표인 하이브리드입니다. 자세한 내용은 [도구 모음에 메뉴 컨트롤러 추가를](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)참조하십시오.

- 명령을 만드는 경우 해당 이벤트 처리기도 만들어야 합니다. 이벤트 처리기는 명령이 표시되거나 사용할 수 있는 경우를 결정하며, 해당 텍스트를 수정할 수 있게 하고, 활성화된 경우 명령이 적절히 응답("라우팅")하도록 합니다. 대부분의 경우 IDE는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 사용하여 명령을 처리합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 의 명령은 로컬 선택 기반의 가장 안쪽의 명령 컨텍스트부터 전역 선택 기반의 가장 바깥쪽 컨텍스트로 진행하는 계층적 방식으로 라우팅합니다. 주 메뉴에 추가된 명령은 즉시 스크립팅에 사용할 수 있습니다. 자세한 내용은 [메뉴 명령 및 OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015) 및 선택 컨텍스트 [개체를](../../extensibility/internals/selection-context-objects.md)참조하십시오.

  새 메뉴와 도구 모음을 정의하려면 Visual Studio 명령*테이블(.vsct)* 파일에서 설명해야 합니다. Visual Studio 패키지 템플릿은 템플릿에서 선택한 명령, 도구 모음 및 편집기를 지원하는 데 필요한 요소와 함께 이 파일을 만듭니다. 또는 여기에 설명된 XML 스키마를 사용하여 *고유한 .vsct* 파일을 [VSCT XML schema reference](../../extensibility/vsct-xml-schema-reference.md)작성할 수 있습니다.

  *.vsct* 파일 작업에 대한 자세한 내용은 [Visual Studio 명령 테이블(.vsct) 파일을](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)참조하십시오.

  이 섹션의 항목에서는 VSPackage에서 명령, 메뉴 및 도구 모음이 작동하는 방법을 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 명령 테이블 형식 사양에 대한 자세한 설명입니다.

- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 명령 테이블에 대한 XML 기반 구문 및 컴파일러에 대해 설명합니다.

- [기본 명령, 그룹 및 도구 모음 배치](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 미리 정의된 명령, 그룹, 메뉴 및 도구 모음에 대해 설명합니다.

- [IDE 정의 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에서 사용할 수 있는 미리 정의된 메뉴, 명령 및 명령 그룹을 지정합니다.

- [명령 디자인](../../extensibility/internals/command-design.md)

 명령을 디자인하는 방법을 설명합니다.

- [메뉴 및 도구 모음 명령 최적화](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 명령에 대한 지침을 제공합니다.

- [명령을 사용할 수 있도록 만들기](../../extensibility/internals/making-commands-available.md)

 Visual Studio에서 명령을 사용할 수 있도록 하는 방법을 설명합니다.

- [interop 어셈블리를 사용하는 명령 및 메뉴](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 interop 어셈블리를 사용하는 명령을 구현하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
- [VS패키지의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)

 VSPackage에서 명령 라우팅을 설명합니다.

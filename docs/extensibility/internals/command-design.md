---
title: 명령 디자인 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6aa58813623dc8150cafb4fbfee6496d09f889ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709657"
---
# <a name="command-design"></a>명령 디자인
VSPackage에 명령을 추가할 때 는 표시 위치, 사용 가능한 시기 및 처리 방법을 지정해야 합니다.

## <a name="define-commands"></a>명령 정의
 새 명령을 정의하려면 VSPackage 프로젝트에 Visual Studio 명령*테이블(.vsct)* 파일을 포함합니다. Visual Studio 패키지 템플릿을 사용하여 VSPackage를 만든 경우 프로젝트에 이러한 파일 중 하나가 포함됩니다. 자세한 내용은 [Visual Studio 명령 테이블(.vsct) 파일을](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)참조하십시오.

 Visual Studio는 찾은 모든 *.vsct* 파일을 병합하여 명령을 표시할 수 있습니다. 이러한 파일은 VSPackage 바이너리와 구별되므로 Visual Studio는 명령을 찾기 위해 패키지를 로드할 필요가 없습니다. 자세한 내용은 [VSPackage가 사용자 인터페이스 요소를 추가하는 방법을](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)참조하십시오.

 Visual Studio는 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 등록 특성을 사용하여 메뉴 리소스 및 명령을 정의합니다. 자세한 내용은 [명령 구현](../../extensibility/internals/command-implementation.md)을 참조하십시오.

 명령은 여러 가지 방법으로 런타임에 변경할 수 있습니다. 표시하거나 숨기거나, 사용 하거나 사용할 수 없습니다. 다른 텍스트 나 아이콘을 표시하거나 다른 값을 포함 할 수 있습니다. Visual Studio에서 VSPackage를 로드하기 전에 많은 사용자 지정을 수행할 수 있습니다. 자세한 내용은 [VSPackage가 사용자 인터페이스 요소를 추가하는 방법을](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)참조하십시오.

## <a name="command-handlers"></a>명령 처리기
 명령을 만들 때 명령을 실행 하기 위해 이벤트 처리기를 제공 해야 합니다. 사용자가 명령을 선택하는 경우 적절하게 라우팅되어야 합니다. 명령을 라우팅하는 것은 명령을 활성화 또는 비활성화하고 숨기거나 표시하고 사용자가 선택한 경우 실행하기 위해 올바른 VSPackage로 전송하는 것을 의미합니다. 자세한 내용은 [명령 라우팅 알고리즘을](../../extensibility/internals/command-routing-algorithm.md)참조하십시오.

## <a name="visual-studio-command-environment"></a>비주얼 스튜디오 명령 환경
 Visual Studio는 여러 수의 VSPackage를 호스팅할 수 있으며 각 패키지는 고유한 명령 집합을 기여할 수 있습니다. 환경에는 현재 작업에 적합한 명령만 표시됩니다. 자세한 내용은 [명령 가용성](../../extensibility/internals/command-availability.md) 및 선택 [컨텍스트 개체를](../../extensibility/internals/selection-context-objects.md)참조하십시오.

 새 명령, 메뉴, 도구 모음 또는 바로 가기 메뉴를 정의하는 VSPackage는 네이티브 또는 관리되는 어셈블리의 리소스를 참조하는 레지스트리 항목을 통해 설치 시 Visual Studio에 명령 정보를 제공합니다. 그런 다음 각 리소스는 Visual Studio 명령*테이블(.vsct)* 파일을 컴파일할 때 생성되는 이진 데이터*리소스(.cto)* 파일을 참조합니다. 이를 통해 Visual Studio는 설치된 모든 VSPackage를 로드할 필요 없이 병합된 명령 집합, 메뉴 및 도구 모음을 제공할 수 있습니다.

### <a name="command-organization"></a>명령 조직
 환경은 그룹, 우선 순위 및 메뉴별로 명령을 배치합니다.

- 그룹은 **잘라내기,** **복사**및 **붙여넣기** 명령 그룹과 같은 관련 명령의 논리적 컬렉션입니다. 그룹은 메뉴에 나타나는 명령입니다.

- 우선 순위는 그룹의 개별 명령이 메뉴에 표시되는 순서를 결정합니다.

- 메뉴는 그룹에 대한 컨테이너 역할을 합니다.

  환경은 일부 명령, 그룹 및 메뉴를 미리 정의합니다. 자세한 내용은 [기본 명령, 그룹 및 도구 모음 배치를](../../extensibility/internals/default-command-group-and-toolbar-placement.md)참조하십시오.

  명령을 기본 그룹에 할당할 수 있습니다. 기본 그룹은 기본 메뉴 구조와 **사용자 지정** 대화 상자에서 명령의 위치를 제어합니다. 명령은 여러 그룹에 나타날 수 있습니다. 예를 들어 명령은 기본 메뉴, 바로 가기 메뉴 및 도구 모음에 있을 수 있습니다. 자세한 내용은 [VSPackage가 사용자 인터페이스 요소를 추가하는 방법을](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)참조하십시오.

### <a name="command-routing"></a>명령 라우팅
 VSPackage에 대한 호출 및 라우팅 명령을 호출하는 프로세스는 개체 인스턴스에서 메서드를 호출하는 프로세스와 다릅니다.

 환경 은 현재 선택을 기반으로 하는 가장 안쪽(로컬) 명령 컨텍스트에서 가장 바깥쪽(전역) 컨텍스트로 순차적으로 명령을 라우팅합니다. 명령을 실행할 수 있는 첫 번째 컨텍스트는 명령을 처리하는 컨텍스트입니다. 자세한 내용은 [명령 라우팅 알고리즘을](../../extensibility/internals/command-routing-algorithm.md)참조하십시오.

 대부분의 경우 환경은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 사용하여 명령을 처리합니다. 명령 라우팅 스키마를 사용하면 여러 개체가 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령을 처리할 수 있으므로 여러 개체에서 구현할 수 있습니다. 여기에는 Microsoft ActiveX 컨트롤, 창 보기 구현, 문서 개체, 프로젝트 계층 구조 및 VSPackage 개체 자체가 포함됩니다(전역 명령의 경우). 예를 들어 계층 구조의 라우팅 명령과 같은 일부 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 특수한 경우에는 인터페이스를 구현해야 합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[명령 구현](../../extensibility/internals/command-implementation.md)|VSPackage에서 명령을 구현하는 방법을 설명합니다.|
|[명령 가용성](../../extensibility/internals/command-availability.md)|Visual Studio 컨텍스트에서 사용할 수 있는 명령을 결정하는 방법을 설명합니다.|
|[명령 라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio 명령 라우팅 아키텍처를 사용하여 다른 VSPackage에서 명령을 처리할 수 있는 방법을 설명합니다.|
|[명령 배치 지침](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio 환경에서 명령을 배치하는 방법을 제안합니다.|
|[VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|VSPackage가 Visual Studio 명령 아키텍처를 가장 잘 활용하는 방법을 설명합니다.|
|[기본 명령, 그룹 및 도구 모음 배치](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|VSPackage가 Visual Studio에 포함된 명령을 가장 잘 사용하는 방법을 설명합니다.|
|[VSPackage 관리](../../extensibility/managing-vspackages.md)|Visual Studio에서 VSPackage를 로드하는 방법을 설명합니다.|
|[비주얼 스튜디오 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|VSPackage에서 명령의 레이아웃과 모양을 설명하는 데 사용되는 XML 기반 *.vsct* 파일에 대한 정보를 제공합니다.|

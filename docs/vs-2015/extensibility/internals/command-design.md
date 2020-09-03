---
title: 명령 디자인 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6e9eaf69be62b38a880b07fd8eb51cfc9c256a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195070"
---
# <a name="command-design"></a>명령 디자인
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackage에 명령을 추가 하는 경우 표시 되는 위치, 사용할 수 있는 시간 및 처리 방법을 지정 해야 합니다.  
  
## <a name="defining-commands"></a>명령 정의  
 새 명령을 정의 하려면 VSPackage 프로젝트에 Visual Studio 명령 테이블 (.vvsct) 파일을 포함 합니다. Visual Studio 패키지 템플릿을 사용 하 여 VSPackage를 만든 경우 프로젝트에는 이러한 파일 중 하나가 포함 됩니다. 자세한 내용은 [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)을 참조하세요.  
  
 Visual Studio는 명령을 표시할 수 있도록 찾은 모든 vsct 파일을 병합 합니다. 이러한 파일은 VSPackage binary와 구별 되므로 Visual Studio에서 패키지를 로드 하 여 명령을 찾을 필요가 없습니다. 자세한 내용은 [How Vspackage Add User Interface Elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)항목을 참조 하세요.  
  
 Visual Studio는 등록 특성을 사용 하 여 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> 메뉴 리소스 및 명령을 정의 합니다. 자세한 내용은 [구현](../../extensibility/internals/command-implementation.md)을 참조 하세요.  
  
 명령은 다양 한 방법으로 런타임에 변경할 수 있습니다. 표시 하거나 숨길 수 있고 사용 하거나 사용 하지 않도록 설정할 수 있습니다. 다른 텍스트 또는 아이콘을 표시 하거나 다른 값을 포함할 수 있습니다. Visual Studio에서 VSPackage를 로드 하기 전에 많은 사용자 지정을 수행할 수 있습니다. 자세한 내용은 [How Vspackage Add User Interface Elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)항목을 참조 하세요.  
  
## <a name="command-handlers"></a>명령 처리기  
 명령을 만들 때 명령을 실행 하려면 이벤트 처리기를 제공 해야 합니다. 사용자가 명령을 선택 하는 경우 적절 하 게 라우팅해야 합니다. 명령을 라우팅하는 작업을 활성화 또는 비활성화 하 고, 숨기 거 나 표시 하 고, 사용자가 선택 하는 경우 실행 하기 위해 올바른 VSPackage로 보내는 것을 의미 합니다. 자세한 내용은 [라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)을 참조 하세요.  
  
## <a name="the-visual-studio-command-environment"></a>Visual Studio 명령 환경  
 Visual Studio는 원하는 수의 Vspackage를 호스트할 수 있으며, 각각의 명령 집합을 제공할 수 있습니다. 환경에는 현재 작업에 적합 한 명령만 표시 됩니다. 자세한 내용은 [가용성](../../extensibility/internals/command-availability.md) 및 [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)를 참조 하세요.  
  
 새 명령, 메뉴, 도구 모음 또는 바로 가기 메뉴를 정의 하는 VSPackage는 설치 시 네이티브 또는 관리 되는 어셈블리의 리소스를 참조 하는 레지스트리 항목을 통해 Visual Studio에 명령 정보를 제공 합니다. 그런 다음 각 리소스는 Visual Studio 명령 테이블 (.cvsct) 파일을 컴파일할 때 생성 되는 이진 데이터 리소스 (.cto) 파일을 참조 합니다. 이렇게 하면 설치 된 모든 VSPackage를 로드할 필요 없이 Visual Studio가 병합 된 명령 집합, 메뉴 및 도구 모음을 제공할 수 있습니다.  
  
### <a name="command-organization"></a>명령 구성  
 환경에서는 그룹, 우선 순위 및 메뉴를 기준으로 명령을 배치 합니다.  
  
- 그룹은 **잘라내기**, **복사**및 **붙여넣기** 명령 그룹과 같은 관련 명령의 논리적 모음입니다. 그룹은 메뉴에 표시 되는 명령입니다.  
  
- 우선 순위 그룹의 개별 명령이 메뉴에 표시 되는 순서를 결정 합니다.  
  
- 메뉴는 그룹의 컨테이너 역할을 합니다.  
  
  환경에서는 일부 명령, 그룹 및 메뉴를 전 합니다. 자세한 내용은 [기본 명령, 그룹 및 도구 모음 배치](../../extensibility/internals/default-command-group-and-toolbar-placement.md)를 참조 하세요.  
  
  명령을 주 그룹에 할당할 수 있습니다. 주 그룹은 주 메뉴 구조와 **사용자 지정** 대화 상자에서 명령의 위치를 제어 합니다. 명령은 여러 그룹에 나타날 수 있습니다. 예를 들어 명령은 주 메뉴, 바로 가기 메뉴 및 도구 모음에 있을 수 있습니다. 자세한 내용은 [How Vspackage Add User Interface Elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)항목을 참조 하세요.  
  
### <a name="command-routing"></a>명령 라우팅  
 Vspackage에 대 한 호출 및 라우팅 명령의 프로세스는 개체 인스턴스에서 메서드를 호출 하는 프로세스와 다릅니다.  
  
 이 환경은 현재 선택 항목을 기반으로 하는 가장 안쪽 (로컬) 명령 컨텍스트에서 명령을 가장 바깥쪽 (전역) 컨텍스트로 라우팅합니다. 명령을 실행할 수 있는 첫 번째 컨텍스트가이를 처리 하는 컨텍스트입니다. 자세한 내용은 [라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)을 참조 하세요.  
  
 대부분의 경우 환경에서는 인터페이스를 사용 하 여 명령을 처리 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . 명령 라우팅 체계를 사용 하면 다양 한 개체에서 명령을 처리할 수 있으므로 여러 개체를 사용 하 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 여 구현할 수 있습니다. 여기에는 Microsoft ActiveX 컨트롤, 창 보기 구현, 문서 개체, 프로젝트 계층 및 VSPackage 개체 자체 (전역 명령의 경우)가 포함 됩니다. 일부 특수 한 경우 (예: 계층의 명령 라우팅)에서 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 구현 해야 합니다.  
  
## <a name="related-topics"></a>관련 항목  
  
|제목|설명|  
|-----------|-----------------|  
|[구현](../../extensibility/internals/command-implementation.md)|VSPackage에서 명령을 구현 하는 방법을 설명 합니다.|  
|[가용성](../../extensibility/internals/command-availability.md)|Visual Studio 컨텍스트에서 사용할 수 있는 명령을 결정 하는 방법에 대해 설명 합니다.|  
|[라우팅 알고리즘](../../extensibility/internals/command-routing-algorithm.md)|Visual Studio 명령 라우팅 아키텍처를 사용 하 여 다른 Vspackage에서 명령을 처리 하는 방법을 설명 합니다.|  
|[배치 지침](../../extensibility/internals/command-placement-guidelines.md)|Visual Studio 환경에서 명령을 배치 하는 방법을 제안 합니다.|  
|[VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Vspackage에서 Visual Studio 명령 아키텍처를 가장 효율적으로 활용할 수 있는 방법을 설명 합니다.|  
|[기본 명령, 그룹 및 도구 모음 배치](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Vspackage에서 Visual Studio에 포함 된 명령을 가장 잘 사용할 수 있는 방법을 설명 합니다.|  
|[VSPackage 관리](../../extensibility/managing-vspackages.md)|Visual Studio에서 Vspackage를 로드 하는 방법을 설명 합니다.|  
|[Visual Studio 명령 테이블(.Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Vspackage의 명령 레이아웃 및 모양을 설명 하는 데 사용 되는 XML 기반 vsct 파일에 대 한 정보를 제공 합니다.|

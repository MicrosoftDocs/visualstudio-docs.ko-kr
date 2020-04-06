---
title: 사용자 지정 사용자 인터페이스(소스 제어 VS패키지) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708924"
---
# <a name="custom-user-interface-source-control-vspackage"></a>사용자 지정 사용자 인터페이스(소스 제어 VSPackage)
VSPackage는 Visual Studio 명령*테이블(.vsct)* 파일을 통해 메뉴 항목과 기본 상태를 선언합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합 개발 환경(IDE)은 VSPackage가 로드될 때까지 메뉴 항목을 기본 상태로 표시합니다. 그런 다음 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메뉴 항목을 활성화하거나 사용하지 않도록 설정하려면 메서드가 호출됩니다.

 VSPackage는 레지스트리 키를 설정하여 VSPackage가 명령 사용자 인터페이스(UI) 컨텍스트에 따라 자동으로 로드될 수 있도록 할 수 있지만 일반적으로 소스 제어 VSPackage는 특정 UI 컨텍스트로 전환하는 대신 필요에 따라 로드해야 합니다. **자동 로드 패키지** 레지스트리 키에 대 한 자세한 내용은 [VSPackage 관리](../../extensibility/managing-vspackages.md)를 참조 합니다.

## <a name="vspackage-ui"></a>VS패키지 UI
 소스 제어 패키지는 VSPackage로 구현되며 에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]UI를 사용하지 않습니다. 각 소스 제어 VSPackage는 메뉴 항목, 메뉴 그룹, 도구 창, 도구 모음 및 소스 제어 VSPackage와 관련된 옵션을 설정하는 데 필요한 UI와 같은 고유한 UI 요소를 지정해야 합니다. 이러한 UI 요소는 정적으로 또는 동적으로 활성화할 수 있습니다. 정적 UI 요소는 *.vsct* 파일에 정의되며 VSPackage가 로드되었는지 여부에 관계없이 표시됩니다. 동적 UI 요소는 와 같은 <xref:EnvDTE.Constants.vsContextNoSolution>특정 명령 UI 컨텍스트에 따라 표시되거나 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드 호출의 결과로 표시될 수 있습니다. 동적 UI 요소의 가시성은 VSPackage의 지연된 로드 전략을 준수합니다.

## <a name="ui-constraints-on-source-control-vspackages"></a>소스 제어 VS패키지에 대한 UI 제약 조건
 소스 제어 VSPackage를 로드한 후 IDE에서 제거할 수 없으므로 VSPackage는 비활성 상태로 들어갈 수 있어야 합니다. VSPackage가 더 이상 활성화되지 않는다는 알림을 받으면 VSPackage는 UI를 비활성화하고 외부 IDE 상호 작용을 무시합니다. VSPackage의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드 구현은 VSPackage가 활성화되어 있지 않을 때 명령을 숨겨야 합니다.

 모든 소스 제어 VSPackage는 인터페이스를 `IVsSccProvider` 구현해야 합니다. 인터페이스에서 두 가지 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>메서드및 는 VSPackage에서 구현해야 합니다.

 소스 제어 VSPackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>의해 구현되는 다양한 IDE 이벤트를 구독했을 수 있습니다. 또한 VSPackage는 와 같은 레지스트리 지원 콜백 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>구현했을 수 있습니다. 이러한 인터페이스는 모두 비활성 상태일 때 무시해야 합니다.

 다음 목록은 소스 제어 VSPackage의 활성 상태에 의해 영향을 받는 인터페이스를 보여 줍니다.

- 프로젝트 문서 이벤트를 추적합니다.

- 솔루션 이벤트입니다.

- 솔루션 지속성 인터페이스입니다. 비활성 상태인 경우 *.sln* 및 *.suo* 파일에 패키지를 작성해서는 안 됩니다.

- 속성 익스텐더입니다.

  소스 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 제어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>VSPackage가 비활성 상태일 때 필요한 및 필수 인터페이스및 소스 제어와 연결된 선택적 인터페이스도 호출되지 않습니다.

  IDE가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 시작되면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령 UI 컨텍스트를 현재 기본 소스 제어 VSPackage ID의 ID로 설정합니다. 이렇게 하면 활성 소스 컨트롤 VSPackage의 정적 UI가 실제로 VSPackage를 로드하지 않고 IDE에 나타납니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> 호출하기 전에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 등록할 수 있도록 일시 중지됩니다.

  다음 표는 IDE가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다른 UI 항목을 숨기는 방법에 대한 구체적인 세부 정보를 설명합니다.

| UI 항목 | 설명 |
| - | - |
| 메뉴 및 도구 모음 | 소스 제어 패키지는 *.vsct* 파일의 [가시성 제약](../../extensibility/visibilityconstraints-element.md) 섹션의 소스 제어 패키지 ID로 초기 메뉴 및 도구 모음 가시성 상태를 설정해야 합니다. 이렇게 하면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE는 VSPackage를 로드하고 메서드의 구현을 호출하지 않고도 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메뉴 항목의 상태를 적절하게 설정할 수 있습니다. |
| 도구 창 | 소스 제어 VSPackage는 비활성 상태가 될 때 소유한 모든 도구 창을 숨깁니다. |
| 소스 제어 VS패키지별 옵션 페이지 | 레지스트리 키 **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\Tools옵션페이지\가시성CmdUIContexts는** VSPackage가 옵션 페이지를 표시해야 하는 컨텍스트를 설정할 수 있도록 합니다. 이 키 아래의 레지스트리 항목은 소스 제어 서비스의 서비스 ID(SID)를 사용하고 DWORD 값을 1로 지정하여 만들어야 합니다. 컨텍스트에서 UI 이벤트가 발생할 때마다 소스 제어 VSPackage가 등록되고 활성 상태인 경우 VSPackage가 호출됩니다. |

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [VSPackage 관리](../../extensibility/managing-vspackages.md)

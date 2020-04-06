---
title: 오류 처리 및 반환 값 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711928"
---
# <a name="error-handling-and-return-values"></a>오류 처리 및 반환 값
VSPackage 및 COM은 오류에 대해 동일한 아키텍처를 사용합니다. 및 `SetErrorInfo` `GetErrorInfo` 함수는 Win32 응용 프로그램 프로그래밍 인터페이스(API)의 일부입니다. 통합 개발 환경(IDE)의 모든 VSPackage는 이러한 전역 Win32 API를 호출하여 오류 알림을 받을 때 풍부한 오류 정보를 기록할 수 있습니다. 오류 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 정보를 관리하기 위한 interop 어셈블리를 제공합니다.

## <a name="interop-methods"></a>인터롭 방법
 편의를 위해 IDE는 Win32 API를 호출하는 대신 사용할 수 있는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>제공합니다. 관리 코드에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>를 사용합니다. 오류 메시지가 `HRESULT` 표시되어야 하는 수준에 오류가 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 도착하면(명령 처리기를 구현하는 개체인 경우) IDE는 다른 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>메서드를 사용하여 적절한 메시지 상자를 표시합니다. 관리 되는 코드에서 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 사용 합니다.

 VSPackage 구현자는 COM 개체가 일반적으로 `ISupportErrorInfo`을 구현합니다. 인터페이스를 `ISupportErrorInfo` 사용하면 풍부한 오류 정보가 호출 체인을 수직으로 이동할 수 있습니다. 프로세스 간 또는 스레드 간에 사용될 수 `ISupportErrorInfo` 있는 개체는 풍부한 오류 정보가 호출자에게 제대로 마샬링되도록 지원해야 합니다.

 VSPackage와 관련되어 있고 편집기 팩터리, 편집자, 계층 구조 및 제공된 서비스를 포함하여 IDE 확장과 관련된 모든 개체는 풍부한 오류 정보를 지원해야 합니다. IDE는 이러한 VSPackage 개체를 구현할 `ISupportErrorInfo`필요가 없지만 항상 권장됩니다.

 IDE는 오류 정보를 보고하고 IDE에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` 전파될 때마다 사용자에게 표시할 책임이 있습니다. IDE는 개체를 만드는 `ErrorInfo` 메커니즘이기도 합니다.

## <a name="general-guidelines"></a>일반 지침
 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 사용하여 VSPackage 구현에 내부에 있는 오류를 설정하고 보고할 수도 있습니다. 그러나 일반적으로 VSPackage에서 오류 메시지를 처리하기 위한 다음 지침을 따릅니다.

- VSPackage COM 개체에 구현합니다. `ISupportErrorInfo`

- 을 구현하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>개체에서 메서드를 호출하는 오류 보고 메커니즘을 만듭니다.

- 메서드를 통해 사용자에게 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 오류를 표시하도록 합니다.

## <a name="error-information-in-the-ide"></a>IDE의 오류 정보
 다음 규칙은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE에서 오류 정보를 처리하는 방법을 나타냅니다.

- 부실 오류 정보가 사용자에게 보고되지 않도록 보장하기 위한 방어 전략으로 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 메서드를 호출하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 함수는 먼저 메서드를 호출해야 합니다. 새 `null` 오류 정보를 설정할 수 있는 모든 것을 호출하기 전에 캐시된 오류 메시지를 지우기 위해 전달합니다.

- 오류 메시지를 직접 보고하지 않는 함수는 오류를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> `HRESULT`반환하는 경우에만 메서드를 호출할 수 있습니다. 함수에 `ErrorInfo` 대한 항목을 지우거나 반환할 <xref:Microsoft.VisualStudio.VSConstants.S_OK>때 허용됩니다. 이 규칙의 유일한 예외는 호출이 `HRESULT` 수신 당사자가 명시적으로 복구하거나 안전하게 무시할 수 있는 오류를 반환하는 경우입니다.

- 오류를 `HRESULT` 명시적으로 무시하는 모든 당사자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 을 <xref:Microsoft.VisualStudio.VSConstants.S_OK>사용하여 메서드를 호출해야 합니다. 그렇지 않으면 `ErrorInfo` 다른 당사자가 자신의 `ErrorInfo`을 제공하지 않고 오류를 생성할 때 개체가 실수로 사용될 수 있습니다.

- 오류가 `HRESULT` 발생한 모든 메서드는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 호출하여 풍부한 오류 정보를 제공하는 것이 좋습니다. 반환된 `HRESULT` 오류가 특수 `FACILITY_ITF` 한 오류 인 경우 메서드는 `ErrorInfo`적절 한 개체를 제공 하는 데 필요한. 반환된 오류가 표준 시스템 오류(예: <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>" , " , 및 등)인 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 메서드를 명시적으로 호출하지 않고 오류 코드를 반환할 수 있습니다. 방어적 코딩 전략으로 오류(시스템 `HRESULT` 오류 포함)를 발생시키는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> `ErrorInfo` 항상 오류를 보다 자세하게 `null`설명하거나 .

- 다른 호출에서 시작된 오류를 반환하는 모든 함수는 `HRESULT` `ErrorInfo` 개체를 수정하지 않고 에서 실패한 호출에서 수신된 정보를 전달해야 합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo(구성 요소 자동화)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)

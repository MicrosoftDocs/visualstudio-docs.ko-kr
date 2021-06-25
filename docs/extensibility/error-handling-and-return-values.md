---
title: 오류 처리 및 반환 값 | Microsoft Docs
description: Visual Studio SDK가 오류 알림을 받을 때 풍부한 오류 정보를 기록하는 interop 어셈블리를 제공하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef33936e3dc36d98cc88b1285aa0b198a84cbd59
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898320"
---
# <a name="error-handling-and-return-values"></a>오류 처리 및 반환 값
VSPackage 및 COM은 오류에 동일한 아키텍처를 사용합니다. `SetErrorInfo`및 `GetErrorInfo` 함수는 Win32 API(애플리케이션 프로그래밍 인터페이스)의 일부입니다. IDE(통합 개발 환경)의 모든 VSPackage는 이러한 전역 Win32 API를 호출하여 오류 알림을 받을 때 풍부한 오류 정보를 기록할 수 있습니다. 는 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 오류 정보를 관리하는 interop 어셈블리를 제공합니다.

## <a name="interop-methods"></a>Interop 메서드
 편의상 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Win32 API를 호출하는 대신 를 사용하는 메서드를 제공합니다. 관리 코드에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 를 사용합니다. 오류 `HRESULT` 메시지가 표시되어야 하는 수준(종종 명령 처리기를 구현하는 개체)에 도달하면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> IDE는 다른 메서드 를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 적절한 메시지 상자를 표시합니다. 관리 코드에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 메서드를 사용합니다.

 VSPackage 구현자는 COM 개체가 일반적으로 `ISupportErrorInfo` 를 구현합니다. `ISupportErrorInfo`인터페이스를 사용하면 풍부한 오류 정보가 호출 체인 위로 세로로 이동할 수 있습니다. 프로세스 간 또는 스레드 간에 사용될 수 있는 개체는 `ISupportErrorInfo` 풍부한 오류 정보가 호출자에게 제대로 마샬링되도록 지원해야 합니다.

 VSPackage와 관련되고 편집기 팩터리, 편집기, 계층 구조 및 제공된 서비스를 포함하여 IDE 확장과 관련된 모든 개체는 풍부한 오류 정보를 지원해야 합니다. IDE는 이러한 VSPackage 개체가 를 구현할 필요가 없지만 `ISupportErrorInfo` 항상 권장됩니다.

 IDE는 가 IDE로 전파 될 때마다 오류 정보를 보고하고 사용자에게 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` 표시합니다. IDE는 개체를 만드는 메커니즘이기도 `ErrorInfo` 합니다.

## <a name="general-guidelines"></a>일반 지침
 및 메서드를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> VSPackage 구현 내부 오류를 설정하고 보고할 수도 있습니다. 그러나 일반적인 규칙으로 VSPackage에서 오류 메시지를 처리하기 위해 다음 지침을 따르세요.

- `ISupportErrorInfo`VSPackage COM 개체에서 를 구현합니다.

- 를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 구현하는 개체에서 메서드를 호출하는 오류 보고 메커니즘을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 만듭니다.

- IDE에서 메서드를 통해 사용자에게 오류를 표시하도록 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 합니다.

## <a name="error-information-in-the-ide"></a>IDE의 오류 정보
 다음 규칙은 IDE에서 오류 정보를 처리하는 방법을 나타냅니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

- 부실 오류 정보가 사용자에게 보고되지 않도록 하기 위한 방어 전략으로 메서드를 호출하는 함수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 먼저 메서드를 호출해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 합니다. 새 오류 정보를 설정할 수 있는 모든 메시지를 `null` 호출하기 전에 캐시된 오류 메시지를 지우려면 을 전달합니다.

- 오류 메시지를 직접 보고하지 않는 함수는 오류를 반환하는 경우에만 메서드를 호출할 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> `HRESULT` 있습니다. 함수에 대한 항목에서 또는 를 반환할 때 를 지울 수 `ErrorInfo` <xref:Microsoft.VisualStudio.VSConstants.S_OK> 있습니다. 이 규칙의 유일한 예외는 수신 `HRESULT` 당사자가 명시적으로 복구하거나 안전하게 무시할 수 있는 오류를 호출에서 반환하는 경우입니다.

- 오류를 명시적으로 무시하는 모든 당사자는 를 사용하여 `HRESULT` 메서드를 호출해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.VSConstants.S_OK> 합니다. 그렇지 않으면 `ErrorInfo` 다른 당사자가 자신의 를 제공하지 않고 오류를 생성할 때 개체가 실수로 사용될 수 `ErrorInfo` 있습니다.

- 오류를 발생시키는 모든 `HRESULT` 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 메서드를 호출하여 풍부한 오류 정보를 제공하는 것이 좋습니다. 반환된 `HRESULT` 가 특별한 오류인 경우 `FACILITY_ITF` 메서드는 적절한 `ErrorInfo` 개체를 제공해야 합니다. 반환된 오류가 표준 시스템 오류(예: <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> , , , <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> 등)인 경우 <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> 메서드를 명시적으로 호출하지 않고 오류 코드를 반환할 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 있습니다. 방어적 코딩 전략으로 오류를 발생시키는 `HRESULT` 경우(시스템 오류 포함) 항상 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 오류를 자세히 설명하는 또는 를 사용하여 메서드를 `ErrorInfo` 호출합니다. `null`

- 다른 호출에서 발생한 오류를 반환하는 모든 함수는 개체를 수정하지 않고 에서 실패한 호출에서 받은 정보를 전달해야 `HRESULT` `ErrorInfo` 합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo(구성 요소 자동화)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)

---
title: 오류 처리 및 반환 값 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74e61e60384b3e98bf26eb8208696ecb9223efa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696339"
---
# <a name="error-handling-and-return-values"></a>오류 처리 및 반환 값
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage 및 COM은 동일한 아키텍처를 사용 하 여 오류를 해결 합니다. `SetErrorInfo`및 `GetErrorInfo` 함수는 Win32 API (응용 프로그래밍 인터페이스)의 일부입니다. IDE (통합 개발 환경)의 모든 VSPackage은 이러한 글로벌 Win32 Api를 호출 하 여 오류 알림을 받을 때 다양 한 오류 정보를 기록할 수 있습니다. 는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 오류 정보를 관리 하는 interop 어셈블리를 제공 합니다.  
  
## <a name="interop-methods"></a>Interop 메서드  
 편의를 위해 IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> Win32 api를 호출 하는 대신를 사용 하는 메서드를 제공 합니다. 관리 코드에서를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 합니다. 오류 메시지를 `HRESULT` 표시 해야 하는 수준에 오류가 도착 하면 (일반적으로 명령 처리기를 구현 하는 개체 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) IDE는 다른 메서드인 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 를 사용 하 여 적절 한 메시지 상자를 표시 합니다. 관리 코드에서 메서드를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 합니다.  
  
 VSPackage 구현자 인 COM 개체는 일반적으로를 구현 `ISupportErrorInfo` 합니다. 인터페이스를 사용 하면 `ISupportErrorInfo` 다양 한 오류 정보가 호출 체인에서 수직으로 이동할 수 있습니다. 프로세스나 스레드 간에 사용 될 수 있는 개체는 `ISupportErrorInfo` 다양 한 오류 정보가 호출자에 게 올바르게 마샬링 되도록 지원 해야 합니다.  
  
 편집기 팩터리, 편집기, 계층 구조 및 제공 된 서비스를 비롯 하 여 IDE 확장에 관련 된 Vspackage와 관련 된 모든 개체는 다양 한 오류 정보를 지원 해야 합니다. IDE는 이러한 VSPackage 개체가 구현 하도록 요구 하지 않지만 `ISupportErrorInfo` 항상 권장 됩니다.  
  
 IDE는가 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ide로 전파 될 때마다 오류 정보를 보고 하 고이를 사용자에 게 표시 하는 일을 담당 합니다 `HRESULT` . IDE는 개체를 만들기 위한 메커니즘 이기도 합니다 `ErrorInfo` .  
  
## <a name="general-guidelines"></a>일반 지침  
 및 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> VSPackage 구현에 대 한 내부 오류를 설정 하 고 보고할 수 있습니다. 그러나 일반적인 규칙에 따라 VSPackage에서 오류 메시지를 처리 하기 위해 다음 지침을 따르세요.  
  
- `ISupportErrorInfo`VSPACKAGE COM 개체에서을 구현 합니다.  
  
- 을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 구현 하는 개체에서 메서드를 호출 하는 오류 보고 메커니즘을 만듭니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
- IDE에서 메서드를 통해 사용자에 게 오류를 표시 하도록 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> .  
  
## <a name="error-information-in-the-ide"></a>IDE의 오류 정보  
 다음 규칙은 IDE에서 오류 정보를 처리 하는 방법을 표시 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- 오래 된 오류 정보가 사용자에 게 보고 되지 않도록 보장 하는 방어 전략으로 메서드를 호출 하는 함수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 먼저 메서드를 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . `null`새 오류 정보를 설정 하는 모든 항목을 호출 하기 전에를 전달 하 여 캐시 된 오류 메시지를 지웁니다.  
  
- 오류 메시지를 직접 보고 하지 않는 함수는 오류를 반환 하는 경우에만 메서드를 호출할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> `HRESULT` . 을 `ErrorInfo` 함수에 대 한 항목에서 지우거 나를 반환할 수 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 있습니다. 이 규칙의 유일한 예외는 호출에서 `HRESULT` 수신 파티가 명시적으로 복구 하거나 무시 하는 오류를 반환 하는 경우입니다.  
  
- 오류를 명시적으로 무시 하는 모든 당사자는 `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 를 사용 하 여 메서드를 호출 해야 합니다 <xref:Microsoft.VisualStudio.VSConstants.S_OK> . 그렇지 않으면 `ErrorInfo` 다른 파티가 자체를 제공 하지 않고 오류를 생성할 때 개체가 실수로 사용 될 수 있습니다 `ErrorInfo` .  
  
- 오류를 발생 시키는 모든 메서드는 `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 다양 한 오류 정보를 제공 하기 위해 메서드를 호출 하는 것이 좋습니다. 반환 된 `HRESULT` 이 특수 오류 이면 `FACILITY_ITF` 메서드가 적절 한 개체를 제공 해야 `ErrorInfo` 합니다. 반환 된 오류가 표준 시스템 오류 (예:,,, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> 등) 인 경우 <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> 메서드를 명시적으로 호출 하지 않고 오류 코드를 반환할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 방어 코딩 전략으로 오류가 발생 하는 경우 `HRESULT` (시스템 오류 포함)에는 항상 오류를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> 자세히 설명 하거나를 사용 하 여 메서드를 호출 합니다 `ErrorInfo` `null` .  
  
- 다른 호출로 발생 한 오류를 반환 하는 모든 함수는 `HRESULT` 개체를 수정 하지 않고의 실패 한 호출에서 받은 정보를 전달 해야 합니다 `ErrorInfo` .  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (구성 요소 자동화)](https://msdn.microsoft.com/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](https://msdn.microsoft.com/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo 인터페이스](https://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32)

---
title: 사용자 인터페이스 업데이트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698883"
---
# <a name="updating-the-user-interface"></a>사용자 인터페이스 업데이트
명령을 구현한 후 새 명령의 상태로 사용자 인터페이스를 업데이트 하는 코드를 추가할 수 있습니다.

 일반적인 Win32 응용 프로그램에서는 명령 집합이 지속적으로 폴링 될 수 있으며 사용자가이를 볼 때 개별 명령의 상태를 조정할 수 있습니다. 그러나 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 셸은 vspackage 수를 무제한으로 호스트할 수 있으므로 광범위 한 폴링은 특히 관리 코드와 COM 간의 상호 운용성 어셈블리 간 폴링을 통해 응답성을 저하 시킬 수 있습니다.

### <a name="to-update-the-ui"></a>UI를 업데이트 하려면

1. 다음 단계 중 하나를 수행합니다.

    - <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 메서드를 호출합니다.

         <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>다음과 같이 서비스에서 인터페이스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> .

        ```csharp
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)
        {
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));
            if (vsShell != null)
            {
                int hr = vsShell.UpdateCommandUI(0);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
            }
        }

        ```

         의 매개 변수가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 0이 아닌 경우 ( `TRUE` ) 업데이트는 동기적으로 즉시 수행 됩니다. `FALSE`좋은 성능을 유지 하기 위해이 매개 변수에 대해 0 ()을 전달 하는 것이 좋습니다. 캐싱을 방지 하려면 `DontCache` . vsct 파일에서 명령을 만들 때 플래그를 적용 합니다. 그럼에도 불구 하 고 주의 해 서 플래그를 사용 하면 성능이 저하 될 수 있습니다. 명령 플래그에 대 한 자세한 내용은 [명령 플래그 요소](../extensibility/command-flag-element.md) 설명서를 참조 하세요.

    - 창에서 내부 활성화 모델을 사용 하 여 ActiveX 컨트롤을 호스트 하는 Vspackage 메서드를 사용 하는 것이 더 편리할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> . 인터페이스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 메서드와 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 인터페이스의 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 기능적으로 동일 합니다. 둘 다 환경에서 모든 명령의 상태를 다시 쿼리 합니다. 일반적으로 업데이트는 즉시 수행 되지 않습니다. 대신 유휴 시간까지 업데이트가 지연 됩니다. Shell은 좋은 성능을 유지 하는 데 도움이 되도록 명령 상태를 캐시 합니다. 캐싱을 방지 하려면 `DontCache` . vsct 파일에서 명령을 만들 때 플래그를 적용 합니다. 그럼에도 불구 하 고 성능이 저하 될 수 있으므로 주의 해 서 플래그를 사용 합니다.

         <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> `QueryInterface` 개체에 대해 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> 하거나 서비스에서 인터페이스를 가져와서 인터페이스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> .

## <a name="see-also"></a>추가 정보
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [구현](../extensibility/internals/command-implementation.md)

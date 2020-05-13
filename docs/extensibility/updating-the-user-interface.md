---
title: 사용자 인터페이스 업데이트 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698883"
---
# <a name="updating-the-user-interface"></a>사용자 인터페이스 업데이트
명령을 구현한 후 코드를 추가하여 새 명령의 상태로 사용자 인터페이스를 업데이트할 수 있습니다.

 일반적인 Win32 응용 프로그램에서는 명령 집합을 지속적으로 폴링할 수 있으며 사용자가 볼 때 개별 명령의 상태를 조정할 수 있습니다. 그러나 셸은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage를 무제한으로 호스팅할 수 있으므로 광범위한 폴링은 응답성을 떨어뜨릴 수 있으며, 특히 관리 되는 코드와 COM 간의 interop 어셈블리 간에 폴링이 발생할 수 있습니다.

### <a name="to-update-the-ui"></a>UI를 업데이트하려면

1. 다음 단계 중 하나를 수행합니다.

    - <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 메서드를 호출합니다.

         인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 다음과 같이 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> 서비스에서 얻을 수 있다.

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

         의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> 매개 변수가 0이`TRUE`아닌 경우 () 업데이트가 동기적으로 즉시 수행됩니다. 이 매개 변수에`FALSE`대해 0 () 을 통과하여 성능을 유지하는 것이 좋습니다. 캐싱을 방지하려면 .vsct `DontCache` 파일에 명령을 만들 때 플래그를 적용합니다. 그럼에도 불구 하 고, 플래그를 신중 하 게 사용 하거나 성능 저하 될 수 있습니다. 명령 플래그에 대한 자세한 내용은 [명령 플래그 요소](../extensibility/command-flag-element.md) 설명서를 참조하십시오.

    - 창에서 내부 활성화 모델을 사용하여 ActiveX 컨트롤을 호스트하는 VSPackage에서는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> 사용하는 것이 더 편리할 수 있습니다. 인터페이스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 메서드와 인터페이스의 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 메서드는 기능적으로 동일합니다. 둘 다 환경이 모든 명령의 상태를 다시 쿼리하게 합니다. 일반적으로 업데이트는 즉시 수행되지 않습니다. 대신 유휴 시간까지 업데이트가 지연됩니다. 셸은 명령 상태를 캐시하여 성능이 양호합니다. 캐싱을 방지하려면 .vsct `DontCache` 파일에 명령을 만들 때 플래그를 적용합니다. 그럼에도 불구하고 성능이 저하될 수 있으므로 플래그를 신중하게 사용하십시오.

         개체에서 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 메서드를 `QueryInterface` 호출하거나 서비스에서 인터페이스를 가져와 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 가져올 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager>

## <a name="see-also"></a>참조
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [구현](../extensibility/internals/command-implementation.md)

---
title: Visual Studio Interop 어셈블리 매개 변수 마샬링 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686918"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Visual Studio Interop 어셈블리 매개 변수 마샬링
관리 코드로 작성 된 Vspackage는 관리 되지 않는 COM 코드에서를 호출 하거나 호출 해야 할 수 있습니다. 일반적으로 메서드 인수는 interop 마샬러에 의해 자동으로 변환 되거나 마샬링됩니다. 그러나 경우에 따라 인수를 간단한 방법으로 변환할 수 없습니다. 이러한 경우 interop 어셈블리 메서드 프로토타입 매개 변수를 사용 하 여 COM 함수 매개 변수를 최대한 가깝게 일치 시킵니다. 자세한 내용은 [Interop 마샬링](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)을 참조 하세요.  
  
## <a name="general-suggestions"></a>일반 제안  
  
##### <a name="read-the-reference-documentation"></a>참조 설명서 읽기  
 상호 운용성 문제를 효과적으로 감지 하려면 각 방법에 대 한 참조 설명서를 읽어 보십시오.  
  
 각 메서드에 대 한 참조 설명서에는 다음과 같은 세 가지 관련 섹션이 있습니다.  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]COM 함수 프로토타입입니다.  
  
- Interop 어셈블리 메서드 프로토타입입니다.  
  
- COM 매개 변수의 목록과 각각에 대 한 간단한 설명입니다.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>두 프로토타입 간의 차이점을 확인 합니다.  
 대부분의 상호 운용성 문제는 COM 인터페이스의 특정 형식 정의와 interop 어셈블리에서 동일한 형식의 정의 간의 불일치에서 파생 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 됩니다. 예를 들어 `null` [out] 매개 변수에서 값을 전달 하는 기능의 차이점을 고려해 보십시오. 두 프로토타입 간의 차이점을 확인 하 고 전달 되는 데이터에 대 한 결과를 고려해 야 합니다.  
  
##### <a name="read-the-parameter-definitions"></a>매개 변수 정의 읽기  
 매개 변수 정의를 읽습니다. COM은 단일 매개 변수에서 여러 형식의 데이터를 혼합 하는 데 대 한 CLR (공용 언어 런타임) 보다 엄격 하지 않습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]COM 인터페이스는 이러한 유연성을 완벽 하 게 활용 합니다. 포인터 매개 변수의 상수 값과 같이 비표준 값 또는 데이터 형식을 전달 하거나 필요로 하는 모든 매개 변수는 설명서에 설명 되어 있어야 합니다.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown 개체가 void 형식으로 전달 되었습니다. * *  
 COM 인터페이스에서 형식으로 정의 되는 [out] 매개 변수를 찾습니다 .이 매개 변수 `void **` 는 `[``iid_is``]` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 어셈블리 메서드 프로토타입에서로 정의 됩니다.  
  
 경우에 따라 COM 인터페이스는 `IUnknown` 개체를 생성 하 고 com 인터페이스는이를 형식으로 전달 합니다 `void **` . 이러한 인터페이스는 변수가 IDL에서 [out]으로 정의 된 경우 `IUnknown` 개체는 메서드와 함께 참조로 계산 되기 때문에 특히 중요 합니다 `AddRef` . 개체가 올바르게 처리 되지 않으면 메모리 누수가 발생 합니다.  
  
> [!NOTE]
> `IUnknown`COM 인터페이스에 의해 생성 되 고 [out] 변수로 반환 되는 개체는 명시적으로 해제 되지 않은 경우 메모리 누수가 발생 합니다.  
  
 이러한 개체를 처리 하는 관리 되는 메서드는 <xref:System.IntPtr> 개체에 대 한 포인터로 처리 하 `IUnknown` 고 메서드를 호출 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 하 여 개체를 가져와야 합니다. 그런 다음 호출자는 적절 한 형식으로 반환 값을 캐스팅 해야 합니다. 개체가 더 이상 필요 하지 않은 경우를 호출 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 하 여 릴리스를 해제 합니다.  
  
 다음은 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> 하 고 개체를 올바르게 처리 하는 예제입니다 `IUnknown` .  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
> 다음 메서드는 개체 포인터를 형식으로 전달 하는 것으로 알려져 있습니다 `IUnknown` <xref:System.IntPtr> . 이 섹션에 설명 된 대로 처리 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>선택적 [out] 매개 변수  
 COM 인터페이스에서 [out] 데이터 형식 (, 등)으로 정의 된 매개 변수를 찾을 `int` `object` 수 있지만 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 어셈블리 메서드 프로토타입에서 동일한 데이터 형식의 배열로 정의 됩니다.  
  
 와 같은 일부 COM 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> [out] 매개 변수를 선택 사항으로 처리 합니다. 개체가 필요 하지 않은 경우 이러한 COM 인터페이스는 `null` [out] 개체를 만드는 대신 포인터를 해당 매개 변수의 값으로 반환 합니다. 이것은 의도적인 것입니다. 이러한 인터페이스의 경우 `null` 포인터는 VSPackage의 올바른 동작의 일부로 간주 되며 오류가 반환 되지 않습니다.  
  
 CLR은 [out] 매개 변수의 값을 허용 하지 않으므로 `null` 이러한 인터페이스의 디자인 된 동작 일부는 관리 코드 내에서 직접 사용할 수 없습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]영향을 받는 인터페이스에 대 한 interop 어셈블리 메서드는 CLR에서 배열 전달을 허용 하기 때문에 관련 매개 변수를 배열로 정의 하 여 문제를 해결 합니다 `null` .  
  
 이러한 메서드의 관리 되는 구현은 `null` 반환 될 항목이 없을 때 매개 변수에 배열을 배치 해야 합니다. 그렇지 않으면 올바른 형식의 요소가 하나인 배열을 만들고 반환 값을 배열에 배치 합니다.  
  
 선택적 [out] 매개 변수가 있는 인터페이스에서 정보를 수신 하는 관리 되는 메서드는 매개 변수를 배열로 받습니다. 배열의 첫 번째 요소 값을 검사 하면 됩니다. 그렇지 않으면 `null` 첫 번째 요소를 원래 매개 변수로 간주 합니다.  
  
### <a name="passing-constants-in-pointer-parameters"></a>포인터 매개 변수에서 상수 전달  
 COM 인터페이스에서 [in] 포인터로 정의 된 매개 변수를 찾습니다 .이 매개 변수는 <xref:System.IntPtr> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 어셈블리 메서드 프로토타입의 형식으로 정의 됩니다.  
  
 COM 인터페이스가 개체 포인터가 아닌 0,-1 또는-2와 같은 특수 값을 전달 하는 경우에도 유사한 문제가 발생 합니다. 와 달리 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] CLR에서는 상수를 개체로 캐스팅할 수 없습니다. 대신 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 어셈블리는 매개 변수를 형식으로 정의 합니다 <xref:System.IntPtr> .  
  
 이러한 메서드의 관리 되는 구현에서는 <xref:System.IntPtr> 클래스에 및 생성자를 모두 사용 하 여 `int` `void *` <xref:System.IntPtr> 개체 또는 정수 상수에서 적절 하 게를 만드는 사실을 활용 해야 합니다.  
  
 이 형식의 매개 변수를 받는 관리 되는 메서드는 <xref:System.IntPtr> <xref:System.IntPtr> 형식 변환 연산자를 사용 하 여 결과를 처리 해야 합니다. 먼저 <xref:System.IntPtr> 를로 변환 하 `int` 고 관련 정수 상수에 대해 테스트 합니다. 일치 하는 값이 없으면 필요한 형식의 개체로 변환 하 고 계속 합니다.  
  
 이에 대 한 예제를 보려면 및를 참조 하십시오 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>[Out] 매개 변수로 전달 된 OLE 반환 값  
 `retval`COM 인터페이스에 반환 값이 있지만 `int` [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interop 어셈블리 메서드 프로토타입의 반환 값 및 추가 [out] 배열 매개 변수가 있는 메서드를 찾습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Interop 어셈블리 메서드 프로토타입의 COM 인터페이스 메서드 보다 하나 이상의 매개 변수가 있으므로 이러한 메서드에 특별 한 처리가 필요 하다는 것을 명확 하 게 해야 합니다.  
  
 OLE 작업을 처리 하는 많은 COM 인터페이스는 OLE 상태에 대 한 정보를 `retval` 인터페이스의 반환 값에 저장 된 호출 프로그램에 다시 보냅니다. 해당 interop 어셈블리 메서드는 반환 값을 사용 하는 대신 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [out] 배열 매개 변수에 저장 된 호출 프로그램으로 정보를 다시 보냅니다.  
  
 이러한 메서드의 관리 되는 구현에서는 [out] 매개 변수와 동일한 형식의 단일 요소 배열을 만들고 매개 변수에 넣습니다. 배열 요소의 값은 적절 한 COM과 같아야 합니다 `retval` .  
  
 이 형식의 인터페이스를 호출 하는 관리 되는 메서드는 [out] 배열에서 첫 번째 요소를 가져와야 합니다. 이 요소는 `retval` 해당 COM 인터페이스의 반환 값인 것 처럼 처리할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Interop 마샬링](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Interop 마샬링](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [상호 운용성 문제 해결](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [관리되는 VSPackage](../misc/managed-vspackages.md)
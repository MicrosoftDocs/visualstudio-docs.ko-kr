---
title: 비주얼 스튜디오 인터롭 어셈블리 사용 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704128"
---
# <a name="using-visual-studio-interop-assemblies"></a>Visual Studio Interop 어셈블리 사용
Visual Studio interop 어셈블리를 사용하면 관리되는 응용 프로그램이 Visual Studio 확장성을 제공하는 COM 인터페이스에 액세스할 수 있습니다. 직선 COM 인터페이스와 인터옵 버전 사이에는 몇 가지 차이점이 있습니다. 예를 들어 HRESULTs는 일반적으로 int 값으로 표시되며 예외와 동일한 방식으로 처리되어야 하며 매개 변수(특히 out 매개 변수)는 다르게 처리됩니다.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>COM에서 관리 코드로 반환되는 HRESULT 처리
 관리 코드에서 COM 인터페이스를 호출하는 경우 HRESULT 값을 검사하고 필요에 따라 예외를 발생시킵니다. <xref:Microsoft.VisualStudio.ErrorHandler> 클래스에는 전달된 HRESULT의 값에 따라 COM 예외를 발생시키는 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 메서드가 포함되어 있습니다.

 기본적으로 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>는 0보다 작은 값을 가진 HRESULT가 전달될 때마다 예외를 발생시킵니다. 이러한 HRESULT가 허용되는 값이며 예외가 발생하지 않아야 하는 경우 값이 테스트된 후에 추가 HRESULT 값을 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>에 전달해야 합니다. 테스트되는 HRESULT가 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>에 명시적으로 전달된 HRESULT 값과 일치하는 경우 예외가 발생하지 않습니다.

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants> 클래스에는 일반적인 HRESULTS <xref:Microsoft.VisualStudio.VSConstants.S_OK> 및 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS(예: <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> 및 <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>)에 대한 상수가 포함되어 있습니다. 또한 <xref:Microsoft.VisualStudio.VSConstants>는 COM의 SUCCEEDED 및 FAILED 매크로에 해당하는 <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> 및 <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> 메서드를 제공합니다.

 예를 들어 <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>은 허용되는 반환 값이지만 0보다 작은 다른 HRESULT는 오류를 나타내는 다음 함수 호출을 고려해 보세요.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 허용되는 반환 값이 둘 이상 있는 경우 <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> 호출의 목록에 다른 HRESULT 값을 추가하면 됩니다.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>관리 코드에서 COM으로 HRESULT 반환
 예외가 발생하지 않는 경우 관리 코드가 호출한 COM 함수에 <xref:Microsoft.VisualStudio.VSConstants.S_OK>를 반환합니다. COM interop는 관리 코드에서 강력한 형식의 일반적인 예외를 지원합니다. 예를 들어 허용되지 않는 `null` 인수를 받은 메서드는 <xref:System.ArgumentNullException>을 발생시킵니다.

 어떤 예외를 발생시켜야 하는지 모르지만 COM에 반환하려는 HRESULT를 알고 있는 경우 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> 메서드를 사용하여 적절한 예외를 발생시킬 수 있습니다. 이는 비표준 오류(예: <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>)에도 적용됩니다. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>이 전달된 HRESULT를 강력한 형식의 예외에 매핑하려고 합니다. 매핑할 수 없는 경우 대신 일반 COM 예외를 발생시킵니다. 최종 결과로, 관리 코드에서 <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>에 전달하는 HRESULT가 호출한 COM 함수에 반환됩니다.

> [!NOTE]
> 예외가 발생하면 성능이 저하되며 비정상적인 프로그램 상태를 나타냅니다. 자주 발생하는 상태는 예외를 발생시키는 대신 인라인으로 처리해야 합니다.

## <a name="iunknown-parameters-passed-as-type-void"></a>I알 수 없는 매개 변수는 형식 void**로 전달되었습니다.
 COM 인터페이스의 유형으로 `void **` 정의되지만 `[``iid_is``]` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 방법 프로토타입에서와 같이 정의된 [out] 매개 변수를 찾습니다.

 경우에 따라 COM 인터페이스가 `IUnknown` 개체를 생성하고 COM 인터페이스는 `void **`이를 문자로 전달합니다. 이러한 인터페이스는 변수가 IDL에서 [out]으로 정의된 경우 개체가 `IUnknown` `AddRef` 메서드와 함께 참조 카운트되기 때문에 특히 중요합니다. 개체가 올바르게 처리되지 않으면 메모리 누수가 발생합니다.

> [!NOTE]
> COM `IUnknown` 인터페이스에서 만들고 [out] 변수로 반환된 개체는 명시적으로 해제되지 않은 경우 메모리 누수의 원인이 됩니다.

 이러한 개체를 처리하는 관리되는 메서드는 <xref:System.IntPtr> `IUnknown` 개체에 대한 <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> 포인터로 취급하고 메서드를 호출하여 개체를 가져와야 합니다. 그런 다음 호출자는 적절한 형식에 반환 값을 캐스팅해야 합니다. 개체가 더 이상 필요하지 <xref:System.Runtime.InteropServices.Marshal.Release%2A> 않은 경우 호출하여 해제합니다.

 다음은 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> 호출하고 개체를 `IUnknown` 올바르게 처리하는 예제입니다.

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
> 다음 메서드는 개체 `IUnknown` 포인터를 type으로 <xref:System.IntPtr>전달하는 것으로 알려져 있습니다. 이 섹션에 설명된 대로 처리합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>[out] 매개 변수 옵션
 COM 인터페이스에서 [out] 데이터`int`형식(등)으로 `object`정의되지만 interop 어셈블리 방법 프로토타입에서 동일한 데이터 형식의 배열로 정의되는 매개 변수를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 찾습니다.

 와 같은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>일부 COM 인터페이스는 [out] 매개 변수를 선택 사항으로 처리합니다. 개체가 필요하지 않은 경우 이러한 COM `null` 인터페이스는 [out] 개체를 만드는 대신 포인터를 해당 매개 변수의 값으로 반환합니다. 이것은 의도적인 것입니다. 이러한 인터페이스의 `null` 경우 포인터는 VSPackage의 올바른 동작의 일부로 가정되며 오류가 반환되지 않습니다.

 CLR은 [out] 매개 변수의 `null`값을 허용하지 않으므로 이러한 인터페이스의 설계된 동작의 일부가 관리되는 코드 내에서 직접 사용할 수 없습니다. CLR을 통해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] `null` 배열을 전달할 수 있으므로 영향을 받는 인터페이스에 대한 interop 어셈블리 메서드는 관련 매개 변수를 배열로 정의하여 문제를 해결합니다.

 이러한 메서드의 관리되는 구현은 반환할 것이 없을 때 `null` 배열을 매개 변수에 넣어야 합니다. 그렇지 않으면 올바른 형식의 한 요소 배열을 만들고 반환 값을 배열에 넣습니다.

 선택적 [out] 매개 변수가 있는 인터페이스에서 정보를 수신하는 관리되는 메서드는 매개 변수를 배열로 받습니다. 배열의 첫 번째 요소의 값을 검사하기만 하면 됩니다. 그렇지 않은 `null`경우 첫 번째 요소를 원래 매개 변수인 것처럼 처리합니다.

## <a name="passing-constants-in-pointer-parameters"></a>포인터 매개 변수에서 상수 전달
 COM 인터페이스에서 [in] 포인터로 정의되지만 interop 어셈블리 방법 <xref:System.IntPtr> 프로토타입의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 유형으로 정의된 매개 변수를 찾습니다.

 COM 인터페이스가 개체 포인터 대신 0, -1 또는 -2와 같은 특수 값을 전달할 때도 비슷한 문제가 발생합니다. 달리 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]CLR에서는 상수를 개체로 캐스팅할 수 없습니다. 대신 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리는 매개변수를 <xref:System.IntPtr> 유형으로 정의합니다.

 이러한 메서드의 관리되는 구현은 <xref:System.IntPtr> 클래스에 개체 또는 `int` `void *` 정수 상수에서 <xref:System.IntPtr> 를 만드는 생성자와 생성자가 모두 있다는 사실을 적절히 활용해야 합니다.

 이 형식의 <xref:System.IntPtr> 매개 변수를 수신하는 <xref:System.IntPtr> 관리되는 메서드는 형식 변환 연산자에서 결과를 처리해야 합니다. 먼저 를 <xref:System.IntPtr> `int` 변환하고 관련 정수 상수에 대해 테스트합니다. 일치하는 값이 없는 경우 필요한 형식의 개체로 변환하고 계속합니다.

 이 예제는 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>을 참조하십시오.

## <a name="ole-return-values-passed-as-out-parameters"></a>[out] 매개 변수로 전달된 OLE 반환 값
 COM 인터페이스에 `retval` 반환 값이 있지만 `int` return 값과 interop 어셈블리 메서드 프로토타입에 추가 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [out] 배열 매개 변수가 있는 메서드를 찾습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 방법 프로토타입에는 COM 인터페이스 방법보다 하나의 매개 변수가 하나 더 있기 때문에 이러한 메서드는 특별한 처리가 필요하다는 것이 분명해야 합니다.

 OLE 활동을 처리하는 많은 COM 인터페이스는 OLE 상태에 대한 정보를 인터페이스의 `retval` 반환 값에 저장된 호출 프로그램으로 다시 보냅니다. 반환 값을 사용하는 대신 해당 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop 어셈블리 메서드는 [out] 배열 매개 변수에 저장된 호출 프로그램으로 정보를 다시 보냅니다.

 이러한 메서드의 관리되는 구현은 [out] 매개 변수와 동일한 형식의 단일 요소 배열을 만들어 매개 변수에 넣어야 합니다. 배열 요소의 값은 적절한 COM `retval`과 같아야 합니다.

 이 형식의 인터페이스를 호출하는 관리되는 메서드는 [out] 배열에서 첫 번째 요소를 끌어내야 합니다. 이 요소는 해당 COM 인터페이스에서 `retval` 반환 값인 것처럼 처리될 수 있습니다.

## <a name="see-also"></a>참조
- [비관리 코드와의 상호 운용](/dotnet/framework/interop/index)

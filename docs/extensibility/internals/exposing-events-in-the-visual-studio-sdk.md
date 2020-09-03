---
title: Visual Studio SDK에서 이벤트 노출 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- events [Visual Studio], exposing
- automation [Visual Studio SDK], exposing events
ms.assetid: 70bbc258-c221-44f8-b0d7-94087d83b8fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48f1e0ea0dcd07bbc26fc89d5c61a6a5941d4727
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708482"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>Visual Studio SDK에서 이벤트 노출
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 자동화를 사용 하 여 이벤트를 원본으로 지정할 수 있습니다. 프로젝트 및 프로젝트 항목에 대 한 이벤트를 원본으로 하는 것이 좋습니다.

 이벤트는 <xref:EnvDTE.DTEClass.Events%2A> 개체 또는 <xref:EnvDTE.DTEClass.GetObject%2A> (예:)에서 자동화 소비자에 의해 검색 됩니다 `GetObject("EventObjectName")` . 환경에서는 또는 플래그를 사용 하 여를 호출 하 여 `IDispatch::Invoke` `DISPATCH_METHOD` `DISPATCH_PROPERTYGET` 이벤트를 반환 합니다.

 다음 프로세스는 VSPackage 특정 이벤트가 반환 되는 방법을 설명 합니다.

1. 환경이 시작 됩니다.

2. 모든 Vspackage의 **Automation**, **Automationevents**및 **automationevents** 키 아래에 있는 모든 값 이름을 레지스트리에서 읽고 해당 이름을 테이블에 저장 합니다.

3. 자동화 소비자는를 호출 합니다 .이 예제에서는 `DTE.Events.AutomationProjectsEvents` 또는 `DTE.Events.AutomationProjectItemsEvents` 입니다.

4. 환경에서는 테이블에서 문자열 매개 변수를 찾고 해당 VSPackage를 로드 합니다.

5. 환경에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 호출에 전달 된 이름을 사용 하 여 메서드를 호출 합니다 .이 예제에서는 `AutomationProjectsEvents` 또는 `AutomationProjectItemsEvents` 입니다.

6. VSPackage는 및와 같은 메서드를 포함 하는 루트 개체를 만든 `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` 다음, 개체에 대 한 IDispatch 포인터를 반환 합니다.

7. 환경에서는 automation 호출에 전달 된 이름을 기반으로 적절 한 메서드를 호출 합니다.

8. `get_`메서드는 인터페이스와 인터페이스를 둘 다 구현 하 `IConnectionPointContainer` `IConnectionPoint` 고를 개체에 반환 하는 또 다른 IDispatch 기반 이벤트 개체 `IDispatchpointer` 를 만듭니다.

   자동화를 사용 하 여 이벤트를 노출 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 레지스트리에 추가 하는 문자열에 응답 하 고이를 감시 해야 합니다. 기본 프로젝트 샘플에서 문자열은 *BscProjectsEvents* 및 *BscProjectItemsEvents*입니다.

## <a name="registry-entries-from-the-basic-project-sample"></a>기본 프로젝트 샘플의 레지스트리 항목
 이 섹션에서는 레지스트리에 자동화 이벤트 값을 추가할 수 있는 위치를 보여 줍니다.

 **[HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\8.0\Packages \\<PkgGUID \> \Automationevents]**

 **Automationprojectevents** = 개체를 반환 `AutomationProjectEvents` 합니다.

 **AutomationProjectItemEvents** = 개체를 반환 `AutomationProjectItemsEvents` 합니다.

|Name|Type|범위|설명|
|----------|----------|-----------|-----------------|
|기본값 (@)|REG_SZ|사용 안 함|사용되지 않습니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.|
|*AutomationProjectsEvents*|REG_SZ|이벤트 개체의 이름입니다.|키 이름만 관련 됩니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.<br /><br /> 이 예제는 기본 프로젝트 샘플에서 제공 됩니다.|
|*AutomationProjectItemEvents*|REG_SZ|이벤트 개체의 이름|키 이름만 관련 됩니다. 설명서에 대 한 데이터 필드를 사용할 수 있습니다.<br /><br /> 이 예제는 기본 프로젝트 샘플에서 제공 됩니다.|

 자동화 소비자가 이벤트 개체를 요청 하는 경우 VSPackage에서 지 원하는 모든 이벤트에 대 한 메서드가 있는 루트 개체를 만듭니다. 환경에서 `get_` 이 개체에 대해 적절 한 메서드를 호출 합니다. 예를 들어 `DTE.Events.AutomationProjectsEvents` 가 호출 되는 경우 `get_AutomationProjectsEvents` 루트 개체에 대 한 메서드가 호출 됩니다.

 ![Visual Studio 프로젝트 이벤트](../../extensibility/internals/media/projectevents.gif "ProjectEvents") 이벤트에 대 한 자동화 모델

 클래스는 `CProjectEventsContainer` *BscProjectsEvents*에 대 한 소스 개체를 나타내며 `CProjectItemsEventsContainer` *BscProjectItemsEvents*의 원본 개체를 나타냅니다.

 대부분의 이벤트 개체는 필터 개체를 사용 하기 때문에 대부분의 경우에는 모든 이벤트 요청에 대해 새 개체를 반환 해야 합니다. 이벤트를 발생 시킬 때이 필터를 선택 하 여 이벤트 처리기가 호출 되는지 확인 합니다.

 *Automationevents. h* 및 *automationevents .cpp* 에는 다음 표에 나와 있는 클래스의 선언과 구현이 포함 되어 있습니다.

|클래스|설명|
|-----------|-----------------|
|`CAutomationEvents`|개체에서 검색 되는 이벤트 루트 개체를 구현 `DTE.Events` 합니다.|
|`CProjectsEventsContainer` 및 `CProjectItemsEventsContainer`|해당 이벤트를 발생 시키는 이벤트 소스 개체를 구현 합니다.|

 다음 코드 예제에서는 이벤트 개체에 대 한 요청에 응답 하는 방법을 보여 줍니다.

```cpp
STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
{
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

    if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        //Is the requested name our Projects object?
    {
        return GetAutomationProjects(ppIDispatch);
        // Gets our Projects object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        //Is the requested name our ProjectsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectEvents object.
    }
    else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  //Is the requested name our ProjectsItemsEvents object?
    {
        return CAutomationEvents::GetAutomationEvents(ppIDispatch);
          // Gets our ProjectItemsEvents object.
    }
    return E_INVALIDARG;
}
```

 위의 코드에서 `g_wszAutomationProjects` 는 프로젝트 컬렉션 (FigProjectItemEvents*프로젝트*)의 이름이 고 ()는 `g_wszAutomationProjectsEvents` *FigProjectsEvents* `g_wszAutomationProjectItemsEvents` VSPackage 구현에서 소스인 프로젝트 항목 및 프로젝트 항목*FigProjectItemEvents*이벤트의 이름입니다.

 이벤트 개체는 동일한 중앙 위치인 개체에서 검색 됩니다 `DTE.Events` . 이러한 방식으로 모든 이벤트 개체는 함께 그룹화 되므로 최종 사용자가 전체 개체 모델을 검색 하 여 특정 이벤트를 찾을 필요가 없습니다. 이를 통해 시스템 수준 이벤트에 대 한 사용자 고유의 코드를 구현 하도록 요구 하는 대신 특정 VSPackage 개체를 제공할 수도 있습니다. 그러나 최종 사용자가 인터페이스에 대 한 이벤트를 찾아야 하는 경우 해당 `ProjectItem` 이벤트 개체가 검색 되는 위치에서 즉시 제거 되지 않습니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>

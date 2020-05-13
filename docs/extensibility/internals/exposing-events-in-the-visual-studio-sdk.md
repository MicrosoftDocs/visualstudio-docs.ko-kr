---
title: 비주얼 스튜디오 SDK에서 이벤트 노출 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708482"
---
# <a name="expose-events-in-the-visual-studio-sdk"></a>비주얼 스튜디오 SDK에서 이벤트 노출
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]을 사용하면 자동화를 사용하여 이벤트를 소스로 만들어 줍니다. 프로젝트 및 프로젝트 항목에 대한 이벤트를 소싱하는 것이 좋습니다.

 이벤트는 개체 <xref:EnvDTE.DTEClass.Events%2A> <xref:EnvDTE.DTEClass.GetObject%2A> 또는(예: `GetObject("EventObjectName")`)에서 자동화 소비자에 의해 검색됩니다. 환경은 `IDispatch::Invoke` 또는 `DISPATCH_PROPERTYGET` 플래그를 사용하여 이벤트를 반환합니다. `DISPATCH_METHOD`

 다음 프로세스는 VSPackage 관련 이벤트가 반환되는 방법을 설명합니다.

1. 환경이 시작됩니다.

2. 레지스트리에서 모든 값 이름을 **자동화,** **AutomationEvents**및 **AutomationProperties** 모든 VSPackage의 키를 읽고 해당 이름을 테이블에 저장합니다.

3. 자동화 소비자는 이 예제에서 `DTE.Events.AutomationProjectsEvents` `DTE.Events.AutomationProjectItemsEvents`호출하거나 .

4. 환경은 테이블에서 문자열 매개 변수를 찾아 해당 VSPackage를 로드합니다.

5. 환경은 호출에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 전달된 이름을 사용하여 메서드를 호출합니다. 이 예제에서는 `AutomationProjectsEvents` `AutomationProjectItemsEvents`또는 .

6. VSPackage와 같은 `get_AutomationProjectsEvents` `get_AutomationProjectItemEvents` 메서드가 있는 루트 개체를 만들고 IDispatch 포인터를 개체에 반환합니다.

7. 환경은 자동화 호출에 전달된 이름에 따라 적절한 메서드를 호출합니다.

8. 메서드는 `get_` `IConnectionPointContainer` 인터페이스와 `IConnectionPoint` 인터페이스를 모두 구현 하 고 개체에 반환 `IDispatchpointer` 하는 다른 IDispatch 기반 이벤트 개체를 만듭니다.

   자동화를 사용하여 이벤트를 노출하려면 레지스트리에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 추가하는 문자열에 응답하고 감시해야 합니다. 기본 프로젝트 샘플에서 문자열은 *BscProjectEvents* 및 *BscProjectItems이벤트입니다.*

## <a name="registry-entries-from-the-basic-project-sample"></a>기본 프로젝트 샘플의 레지스트리 항목
 이 섹션에서는 레지스트리에 자동화 이벤트 값을 추가할 위치를 보여 주며 있습니다.

 **[HKEY_LOCAL_MACHINE\SOFTWARE\마이크로소프트\비주얼 스튜디오\8.0\패키지\\<PkgGUID\>\AutomationEvents]**

 **자동화프로젝트이벤트** = `AutomationProjectEvents` 개체를 반환합니다.

 **자동화프로젝트항목이벤트** = `AutomationProjectItemsEvents` 개체를 반환합니다.

|이름|Type|범위|설명|
|----------|----------|-----------|-----------------|
|기본값 (@)|REG_SZ|사용 안 함|사용되지 않습니다. 문서화에 데이터 필드를 사용할 수 있습니다.|
|*자동화프로젝트이벤트*|REG_SZ|이벤트 개체의 이름입니다.|키 이름만 관련이 있습니다. 문서화에 데이터 필드를 사용할 수 있습니다.<br /><br /> 이 예제는 기본 프로젝트 샘플에서 제공됩니다.|
|*자동화프로젝트항목이벤트*|REG_SZ|이벤트 개체의 이름|키 이름만 관련이 있습니다. 문서화에 데이터 필드를 사용할 수 있습니다.<br /><br /> 이 예제는 기본 프로젝트 샘플에서 제공됩니다.|

 자동화 소비자가 이벤트 개체를 요청하는 경우 VSPackage가 지원하는 모든 이벤트에 대한 메서드가 있는 루트 개체를 만듭니다. 환경은 이 `get_` 개체에 대한 적절한 메서드를 호출합니다. 예를 들어 `DTE.Events.AutomationProjectsEvents` 호출된 경우 `get_AutomationProjectsEvents` 루트 개체의 메서드가 호출됩니다.

 ![비주얼 스튜디오 프로젝트 이벤트](../../extensibility/internals/media/projectevents.gif "ProjectEvents") 이벤트에 대한 자동화 모델

 클래스는 `CProjectEventsContainer` *BscProjectEvents의*소스 개체를 `CProjectItemsEventsContainer` 나타내고 *BscProjectItemsEvents의*소스 개체를 나타냅니다.

 대부분의 이벤트 개체는 필터 개체를 사용하므로 대부분의 경우 모든 이벤트 요청에 대해 새 개체를 반환해야 합니다. 이벤트를 발생시 이 필터를 확인하여 이벤트 처리기가 호출되고 있는지 확인합니다.

 *AutomationEvents.h* 및 *AutomationEvents.cpp는* 다음 표에 클래스의 선언 및 구현을 포함합니다.

|클래스|설명|
|-----------|-----------------|
|`CAutomationEvents`|개체에서 검색된 이벤트 루트 개체를 구현합니다. `DTE.Events`|
|`CProjectsEventsContainer` 및 `CProjectItemsEventsContainer`|해당 이벤트를 발생 시키는 이벤트 원본 개체를 구현 합니다.|

 다음 코드 예제에서는 이벤트 개체에 대한 요청에 응답하는 방법을 보여 주며 있습니다.

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

 위의 `g_wszAutomationProjects` 코드에서 프로젝트 컬렉션 *(FigProjects)* `g_wszAutomationProjectsEvents` *(FigProjectEvents)* 및 `g_wszAutomationProjectItemsEvents` *(FigProjectItemEvents)의*이름은 VSPackage 구현에서 소스되는 프로젝트 이벤트 및 프로젝트 항목 이벤트의 이름입니다.

 이벤트 개체는 동일한 중앙 위치인 `DTE.Events` 개체에서 검색됩니다. 이렇게 하면 최종 사용자가 특정 이벤트를 찾기 위해 전체 개체 모델을 찾아볼 필요가 없도록 모든 이벤트 개체가 함께 그룹화됩니다. 또한 시스템 전체 이벤트에 대해 고유한 코드를 구현해야 하는 대신 특정 VSPackage 개체를 제공할 수 있습니다. 그러나 `ProjectItem` 인터페이스에 대한 이벤트를 찾아야 하는 최종 사용자의 경우 해당 이벤트 개체가 검색되는 위치를 즉시 확인할 수 없습니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>

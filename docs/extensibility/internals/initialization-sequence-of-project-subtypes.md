---
title: 프로젝트 하위 유형의 초기화 순서 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707626"
---
# <a name="initialization-sequence-of-project-subtypes"></a>프로젝트 하위 형식의 초기화 시퀀스
환경은 기본 프로젝트 팩터리 구현을 호출하여 프로젝트를 구성합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 프로젝트 하위 유형의 구성은 환경이 프로젝트 파일의 확장명명명부에 대한 프로젝트 유형 GUID 목록이 비어 있지 않다고 판단할 때 시작됩니다. 프로젝트 파일 확장자 및 프로젝트 GUID는 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 프로젝트가 프로젝트 유형인지 여부를 지정합니다. 예를 들어 .vbproj 확장 및 {F184B08F-C81C-45F6-A57F-5ABD9991F28F}는 프로젝트를 식별합니다. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]

## <a name="environments-initialization-of-project-subtypes"></a>환경의 프로젝트 하위 유형 초기화
 다음 절차에서는 여러 프로젝트 하위 유형으로 집계된 프로젝트 시스템의 초기화 순서를 자세히 설명합니다.

1. 환경은 기본 프로젝트를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>호출하고 프로젝트가 프로젝트 파일을 구문 분석하는 동안 집계 프로젝트 유형 GUID목록이 `null`아님을 발견합니다. 프로젝트는 프로젝트를 직접 생성하지 않습니다.

2. 이 프로젝트는 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> 환경의 메서드 구현을 사용하여 프로젝트 하위 유형을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 만들기 위해 서비스를 호출합니다. 이 메서드 내에서 환경은 가장 바깥쪽 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>하위 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> 문자로 시작하여 프로젝트 유형 GUID 목록을 걷는 동안 의 구현 및 메서드에 대한 재귀 함수 호출을 만듭니다.

     다음은 초기화 단계에 대해 자세히 설명합니다.

    1. 환경의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 메서드 구현은 다음 `HrCreateInnerProj` 함수 선언을 사용하여 메서드를 호출합니다.

         \<코드콘텐츠플레이스홀더>0</CodeContentPlaceHolder>

         이 함수가 처음으로 호출되면, 즉 가장 바깥쪽 프로젝트 하위 유형에 `pOuter` `pOwner` 대해 매개 `null` 변수가 전달되고 함수가 가장 `IUnknown` `pOuter`바깥쪽 프로젝트 하위 유형을 로 설정합니다.

    2. 다음으로 환경 `HrCreateInnerProj` 호출 목록에서 두 번째 프로젝트 유형 GUID가 있는 함수입니다. 이 GUID는 집계 시퀀스의 기본 프로젝트를 향해 들어오는 두 번째 내부 프로젝트 하위 유형에 해당합니다.

    3. 은 `pOuter` 이제 가장 `IUnknown` 바깥쪽 프로젝트 하위 유형을 `HrCreateInnerProj` 가리키고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 있으며 구현 다음에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>구현을 호출합니다. 메서드에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 가장 바깥쪽 프로젝트 하위 유형의 제어를 `IUnknown` `pOuter`전달합니다. 소유 된 프로젝트 (내부 프로젝트 하위 유형)는 여기에 집계 프로젝트 개체를 만들어야합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 메서드 구현에서는 집계되는 내부 프로젝트의 `IUnknown` 포인터를 전달합니다. 이러한 두 메서드는 집계 개체를 만들고 구현에서는 COM 집계 규칙을 따라야 프로젝트 하위 유형이 참조 수를 자체적으로 보유하지 않도록 해야 합니다.

    4. `HrCreateInnerProj`구현을 호출합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 이 메서드에서 프로젝트 하위 형식은 초기화 작업을 수행합니다. 예를 들어 에서 솔루션 이벤트를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>등록할 수 있습니다.

    5. `HrCreateInnerProj`은 목록의 마지막 GUID(기본 프로젝트)에 도달할 때까지 재귀적으로 호출됩니다. 이러한 각 호출에 대해 c부터 d까지의 단계가 반복됩니다. `pOuter`은 각 집계 수준에 `IUnknown` 대한 가장 바깥쪽 프로젝트 하위 유형을 가리킵니다.

## <a name="example"></a>예제

다음 예제에서는 환경에 의해 구현되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 메서드의 대략적인 표현으로 프로그래밍 프로세스를 자세히 설명합니다. 코드는 예에 불과합니다. 컴파일할 수 없으며 명확성을 위해 모든 오류 검사가 제거되었습니다.

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)

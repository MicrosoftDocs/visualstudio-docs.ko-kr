---
title: 프로젝트 하위 형식의 초기화 순서 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c5594d54c188c2f561dd66229e808e48068ba41a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192664"
---
# <a name="initialization-sequence-of-project-subtypes"></a>프로젝트 하위 형식의 초기화 시퀀스
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

환경에서는의 기본 프로젝트 팩터리 구현을 호출 하 여 프로젝트를 생성 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . 프로젝트 하위 형식 생성은 환경에서 프로젝트 파일 확장명에 대 한 프로젝트 형식 GUID 목록이 비어 있지 않은 것으로 확인 될 때 시작 됩니다. 프로젝트 파일 확장명 및 프로젝트 GUID는 프로젝트가 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 또는 프로젝트 형식 인지 여부를 지정 합니다 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . 예를 들어 .vbproj 확장명 및 {F184B08F-C81C-45F6-A57F-5ABD9991F28F}는 프로젝트를 식별 합니다. [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]  
  
## <a name="environments-initialization-of-project-subtypes"></a>환경의 프로젝트 하위 형식 초기화  
 다음 절차에서는 여러 프로젝트 하위 형식으로 집계 된 프로젝트 시스템의 초기화 순서에 대해 자세히 설명 합니다.  
  
1. 환경에서는 기본 프로젝트를 호출 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 고 프로젝트에서 해당 프로젝트 파일을 구문 분석 하는 동안 집계 프로젝트 형식 guid 목록이 없다는 것을 검색 합니다 `null` . 프로젝트 중단 직접 프로젝트를 만듭니다.  
  
2. 프로젝트는 `QueryService` 서비스에서를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> 하 여 환경의 메서드 구현을 사용 하 여 프로젝트 하위 유형을 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> . 이 메서드 내에서 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> 가장 바깥쪽 프로젝트 하위 형식부터 시작 하 여 프로젝트 형식 guid의 목록을 탐색 하는 동안, 및 메서드의 구현에 대 한 재귀 함수 호출을 수행 합니다.  
  
    다음은 초기화 단계를 자세히 설명 합니다.  
  
   1. 환경의 메서드 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 다음 함수 선언을 사용 하 여 ' HrCreateInnerProj ' ' ' 메서드를 호출 합니다.  
  
       ```  
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
           BOOL *pfCancelled  
       )  
       ```  
  
        가장 바깥쪽 프로젝트 하위 형식에 대해이 함수를 처음 호출 하는 경우 및 매개 변수는 `pOuter` `pOwner` 로 전달 되 `null` 고 함수는 가장 바깥쪽 프로젝트 하위 형식을로 설정 합니다 `IUnknown` `pOuter` .  
  
   2. 그런 다음 환경에서는 `HrCreateInnerProj` 목록에서 두 번째 프로젝트 형식 GUID를 사용 하 여 함수를 호출 합니다. 이 GUID는 집계 시퀀스의 기본 프로젝트를 중심으로 하는 두 번째 내부 프로젝트 하위 유형 단계별 실행에 해당 합니다.  
  
   3. `pOuter`이제는 가장 바깥쪽 프로젝트 하위 형식의을 가리키고의 구현을 `IUnknown` 호출한 다음 구현에 대 한 호출을 `HrCreateInnerProj` 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>메서드에서 `IUnknown` 가장 바깥쪽 프로젝트 하위 형식 ()의 제어를 전달 합니다 `pOuter` . 소유 하는 프로젝트 (내부 프로젝트 하위 형식)는 여기에 집계 프로젝트 개체를 만들어야 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>메서드 구현에서는 집계할 내부 프로젝트의에 대 한 포인터를 전달 `IUnknown` 합니다. 이러한 두 메서드는 집계 개체를 만들며, 프로젝트 하위 형식에서 참조 횟수를 포함 하지 않도록 하려면 구현에서 COM 집계 규칙을 따라야 합니다.  
  
   4. `HrCreateInnerProj` 의 구현을 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> 합니다. 이 메서드에서 프로젝트 하위 형식이 초기화 작업을 수행 합니다. 예를 들어에서 솔루션 이벤트를 등록할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .  
  
   5. `HrCreateInnerProj` 는 목록의 마지막 GUID (기본 프로젝트)에 도달할 때까지 재귀적으로 호출 됩니다. 이러한 각 호출에 대해 c ~ d 단계를 반복 합니다. `pOuter` 각 집계 수준에 대해 가장 바깥쪽 프로젝트 하위 유형을 가리킵니다 `IUnknown` .  
  
   다음 예제에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> 환경에 의해 구현 되는 메서드를 대략적으로 표현 하는 프로그래밍 프로세스를 자세히 설명 합니다. 코드는 단지 예입니다. 이는 컴파일되지 않으며 모든 오류 검사가 명확 하 게 제거 되었습니다.  
  
## <a name="example"></a>예제  
  
### <a name="code"></a>코드  
  
```  
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
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)

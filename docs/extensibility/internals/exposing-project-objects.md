---
title: 프로젝트 객체 노출 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708478"
---
# <a name="expose-project-objects"></a>프로젝트 객체 노출

사용자 지정 프로젝트 유형은 자동화 인터페이스를 사용하여 프로젝트에 액세스할 수 있도록 자동화 개체를 제공할 수 있습니다. 모든 프로젝트 유형은 IDE에서 열려 있는 모든 <xref:EnvDTE.Solution>프로젝트의 컬렉션을 포함하는 에서 액세스되는 표준 <xref:EnvDTE.Project> 자동화 개체를 제공해야 합니다. 프로젝트의 각 항목은 <xref:EnvDTE.ProjectItem> `Project.ProjectItems`에 액세스하는 개체에 의해 노출될 것으로 예상됩니다. 이러한 표준 자동화 개체 외에도 프로젝트는 프로젝트별 자동화 개체를 제공하도록 선택할 수 있습니다.

을 사용하여 `DTE.<customObjectName>` 루트 DTE 개체에서 늦게 바인딩된 에 액세스할 수 있는 `DTE.GetObject("<customObjectName>")`사용자 지정 루트 수준 자동화 개체를 만들 수 있습니다. 예를 들어 Visual C++는 을 `DTE.VCProjects` `DTE.GetObject("VCProjects")`사용하여 액세스할 수 있는 *VCProject라는* C++ 프로젝트별 프로젝트 컬렉션을 만듭니다. 프로젝트 형식에 `Project.Object`고유한 을 만들 수도 있고, `Project.CodeModel`가장 파생된 개체에 대해 쿼리할 수 `ProjectItem`있는 및 `ProjectItem.Object` 노출및 `ProjectItem.FileCodeModel`을 포함하는 를 만들 수도 있습니다.

프로젝트가 사용자 지정 프로젝트별 프로젝트 컬렉션을 노출하는 일반적인 규칙입니다. 예를 들어, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 다음 사용 `DTE.VCProjects` 하 여 액세스할 수 있는 `DTE.GetObject("VCProjects")`C ++ 특정 프로젝트 컬렉션을 만듭니다. 프로젝트 형식에 `Project.Object`고유한 을 만들 수도 있고, `Project.CodeModel`에 대해 가장 파생된 개체에 대해 `ProjectItem`쿼리할 수 `ProjectItem.Object`있는 `ProjectItem.FileCodeModel`및 을 노출하는 .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>프로젝트에 VSPackage 관련 개체를 기여하려면

1. VSPackage의 *.pkgdef* 파일에 적절한 키를 추가합니다.

     예를 들어 C++ 언어 프로젝트의 *.pkgdef* 설정은 다음과 같습니다.

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. 다음 예제와 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 같이 메서드에서 코드를 구현합니다.

    ```cpp
    STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
    {
    ExpectedPtrRet(pszPropName);
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

        if (m_fZombie)
            return E_UNEXPECTED;

        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        {
            return GetAutomationProjects(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        return E_INVALIDARG;
    }
    ```

     코드에서 프로젝트 `g_wszAutomationProjects` 컬렉션의 이름입니다. 메서드는 `GetAutomationProjects` `Projects` 인터페이스를 구현 하는 개체를 `IDispatch` 만들고 다음 코드 예제와 같이 호출 개체에 대 한 포인터를 반환 합니다.

    ```cpp
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)
    {
        ExpectedPtrRet(ppIDispatch);
        *ppIDispatch = NULL;

        if (!m_srpAutomationProjects)
        {
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);
            IfFailRet(hr);
            ExpectedExprRet(m_srpAutomationProjects != NULL);
        }
        return m_srpAutomationProjects.CopyTo(ppIDispatch);
    }
    ```

     자동화 개체의 고유한 이름을 선택합니다. 이름 충돌은 예측할 수 없으며 충돌하면 여러 프로젝트 형식이 동일한 이름을 사용하는 경우 충돌하는 개체 이름이 임의로 throw됩니다. 회사 이름 또는 자동화 개체의 이름에 제품 이름의 일부 고유한 측면을 포함해야 합니다.

     사용자 `Projects` 지정 컬렉션 개체는 프로젝트 자동화 모델의 나머지 부분에 대한 편리한 진입점입니다. 프로젝트 개체는 <xref:EnvDTE.Solution> 프로젝트 컬렉션에서도 액세스할 수 있습니다. 소비자에게 `Projects` 컬렉션 개체를 제공하는 적절한 코드 및 레지스트리 항목을 만든 후에는 구현에서 프로젝트 모델에 대한 나머지 표준 개체를 제공해야 합니다. 자세한 내용은 [프로젝트 모델링](../../extensibility/internals/project-modeling.md)을 참조하십시오.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>

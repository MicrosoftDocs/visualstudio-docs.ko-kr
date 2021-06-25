---
title: 프로젝트 개체 | 노출 Microsoft Docs
description: 자동화 인터페이스를 사용하여 프로젝트에 액세스할 수 있는 자동화 개체를 제공하여 Visual Studio 사용자 지정 프로젝트 형식에 대한 개체를 노출하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3e89b4c80d64bedb77e68c648ba993794f8b658
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898294"
---
# <a name="expose-project-objects"></a>프로젝트 개체 노출

사용자 지정 프로젝트 형식은 자동화 인터페이스를 사용하여 프로젝트에 액세스할 수 있도록 자동화 개체를 제공할 수 있습니다. 모든 프로젝트 형식은 <xref:EnvDTE.Project> IDE에서 열려 있는 모든 프로젝트의 컬렉션을 포함하는 에서 액세스하는 표준 자동화 개체를 제공해야 <xref:EnvDTE.Solution> 합니다. 프로젝트의 각 항목은 로 액세스되는 개체에 의해 노출되어야 <xref:EnvDTE.ProjectItem> `Project.ProjectItems` 합니다. 프로젝트는 이러한 표준 자동화 개체 외에도 프로젝트별 자동화 개체를 제공하도록 선택할 수 있습니다.

또는 을 사용하여 루트 DTE 개체에서 지연 바인딩된 개체에 액세스할 수 있는 사용자 지정 루트 수준 자동화 개체를 만들 수 `DTE.<customObjectName>` `DTE.GetObject("<customObjectName>")` 있습니다. 예를 들어 Visual C++ 또는 을 사용하여 액세스할 수 있는 *VCProjects라는* C++ 프로젝트별 프로젝트 컬렉션을 `DTE.VCProjects` 만듭니다. `DTE.GetObject("VCProjects")` `Project.Object`또한 프로젝트 형식에 대해 고유한 , 가장 `Project.CodeModel` 많이 파생된 개체에 대해 쿼리할 수 있는 , 및 를 노출하는 를 만들 수도 `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` 있습니다.

프로젝트에서 사용자 지정 프로젝트별 프로젝트 컬렉션을 노출하는 것은 일반적인 규칙입니다. 예를 들어 는 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 또는 을 사용하여 액세스할 수 있는 C++ 특정 프로젝트 컬렉션을 만듭니다. `DTE.VCProjects` `DTE.GetObject("VCProjects")` `Project.Object`또한 프로젝트 형식에 대해 고유한 , 가장 `Project.CodeModel` 많이 파생된 개체에 대해 쿼리할 수 있는 , 및 를 노출하는 를 만들 수도 `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` 있습니다.

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>프로젝트에 VSPackage 관련 개체를 기여하려면

1. VSPackage의 *.pkgdef* 파일에 적절한 키를 추가합니다.

     예를 들어 C++ 언어 프로젝트에 대한 *.pkgdef* 설정은 다음과 같습니다.

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>다음 예제와 같이 메서드에서 코드를 구현합니다.

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

     코드에서 `g_wszAutomationProjects` 는 프로젝트 컬렉션의 이름입니다. `GetAutomationProjects`메서드는 `Projects` 다음 코드 예제와 같이 인터페이스를 구현하고 `IDispatch` 호출하는 개체에 대한 포인터를 반환하는 개체를 만듭니다.

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

     자동화 개체의 고유한 이름을 선택합니다. 이름 충돌은 예측할 수 없으며 여러 프로젝트 형식이 동일한 이름을 사용하는 경우 충돌하는 개체 이름이 임의로 throw됩니다. Automation 개체의 이름에 회사 이름 또는 제품 이름의 일부 고유한 측면을 포함해야 합니다.

     사용자 지정 `Projects` 컬렉션 개체는 프로젝트 자동화 모델의 나머지 부분에 대한 편리한 진입점입니다. 프로젝트 컬렉션에서도 프로젝트 개체에 액세스할 수 <xref:EnvDTE.Solution> 있습니다. 소비자에게 컬렉션 개체를 제공하는 적절한 코드 및 레지스트리 항목을 만든 후에는 `Projects` 구현에서 프로젝트 모델에 대한 나머지 표준 개체를 제공해야 합니다. 자세한 내용은 [프로젝트 모델링을 참조하세요.](../../extensibility/internals/project-modeling.md)

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>

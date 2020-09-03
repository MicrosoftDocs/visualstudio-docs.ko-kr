---
title: 프로젝트 개체 노출 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196649"
---
# <a name="exposing-project-objects"></a>프로젝트 개체 노출
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자 지정 프로젝트 형식은 자동화 인터페이스를 사용 하 여 프로젝트에 대 한 액세스를 허용 하기 위해 자동화 개체를 제공할 수 있습니다. 모든 프로젝트 형식은 <xref:EnvDTE.Project> <xref:EnvDTE.Solution> IDE에 열려 있는 모든 프로젝트의 컬렉션을 포함 하는에서 액세스 되는 표준 자동화 개체를 제공 해야 합니다. 프로젝트의 각 항목은로 액세스 하는 개체에 의해 노출 될 것으로 예상 됩니다 <xref:EnvDTE.ProjectItem> <xref:EnvDTE.Project.ProjectItems> . 이러한 표준 자동화 개체 외에도 프로젝트는 프로젝트별 자동화 개체를 제공 하도록 선택할 수 있습니다.  
  
 또는을 사용 하 여 루트 DTE 개체에서 런타임에 바인딩할 수 있는 사용자 지정 루트 수준 자동화 개체를 만들 수 `DTE.<customeObjectName>` 있습니다 `DTE.GetObject(“<customObjectName>”)` . 예를 들어 Visual C++은 DTE를 사용 하 여 액세스할 수 있는 "VCProjects" 라는 c + + 프로젝트 관련 프로젝트 컬렉션을 만듭니다. VCProjects 또는 DTE. GetObject ("VCProjects"). 프로젝트 형식에 대해 고유 하 고 프로젝트를 만들 수도 있습니다. 개체는 가장 많이 파생 되는 개체에 대해 쿼리할 수 있는 프로젝트. CodeModel. FileCodeModel 및 projectitem을 노출 하는 ProjectItem입니다.  
  
 프로젝트에서 사용자 지정 프로젝트별 프로젝트 컬렉션을 노출 하는 것이 일반적인 규칙입니다. 예를 들어은 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 또는를 사용 하 여 액세스할 수 있는 c + + 특정 프로젝트 컬렉션을 만듭니다 `DTE.VCProjects` `DTE.GetObject("VCProjects")` . `Project.Object`프로젝트 형식에 대해 고유한를 만들 수도 있습니다 `Project.CodeModel` .이 개체는 가장 많이 파생 되는 개체, 및를 노출 하는에 대해 쿼리할 수 있습니다 `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` .  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>프로젝트에 대 한 VSPackage 개체를 적용 하려면  
  
1. VSPackage의 .pkgdef 파일에 적절 한 키를 추가 합니다.  
  
     예를 들어 다음은 c + + 언어 프로젝트에 대 한. .pkgdef 설정입니다.  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>다음 예제와 같이 메서드의 코드를 구현 합니다.  
  
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
  
     코드에서 `g_wszAutomationProjects` 는 프로젝트 컬렉션의 이름입니다. `GetAutomationProjects`메서드는 `Projects` 다음 코드 예제와 같이 인터페이스를 구현 하는 개체를 만들고 호출 하는 `IDispatch` 개체에 대 한 포인터를 반환 합니다.  
  
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
  
     자동화 개체에 대 한 고유한 이름을 선택 해야 합니다. 이름 충돌을 예측할 수 없으며, 여러 프로젝트 형식에서 같은 이름을 사용 하는 경우 충돌이 발생 하면 충돌 하는 개체 이름이 임의로 throw 됩니다. Automation 개체의 이름에 회사 이름 또는 제품 이름의 일부 고유한 부분을 포함 해야 합니다.  
  
     사용자 지정 `Projects` 컬렉션 개체는 프로젝트 자동화 모델의 나머지 부분에 대 한 편리한 진입점입니다. 프로젝트 개체는 프로젝트 컬렉션 에서도 액세스할 수 <xref:EnvDTE.Solution> 있습니다. 컬렉션 개체를 소비자에 게 제공 하는 적절 한 코드 및 레지스트리 항목을 만든 후에는 `Projects` 구현에서 프로젝트 모델에 대 한 나머지 표준 개체를 제공 해야 합니다. 자세한 내용은 [프로젝트 모델링](../../extensibility/internals/project-modeling.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>

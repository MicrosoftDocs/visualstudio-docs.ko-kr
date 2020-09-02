---
title: '방법: 편집기 파일 형식 등록 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204113"
---
# <a name="how-to-register-editor-file-types"></a>방법: 편집기 파일 형식 등록
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기 파일 형식을 등록 하는 가장 쉬운 방법은 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] MPF (관리 패키지 프레임 워크) 클래스의 일부로 제공 되는 등록 특성을 사용 하는 것입니다. 네이티브에서 패키지를 구현 하는 경우 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 편집기와 연결 된 확장을 등록 하는 레지스트리 스크립트를 작성할 수도 있습니다.  
  
## <a name="registration-using-mpf-classes"></a>MPF 클래스를 사용 하 여 등록  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>MPF 클래스를 사용 하 여 편집기 파일 형식을 등록 하려면  
  
1. <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>VSPackage 클래스의 편집기에 대 한 적절 한 매개 변수를 클래스에 제공 합니다.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Where ". Sample "은이 편집기에 대해 등록 된 확장 이며" 32 "은 우선 순위 수준입니다.  
  
     는 `projectGuid` 에 정의 된 기타 파일 형식에 대 한 GUID입니다 <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . 결과 파일이 빌드 프로세스에 포함 되지 않도록 기타 파일 형식이 제공 됩니다.  
  
     `TemplateDir` 관리 되는 기본 편집기 샘플에 포함 된 템플릿 파일을 포함 하는 폴더를 나타냅니다.  
  
     `NameResourceID` 는 BasicEditorUI 프로젝트의 resource.h 파일에 정의 되며 편집기를 "내 편집기"로 식별 합니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드를 재정의합니다.  
  
     메서드 구현에서 메서드를 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 호출 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 하 고 아래와 같이 편집기 팩터리의 인스턴스를 전달 합니다.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     이 단계에서는 편집기 팩터리와 편집기 파일 확장명을 모두 등록 합니다.  
  
3. 편집기 팩터리를 등록 취소 합니다.  
  
     VSPackage가 삭제 되 면 편집기 팩터리가 자동으로 등록 취소 됩니다. 편집기 팩터리 개체가 인터페이스를 구현 하는 경우 <xref:System.IDisposable> `Dispose` 팩터리가로 등록 취소 된 후에 해당 메서드가 호출 됩니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>레지스트리 스크립트를 사용 하 여 등록  
 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]다음에 설명 된 것 처럼 레지스트리 스크립트를 사용 하 여 windows 레지스트리에 쓰도록 편집기 팩터리 및 파일 형식을 등록 합니다.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>레지스트리 스크립트를 사용 하 여 편집기 파일 형식을 등록 하려면  
  
1. 레지스트리 스크립트에서 `GUID_BscEditorFactory` 다음 레지스트리 스크립트의 섹션과 같이 편집기 팩터리와 편집기 팩터리 GUID 문자열을 정의 합니다. 또한 편집기 확장의 확장 및 우선 순위를 정의 합니다.  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     이 예제의 편집기 파일 확장명은 ".rtf"로 식별 되며 우선 순위는 "50"입니다. GUID 문자열은 BscEdit 샘플 프로젝트의 resource.h 파일에 정의 되어 있습니다.  
  
2. VSPackage를 등록 합니다.  
  
3. 편집기 팩터리를 등록 합니다.  
  
     편집기 팩터리가 구현에 등록 되어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 있습니다.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     GUID 문자열은 BscEdit 프로젝트의 resource.h 파일에 정의 되어 있습니다.

---
title: 편집기에 레거시 코드 적용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184912"
---
# <a name="adapting-legacy-code-to-the-editor"></a>레거시 코드를 편집기로 조정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 편집기에는 기존 코드 구성 요소에서 액세스할 수 있는 많은 기능이 있습니다. 다음 지침에서는 VSPackage 등의 비 MEF 구성 요소를 조정 하 여 편집기 기능을 사용 하는 방법을 보여 줍니다. 또한 어댑터를 사용 하 여 관리 코드와 비관리 코드 모두에서 편집기의 서비스를 가져오는 방법을 보여 줍니다.  
  
## <a name="editor-adapters"></a>편집기 어댑터  
 편집기 어댑터 또는 shim은 API의 클래스와 인터페이스도 노출 하는 편집기 개체의 래퍼입니다 <xref:Microsoft.VisualStudio.TextManager.Interop> . 어댑터를 사용 하 여 비 편집기 서비스 (예: Visual Studio shell 명령 및 편집기 서비스) 간을 이동할 수 있습니다. 편집기는 현재 Visual Studio에서 호스팅되는 방법입니다. 어댑터를 사용 하면 레거시 편집기 및 언어 서비스 확장도 Visual Studio에서 제대로 작동할 수 있습니다.  
  
## <a name="using-editor-adapters"></a>편집기 어댑터 사용  
 는 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 새 편집기 인터페이스와 레거시 인터페이스 간을 전환 하는 메서드와 어댑터를 만드는 메서드를 제공 합니다.  
  
 MEF 구성 요소 부분에서이 서비스를 사용 하는 경우 다음과 같이 서비스를 가져올 수 있습니다.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 비 MEF 구성 요소에서이 서비스를 사용 하려면이 항목의 뒷부분에 나오는 "MEF 구성 요소에서 Visual Studio 편집기 서비스 사용" 섹션의 지침을 따르세요.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>새 편집기 API와 레거시 API 간 전환  
 편집기 개체와 레거시 인터페이스 간을 전환 하려면 다음 메서드를 사용 합니다.  
  
|메서드|변환|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|<xref:Microsoft.VisualStudio.Text.ITextBuffer>을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>로 변환합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>을 <xref:Microsoft.VisualStudio.Text.ITextBuffer>로 변환합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>을 <xref:Microsoft.VisualStudio.Text.ITextBuffer>로 변환합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|<xref:Microsoft.VisualStudio.Text.Editor.ITextView>을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>로 변환합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>을 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>로 변환합니다.|  
  
## <a name="creating-adapters"></a>어댑터 만들기  
 레거시 인터페이스용 어댑터를 만들려면 다음 메서드를 사용 합니다.  
  
|메서드|변환|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>를 만듭니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|지정 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 에 대 한를 만듭니다 <xref:Microsoft.VisualStudio.Utilities.IContentType> .|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>를 만듭니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>를 만듭니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>에 대해 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>를 만듭니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>를 만듭니다.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>비관리 코드에서 어댑터 만들기  
 모든 어댑터 클래스는 로컬에서 생성 가능 하도록 등록 되며 함수를 사용 하 여 인스턴스화할 수 있습니다 `VsLocalCreateInstance()` .  
  
 모든 어댑터는. .의 vsshlids .h 파일에 정의 된 Guid를 사용 하 여 만들어집니다. Visual Studio SDK 설치의 \VisualStudioIntegration\Common\Inc\ 폴더입니다. VsTextBufferAdapter의 인스턴스를 만들려면 다음 코드를 사용 합니다.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>관리 코드에서 어댑터 만들기  
 관리 코드에서 관리 되지 않는 코드에 대해 설명한 것과 동일한 방법으로 어댑터를 공동 만들 수 있습니다. 어댑터를 만들고 조작할 수 있는 MEF 서비스를 사용할 수도 있습니다. 이러한 방식으로 어댑터를 가져오면 공동 만들 때 보다 세분화 된 제어를 사용할 수 있습니다.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>IVsTextView 용 어댑터를 만들려면  
  
1. Microsoft.VisualStudio.Editor.dll에 대 한 참조를 추가 합니다. `CopyLocal`이 `false`로 설정되어 있는지 확인합니다.  
  
2. <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>다음과 같이를 인스턴스화합니다.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. `CreateX()` 메서드를 호출합니다.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>비관리 코드에서 직접 Visual Studio 편집기 사용  
 VisualStudio 네임 스페이스 및 VSEditor 네임 스페이스는 COM 호출 가능 인터페이스를 IVx * 인터페이스로 노출 합니다. 예를 들어, VSEditor 인터페이스는 COM 버전의 인터페이스입니다 (예: VisualStudio). <xref:Microsoft.VisualStudio.Text.ITextBuffer> 에서 버퍼 `IVxTextBuffer` 스냅숏에 대 한 액세스 권한을 얻고, 버퍼를 수정 하 고, 버퍼에서 텍스트 변경 이벤트를 수신 하 고, 추적 지점과 범위를 만들 수 있습니다. 다음 단계에서는에서에 액세스 하는 방법을 보여 줍니다 `IVxTextBuffer` `IVsTextBuffer` .  
  
#### <a name="to-get-an-ivxtextbuffer"></a>IVxTextBuffer를 가져오려면  
  
1. IVx * 인터페이스에 대 한 정의는의 VSEditor 파일에 있습니다. Visual Studio SDK 설치의 \VisualStudioIntegration\Common\Inc\ 폴더입니다.  
  
2. 다음 코드에서는 메서드를 사용 하 여 텍스트 버퍼를 인스턴스화합니다 `IVsUserData->GetData()` . 다음 코드에서 `pData` 는 개체에 대 한 포인터입니다 `IVsUserData` .  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>비 MEF 구성 요소에서 Visual Studio 편집기 서비스 사용  
 MEF를 사용 하지 않고 Visual Studio 편집기의 서비스를 사용 하려는 기존 관리 코드 구성 요소가 있는 경우 ComponentModelHost VSPackage를 포함 하는 어셈블리에 대 한 참조를 추가 하 고 해당 SComponentModel 서비스를 가져와야 합니다.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>비 MEF 구성 요소에서 Visual Studio 편집기 구성 요소를 사용 하려면  
  
1. 에서 Microsoft.VisualStudio.ComponentModelHost.dll 어셈블리에 대 한 참조를 추가 합니다. Visual Studio 설치의 \Common7\IDE\ 폴더입니다. `CopyLocal`이 `false`로 설정되어 있는지 확인합니다.  
  
2. `IComponentModel`다음과 같이 Visual Studio 편집기 서비스를 사용 하려는 클래스에 전용 멤버를 추가 합니다.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. 구성 요소에 대 한 초기화 메서드에서 구성 요소 모델을 인스턴스화합니다.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. 그런 다음 `IComponentModel.GetService<T>()` 원하는 서비스에 대해 메서드를 호출 하 여 Visual Studio 편집기 서비스 중 하나를 가져올 수 있습니다.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```

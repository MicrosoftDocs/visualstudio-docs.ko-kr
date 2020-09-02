---
title: 단일 및 다중 탭 보기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - single and multi-tab views
ms.assetid: e3611704-349f-4323-b03c-f2b0a445d781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c308b4d6c7b90456255019ef57c6b9d544aefc77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699984"
---
# <a name="single-and-multi-tab-views"></a>단일 및 다중 탭 보기
편집기에서 다양 한 유형의 뷰를 만들 수 있습니다. 한 가지 예는 코드 편집기 창이 며 다른 하나는 폼 디자이너입니다.

 다중 탭 보기는 여러 탭이 있는 뷰입니다. 예를 들어 HTML 편집기의 맨 아래에는 두 개의 탭이 있습니다. **디자인** 및 **소스**는 각각 논리적 뷰입니다. 디자인 뷰에는 렌더링 된 웹 페이지가 표시 되 고 다른 페이지에는 웹 페이지를 구성 하는 HTML이 표시 됩니다.

## <a name="accessing-physical-views"></a>실제 뷰 액세스
 물리적 보기는 코드 또는 양식과 같은 버퍼의 데이터 뷰를 각각 나타내는 문서 뷰 개체를 호스팅합니다. 따라서 각 문서 보기 개체에는 물리적 뷰 (물리적 뷰 문자열 이라고 함)와 일반적으로 단일 논리적 뷰가 있습니다.

 그러나 경우에 따라 실제 뷰에는 둘 이상의 논리적 보기가 있을 수 있습니다. 일부 예는 나란히 보기가 포함 된 분할 창이 나 GUI/디자인 뷰 및 코드 숨김과 폼 뷰가 있는 폼 디자이너를 포함 하는 편집기입니다.

 편집기에서 사용 가능한 모든 물리적 보기에 액세스할 수 있게 하려면 편집기 팩터리에서 만들 수 있는 각 문서 보기 개체 형식에 대 한 고유한 실제 뷰 문자열을 만들어야 합니다. 예를 들어, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 편집기 팩터리는 코드 창과 폼 디자이너 창의 문서 뷰 개체를 만들 수 있습니다.

## <a name="creating-multi-tabbed-views"></a>다중 탭 뷰 만들기
 문서 뷰 개체는 고유한 물리적 뷰 문자열을 통해 물리적 뷰와 연결 되어야 하지만, 여러 가지 방법으로 데이터를 볼 수 있도록 물리적 보기에 여러 탭을 둘 수 있습니다. 이 다중 탭 구성에서는 모든 탭이 동일한 물리적 뷰 문자열과 연결 되지만 각 탭에는 서로 다른 논리 보기 GUID가 지정 됩니다.

 편집기에 대 한 다중 탭 뷰를 만들려면 인터페이스를 구현 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> 고 다른 논리 보기 GUID ( <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID> )를 만든 각 탭과 연결 합니다.

 Visual Studio HTML 편집기는 다중 탭 뷰가 있는 편집기의 예입니다. **디자인** 및 **소스** 탭이 있습니다. 이 기능을 사용 하기 위해 `LOGICALVIEWID_TextView` **디자인** 탭 및 `LOGICALVIEWID_Code` **원본** 탭의 각 탭에는 다른 논리 보기가 연결 됩니다.

 VSPackage는 적절 한 논리적 보기를 지정 하 여 양식 디자인, 코드 편집, 코드 디버깅 등의 특정 용도에 해당 하는 뷰에 액세스할 수 있습니다. 그러나 windows 중 하나는 NULL 문자열로 식별 되어야 하며,이는 기본 논리 뷰 ()와 일치 해야 합니다 `LOGVIEWID_Primary` .

 다음 표에서는 사용 가능한 논리 보기 값 및 해당 값을 보여 줍니다.

|LOGVIEWID GUID|권장 사용|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|편집기 팩터리의 기본/기본 뷰입니다.<br /><br /> 모든 편집기 팩터리는이 값을 지원 해야 합니다. 이 뷰에서는 NULL 문자열을 실제 뷰 문자열로 사용 해야 합니다. 논리적 뷰를 하나 이상이 값으로 설정 해야 합니다.|
|`LOGVIEWID_Debugging`|디버깅 뷰입니다. 일반적으로는 `LOGVIEWID_Debugging` 와 동일한 뷰에 매핑됩니다 `LOGVIEWID_Code` .|
|`LOGVIEWID_Code`|**코드 보기** 명령으로 시작 된 뷰입니다.|
|`LOGVIEWID_Designer`|**보기 폼** 명령으로 시작 된 뷰입니다.|
|`LOGVIEWID_TextView`|텍스트 편집기 뷰입니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>에서 액세스할 수 있는를 반환 하는 뷰입니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|`LOGVIEWID_UserChooseView`|사용자에 게 사용할 뷰를 선택 하 라는 메시지를 표시 합니다.|
|`LOGVIEWID_ProjectSpecificEditor`|**연결 프로그램** 대화 상자에 의해 전달 됩니다.<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 사용자가 "(프로젝트 기본 편집기)" 항목을 선택 하는 경우|

 논리적 보기 Guid는 확장 가능 하지만 VSPackage에 정의 된 논리 보기 Guid만 사용할 수 있습니다.

 종료 시 Visual Studio는 솔루션을 다시 열 때 문서 창을 다시 여는 데 사용할 수 있도록 편집기 팩터리의 GUID와 문서 창에 연결 된 실제 뷰 문자열을 유지 합니다. 솔루션이 닫힐 때 열려 있는 windows만 솔루션 (.suo) 파일에 저장 됩니다. 이러한 값은 `VSFPROPID_guidEditorType` `VSFPROPID_pszPhysicalView` 메서드의 매개 변수에 전달 된 및 값에 해당 합니다 `propid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> .

## <a name="example"></a>예
 이 코드 조각은 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> 사용 하 여을 구현 하는 뷰에 액세스 하는 방법을 보여 줍니다 `IVsCodeWindow` . 이 경우 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> 서비스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> `LOGVIEWID_TextView` 창 프레임에 대 한 포인터를 가져오는를 호출 하 고를 요청 하는 데 사용 됩니다. 문서 뷰 개체에 대 한 포인터는를 호출 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 고 값을 지정 하 여 가져옵니다 `VSFPROPID_DocView` . 문서 뷰 개체에서 `QueryInterface` 가에 대해 호출 됩니다 `IVsCodeWindow` . 이 경우 텍스트 편집기가 반환 되므로 메서드에서 반환 되는 문서 뷰 개체는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 코드 창이 됩니다.

```cpp
HRESULT CFindTool::GotoFileLocation(const WCHAR * szFile, long iLine, long iStart, long iLen)
{
  HRESULT hr;
  if (NULL == szFile || !*szFile)
    return E_INVALIDARG;

  if (iLine == -1L)
    return S_FALSE;

  VSITEMID                  itemid;
  VARIANT                   var;
  RECT                      rc;
  IVsUIShellOpenDocument *  pOpenDoc    = NULL;
  IVsCodeWindow *           pCodeWin    = NULL;
  IVsTextView *             pTextView   = NULL;
  IVsUIHierarchy *          pHierarchy  = NULL;
  IVsWindowFrame *          pFrame      = NULL;
  IUnknown *                pUnk        = NULL;
  IVsHighlight *            pHighlight  = NULL;

  IfFailGo(CGlobalServiceProvider::HrQueryService(SID_SVsUIShellOpenDocument, IID_IVsUIShellOpenDocument, (void **)&pOpenDoc));
  IfFailGo(pOpenDoc->OpenDocumentViaProject(szFile, LOGVIEWID_TextView, NULL, &pHierarchy, &itemid, &pFrame));
  pFrame->Show();
  VariantInit(&var);
  IfFailGo(pFrame->GetProperty(VSFPROPID_DocView, &var));
  if (VT_UNKNOWN != var.vt) { hr = E_FAIL; goto Error; }
  pUnk = V_UNKNOWN(&var);
  if (NULL != pUnk)
  {
    IfFailGo(pUnk->QueryInterface(IID_IVsCodeWindow, (void **)&pCodeWin));
    if (SUCCEEDED(hr = pCodeWin->GetLastActiveView(&pTextView)) ||
        SUCCEEDED(hr = pCodeWin->GetPrimaryView(&pTextView)) )
    {
      pTextView->SetSelection(iLine, iStart, iLine, iStart + iLen);
      // uncover selection
      IfFailGo(pTextView->QueryInterface(IID_IVsHighlight, (void**)&pHighlight));
      IfFailGo(SUCCEEDED(pHighlight->GetHighlightRect(&rc)));
      UncoverSelectionRect(&rc);
    }
  }

Error:
  CLEARINTERFACE(pHighlight);
  CLEARINTERFACE(pTextView);
  CLEARINTERFACE(pCodeWin);
  CLEARINTERFACE(pUnk);
  CLEARINTERFACE(pFrame);
  CLEARINTERFACE(pOpenDoc);
  CLEARINTERFACE(pHierarchy);
  RedrawWindow(m_hwndResults, NULL, NULL, RDW_ERASE|RDW_FRAME|RDW_INVALIDATE|RDW_ALLCHILDREN);
  return hr;
}
```

## <a name="see-also"></a>추가 정보
- [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)
- [방법: 문서 데이터에 보기 연결](../extensibility/how-to-attach-views-to-document-data.md)
- [사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)

---
title: 단일 및 다중 탭 보기 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699984"
---
# <a name="single-and-multi-tab-views"></a>단일 및 다중 탭 보기
편집자는 다양한 유형의 뷰를 만들 수 있습니다. 한 가지 예는 코드 편집기 창, 다른 하나는 양식 디자이너입니다.

 다중 탭보기는 여러 탭이 있는 보기입니다. 예를 들어 HTML 편집기 하단에는 **디자인과** **소스,** 각각 논리적 보기의 두 개의 탭이 있습니다. 디자인 보기에는 렌더링된 웹 페이지가 표시되고 다른 웹 페이지는 웹 페이지를 구성하는 HTML이 표시됩니다.

## <a name="accessing-physical-views"></a>실제 보기 액세스
 물리적 뷰호스트 문서 뷰 개체는 각각 코드 또는 양식과 같은 버퍼의 데이터 보기를 나타냅니다. 따라서 각 문서 뷰 개체에는 물리적 보기(물리적 뷰 문자열로 식별됨)가 있으며 일반적으로 단일 논리 보기가 있습니다.

 그러나 경우에 따라 물리적 보기에는 둘 이상의 논리적 보기가 있을 수 있습니다. 몇 가지 예로는 나란히 보기가 있는 분할 창이 있는 편집기 또는 GUI/디자인 보기와 코드 뒤형식 보기가 있는 양식 디자이너가 있습니다.

 편집기가 사용 가능한 모든 실제 뷰에 액세스할 수 있도록 하려면 편집기 팩터리에서 만들 수 있는 각 문서 뷰 개체 유형에 대해 고유한 물리적 보기 문자열을 만들어야 합니다. 예를 들어 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 편집기 팩터리는 코드 창 및 양식 디자이너 창에 대한 문서 뷰 개체를 만들 수 있습니다.

## <a name="creating-multi-tabbed-views"></a>다중 탭뷰 작성
 문서 뷰 개체는 고유한 물리적 뷰 문자열을 통해 실제 보기와 연결되어야 하지만 실제 보기 내에 여러 탭을 배치하여 다양한 방식으로 데이터를 볼 수 있습니다. 이 다중 탭 구성에서는 모든 탭이 동일한 물리적 보기 문자열과 연결되지만 각 탭에는 다른 논리 보기 GUID가 제공됩니다.

 편집기의 다중 탭 뷰를 만들려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiViewDocumentView> 인터페이스를 구현한 다음 만드는<xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID>각 탭에 다른 논리 보기 GUID()를 연결합니다.

 Visual Studio HTML 편집기는 다중 탭 보기가 있는 편집기의 예입니다. **디자인** 및 **소스** 탭이 있습니다. 이를 사용하려면 **디자인** 탭 및 **소스** `LOGICALVIEWID_TextView` 탭에 대해 각 `LOGICALVIEWID_Code` 탭과 다른 논리 보기가 연결됩니다.

 VSPackage는 적절한 논리 보기를 지정하여 폼 디자인, 코드 편집 또는 코드 디버깅과 같은 특정 목적에 해당하는 뷰에 액세스할 수 있습니다. 그러나 창 중 하나를 NULL 문자열로 식별해야 하며 기본 논리 보기()와`LOGVIEWID_Primary`일치해야 합니다.

 다음 표에는 사용 가능한 논리 뷰 값과 해당 사용값이 나열되어 있습니다.

|로그뷰ID GUID|권장 사용|
|--------------------|---------------------|
|`LOGVIEWID_Primary`|편집기 팩터의 기본/기본 보기입니다.<br /><br /> 모든 편집기 팩터리에서 이 값을 지원해야 합니다. 이 뷰는 NULL 문자열을 실제 뷰 문자열로 사용해야 합니다. 하나 이상의 논리 뷰를 이 값으로 설정해야 합니다.|
|`LOGVIEWID_Debugging`|뷰를 디버깅합니다. 일반적으로 `LOGVIEWID_Debugging` `LOGVIEWID_Code`와 동일한 뷰에 매핑됩니다.|
|`LOGVIEWID_Code`|코드 보기 명령에서 시작된 **보기입니다.**|
|`LOGVIEWID_Designer`|양식 보기 명령으로 시작된 **보기입니다.**|
|`LOGVIEWID_TextView`|텍스트 편집기 보기입니다. 이 보기는 에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>액세스할 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>수 있는 을 반환합니다.|
|`LOGVIEWID_UserChooseView`|사용할 보기를 선택하라는 메시지가 표시됩니다.|
|`LOGVIEWID_ProjectSpecificEditor`|**대화** 상자 열기를 통해 전달된 대화 상자<br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.OpenItem%2A><br /><br /> 사용자가 "(프로젝트 기본 편집기)" 항목을 선택할 때|

 논리 보기 GUID는 확장 가능하지만 VSPackage에 정의된 논리 보기 GUID만 사용할 수 있습니다.

 종료 시 Visual Studio는 편집기 팩터리의 GUID와 문서 창과 연결된 물리적 보기 문자열을 유지하므로 솔루션을 다시 열 때 문서 창을 다시 여는 데 사용할 수 있습니다. 솔루션이 닫힐 때 열려 있는 창만 솔루션(.suo) 파일에 유지됩니다. 이러한 값은 `VSFPROPID_guidEditorType` 메서드의 `VSFPROPID_pszPhysicalView` `propid` 매개 변수에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 전달된 값및 값에 해당합니다.

## <a name="example"></a>예제
 이 코드 조각은 개체가 <xref:Microsoft.VisualStudio.Shell.Interop.LogicalViewID.TextView> 구현되는 뷰에 액세스하는 `IVsCodeWindow`데 사용되는 방법을 보여 줍니다. 이 경우 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShellOpenDocument> 서비스는 창 프레임에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 대한 `LOGVIEWID_TextView`포인터를 가져오는 호출 및 요청에 사용됩니다. 문서 뷰 개체에 대한 포인터는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> `VSFPROPID_DocView`의 값을 호출하고 지정하여 가져옵니다. 문서 뷰 개체에서 `QueryInterface` 에 `IVsCodeWindow`대해 호출됩니다. 이 경우 예상되는 것은 텍스트 편집기가 반환되므로 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 메서드에서 반환되는 문서 뷰 개체는 코드 창입니다.

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

## <a name="see-also"></a>참조
- [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)
- [방법: 문서 데이터에 보기 연결](../extensibility/how-to-attach-views-to-document-data.md)
- [사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)

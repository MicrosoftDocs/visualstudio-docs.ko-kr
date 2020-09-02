---
title: '방법: 파일 변경 알림 표시 하지 않음 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204073"
---
# <a name="how-to-suppress-file-change-notifications"></a>방법: 파일 변경 알림 표시 안 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 버퍼를 나타내는 물리적 파일이 변경 되 면 **다음 항목에 대 한 변경 내용을 저장 하 시겠습니까?** 메시지가 포함 된 대화 상자가 표시 됩니다. 이를 파일 변경 알림 이라고 합니다. 파일에 많은 변경 내용이 있을 경우이 대화 상자를 다시 표시 하면 보다 신속 하 게 표시 될 수 있습니다.  
  
 다음 절차를 사용 하 여 프로그래밍 방식으로이 대화 상자를 표시 하지 않을 수 있습니다. 이렇게 하면 사용자에 게 매번 변경 내용을 저장 하 라는 메시지를 표시 하지 않고 즉시 파일을 다시 로드할 수 있습니다.  
  
### <a name="to-suppress-file-change-notification"></a>파일 변경 알림을 표시 하지 않으려면  
  
1. 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> 하 여 열려 있는 파일과 연결 된 텍스트 버퍼 개체를 확인 합니다.  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (문서 데이터) 개체에서 인터페이스를 가져온 다음로 설정 된 매개 변수를 사용 하 여 메서드를 구현 하 여 메모리에 있는 개체를 전달 하 여 파일 변경 내용 모니터링을 무시 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> `fIgnore` `true` 합니다.  
  
3. 및 인터페이스에서 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 하 여 메모리 내 개체를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 파일 변경 내용으로 업데이트 합니다 (예: 필드가 구성 요소에 추가 되는 경우).  
  
4. 사용자가 진행 중일 수 있는 보류 중인 편집 내용을 고려 하지 않고 디스크의 파일을 변경 하 여 업데이트 합니다.  
  
     이러한 방식으로 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 파일 변경 알림에 대 한 모니터링을 다시 시작 하도록 개체를 지시할 때 메모리의 텍스트 버퍼에는 생성 된 변경 내용과 보류 중인 기타 모든 편집 내용이 반영 됩니다. 디스크의 파일은 사용자가 생성 한 최신 코드와 사용자가 편집한 코드에서 이전에 저장 한 변경 내용을 반영 합니다.  
  
5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 매개 변수를로 설정 하 여 파일 변경 알림에 대 한 모니터링을 다시 시작 하도록 개체에 알리려면 메서드를 호출 합니다 `fIgnore` `false` .  
  
6. SCC (소스 코드 제어)의 경우와 같이 파일을 여러 번 변경 하려는 경우에는 전역 파일 변경 서비스에 파일 변경 알림을 임시로 일시 중단 하도록 지시 해야 합니다.  
  
     예를 들어 파일을 다시 작성 한 다음 타임 스탬프를 변경 하는 경우 다시 작성 및 timestample 한 작업은 각각 별도의 파일 변경 이벤트로 계산 되므로 파일 변경 알림을 일시 중단 해야 합니다. 전역 파일 변경 알림을 사용 하도록 설정 하려면 메서드를 대신 호출 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> .  
  
## <a name="example"></a>예  
 다음은 파일 변경 알림을 표시 하지 않도록 설정 하는 방법을 보여 줍니다.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 SCC의 경우 처럼 파일의 여러 변경 내용을 포함 하는 경우에는 파일 변경 내용에 대 한 모니터링을 다시 시작 하기 위해 문서 데이터에 경고 하기 전에 전역 파일 변경 알림을 다시 시작 하는 것이 중요 합니다.

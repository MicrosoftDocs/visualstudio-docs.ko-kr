---
title: 지연 된 문서 로드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196866"
---
# <a name="delayed-document-loading"></a>지연된 문서 로드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자가 Visual Studio 솔루션을 다시 열면 연결 된 문서 대부분이 즉시 로드 되지 않습니다. 문서 창 프레임은 보류 중인 초기화 상태에서 만들어지고, 자리 표시자 문서 (스텁 프레임)는 RDT (실행 문서 테이블)에 배치 됩니다.  
  
 문서를 로드 하기 전에 문서에서 요소를 쿼리하여 프로젝트 문서를 불필요 하 게 로드할 수 있습니다. 그러면 Visual Studio의 전체 메모리 공간이 늘어날 수 있습니다.  
  
## <a name="document-loading"></a>문서 로드  
 예를 들어 창 프레임의 탭을 선택 하 여 사용자가 문서에 액세스할 때 스텁 프레임 및 문서가 완전히 초기화 됩니다. 문서 데이터를 얻기 위해 RDT에 직접 액세스 하거나 다음 호출 중 하나를 수행 하 여 RT에 간접적으로 액세스 하 여 문서 데이터를 요청 하는 확장을 통해 문서를 초기화할 수도 있습니다.  
  
- 창 프레임 표시 메서드: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- 다음 속성에 대 한 창 프레임 GetProperty 메서드는 다음과 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 같습니다.  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  확장 프로그램에서 관리 코드를 사용 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 문서가 보류 중인 초기화 상태에 있지 않거나 문서를 완전히 초기화 하려는 경우를 제외 하 고는를 호출 하면 안 됩니다. 이 메서드는 항상 doc 데이터 개체를 반환 하 여 필요한 경우 만듭니다. 대신 IVsRunningDocumentTable4 인터페이스의 메서드 중 하나를 호출 해야 합니다.  
  
  확장에서 c + +를 사용 하는 경우 `null` 원하지 않는 매개 변수에 대해을 전달할 수 있습니다.  
  
  관련 속성을 요청 하기 전에 다른 속성을 요청 하기 전에 다음 메서드 중 하나를 호출 하 여 불필요 한 문서 로드를 방지할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A><xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>를 사용 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 문서를 아직 초기화 하지 않은 경우이 메서드는에 대 한 값을 포함 하는 개체를 반환 합니다.  
  
  문서가 완전히 초기화 될 때 발생 하는 RDT 이벤트를 구독 하 여 문서가 로드 된 시기를 확인할 수 있습니다. 다음과 같은 두 가지 가능성이 있습니다.  
  
- 이벤트 싱크가를 구현 하는 경우 다음을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> 구독할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>  
  
- 그렇지 않으면를 구독할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  다음은 가상 문서 액세스 시나리오입니다. Visual Studio 확장에서 열린 문서에 대 한 일부 정보 (예를 들어 편집 잠금 수 및 문서 데이터에 대 한 정보)를 표시 하려고 합니다. 를 사용 하 여 RDT의 문서를 열거 <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> 한 다음 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> 편집 잠금 수와 문서 데이터를 검색 하기 위해 각 문서에 대해를 호출 합니다. 문서가 보류 중인 초기화 상태에 있는 경우 문서 데이터를 요청 하면 해당 문서가 불필요 하 게 초기화 됩니다.  
  
  을 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> 편집 잠금 횟수를 가져온 다음를 사용 하 여 문서가 초기화 되었는지 여부를 확인 하는 것이 더 효율적입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> . 플래그가 포함 되어 있지 않은 경우 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 문서가 이미 초기화 되었으며를 사용 하 여 문서 데이터를 요청 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> 해도 불필요 한 초기화가 발생 하지 않습니다. 플래그가를 포함 하는 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> 문서가 초기화 될 때까지 확장명이 문서 데이터를 요청 하지 않아야 합니다. 이는 OnAfterAttributeChange (Ex) 이벤트 처리기에서 검색할 수 있습니다.  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>확장을 테스트 하 여 초기화가 강제로 수행 되는지 확인  
 문서가 초기화 되었는지 여부를 나타내는 표시 된 큐가 없으므로 확장이 강제로 초기화 되는지 확인 하기 어려울 수 있습니다. 완전 하 게 초기화 되지 않은 모든 문서의 제목이 제목에 텍스트를 포함 하도록 하는 레지스트리 키를 설정 하 여 더 쉽게 확인할 수 있습니다 `[Stub]` .  
  
 **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]** 에서 **StubTabTitleFormatString** 을 ** {0} [스텁]** 으로 설정 합니다.

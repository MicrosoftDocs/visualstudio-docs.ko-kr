---
title: '방법: 편집기에 대 한 컨텍스트 제공 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841679"
---
# <a name="how-to-provide-context-for-editors"></a>방법: 편집기에 대한 컨텍스트 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기의 경우 포커스가 도구 창으로 이동 하기 바로 전에 편집기에 포커스가 있거나 포커스가 있는 경우에만 컨텍스트가 활성화 됩니다. 다음을 수행 하 여 편집기에 대 한 컨텍스트를 제공할 수 있습니다.  
  
1. 컨텍스트 모음을 만듭니다.  
  
2. 선택 요소 식별자 (SEID)에 컨텍스트 모음을 게시 합니다.  
  
3. 모음에서 컨텍스트를 유지 관리 합니다.  
  
   이러한 작업에 대해서는 다음 절차를 수행 합니다. 컨텍스트를 제공 하는 방법에 대 한 자세한 내용은이 항목의 뒷부분에 있는 **강력한 프로그래밍** 을 참조 하십시오.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>편집기 또는 디자이너에 대 한 컨텍스트 모음을 만들려면  
  
1. `QueryService` <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 서비스의 인터페이스에서를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> 합니다.  
  
     인터페이스에 대 한 포인터가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> 반환 됩니다.  
  
2. 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> 하 여 새 컨텍스트 또는 subcontext 모음을 만듭니다.  
  
     인터페이스에 대 한 포인터가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> 반환 됩니다.  
  
3. 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> 하 여 특성, 조회 키워드 또는 F1 키워드를 컨텍스트 또는 subcontext 모음에 추가 합니다.  
  
4. Subcontext 모음을 만드는 경우 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> subcontext 자루를 부모 컨텍스트 모음에 연결 합니다.  
  
5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>을 호출 하 여 **동적 도움말** 창이 업데이트 될 때 알림을 받습니다.  
  
     **동적 도움말** 창을 업데이트할 준비가 되 면 편집기를 호출 하면 업데이트가 발생할 때까지 컨텍스트 변경을 연기할 수 있습니다. 이렇게 하면 시스템 유휴 시간을 사용할 수 있을 때까지 실행 시간이 오래 걸리는 알고리즘을 지연 시킬 수 있으므로 성능이 향상 될 수 있습니다.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>SEID에 컨텍스트 모음을 게시 하려면  
  
1. `QueryService`서비스에서를 호출 하 여 인터페이스에 대 한 포인터를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> 반환 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 합니다.  
  
2. 을 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> `elementid` 전역 수준에 컨텍스트를 전달 하 고 있음을 나타내기 위해 SEID_UserContext의 요소 식별자 (매개 변수) 값을 지정 합니다.  
  
3. 편집기 또는 디자이너가 활성화 되 면 개체의 값 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> 이 전역 선택 항목으로 전파 됩니다. 이 프로세스는 세션당 한 번만 완료 한 다음를 호출할 때 만들어진 전역 컨텍스트에 포인터를 저장 하기만 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> 됩니다.  
  
### <a name="to-maintain-the-context-bag"></a>컨텍스트 모음을 유지 관리 하려면  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>를 구현 하 여 **동적 도움말** 창이 업데이트 되기 전에 편집기나 디자이너를 호출 하는지 확인 합니다.  
  
     컨텍스트 모음을 만들고 구현한 후에 호출 된 각 컨텍스트 모음에 대해를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> 호출 하 여 컨텍스트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 모음이 업데이트 될 것 이라는 것을 컨텍스트 공급자에 게 알립니다. 이 호출을 사용 하 여 **동적 도움말** 창 업데이트를 수행 하기 전에 컨텍스트 모음 및 모든 subcontext 백에서 특성 및 키워드를 변경할 수 있습니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>편집기 또는 디자이너에 새 컨텍스트가 있음을 나타내려면 컨텍스트 모음에서를 호출 합니다.  
  
     **동적 도움말** 창에서를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> 하 여 업데이트 중임을 나타내는 경우 편집기 또는 디자이너는 해당 시점에 부모 컨텍스트 모음 및 subcontext 백 모두에 대해 컨텍스트를 적절 하 게 업데이트할 수 있습니다.  
  
    > [!NOTE]
    > 컨텍스트 `SetDirty` `true` 모음에서 컨텍스트를 추가 하거나 제거할 때마다 플래그가 자동으로로 설정 됩니다. **동적 도움말** 창은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> `SetDirty` 플래그가로 설정 된 경우에만 컨텍스트 모음에서를 호출 합니다 `true` . 업데이트 후로 다시 설정 됩니다 `false` .  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>를 호출 하 여 컨텍스트를 활성 컨텍스트 컬렉션에 추가 하거나 컨텍스트를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> 제거 합니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 편집기를 직접 작성 하는 경우이 항목의 세 가지 절차를 모두 완료 하 여 편집기에 대 한 컨텍스트를 제공 해야 합니다.  
  
> [!NOTE]
> 편집기 또는 디자이너 창을 적절히 활성화 하 고 명령 라우팅이 제대로 업데이트 되도록 하려면 구성 요소에서를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 포커스 창으로 설정 해야 합니다.  
  
 SEID는 선택 항목에 따라 변경 되는 속성의 컬렉션입니다. SEID 정보는 전역 선택 항목을 통해 사용할 수 있습니다. 전역 선택은 인터페이스에 의해 트리거되는 이벤트에 연결 되며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> , 선택 된 모든 항목 (현재 편집기, 현재 도구 창, 현재 계층 등)의 목록을 포함 합니다.  
  
 커서가 단어 내에서 이동할 때마다 컨텍스트가 변경 될 수 있는 편집기 및 디자이너의 경우 컨텍스트 모음을 지속적으로 업데이트 하는 것은 비효율적입니다. 편집기 또는 디자이너 창에서 이동 하는 커서를 검색할 때마다 업데이트를 보다 효율적으로 수행 하려면를 호출 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> 됩니다. 이렇게 하면 유휴 시간이 있을 때까지 컨텍스트 변경을 보류 하 고 IDE의 컨텍스트 서비스에서 **동적 도움말** 창이 업데이트 되는 편집기나 디자이너에 게 알림을 보낼 수 있습니다. 이 방법은이 항목의 "컨텍스트 모음을 유지 관리 하려면" 절차에서 사용 됩니다.  
  
 편집기나 디자이너 내에서 활동에 대 한 컨텍스트를 제공한 후에는 사용자가 편집기나 디자이너 자체에 대 한 도움말을 볼 수 있도록 특정 F1 키워드를 제공 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>

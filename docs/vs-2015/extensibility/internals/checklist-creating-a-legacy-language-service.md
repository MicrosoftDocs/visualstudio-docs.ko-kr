---
title: '검사 목록: 레거시 언어 서비스 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b79afe64aafac473d4fe5d22464998d0c2f0537
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842138"
---
# <a name="checklist-creating-a-legacy-language-service"></a>검사 목록: 레거시 언어 서비스 만들기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음 검사 목록에서는 핵심 편집기에 대 한 언어 서비스를 만들기 위해 수행 해야 하는 기본 단계를 요약 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 언어 서비스를에 통합 하려면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 디버그 식 계산기를 만들어야 합니다. 자세한 내용은 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)에서 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) 을 참조 하세요.  
  
## <a name="steps-for-creating-a-language-service"></a>언어 서비스를 만드는 단계  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 인터페이스를 구현합니다.  
  
    - VSPackage에서 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 언어 서비스를 제공 하는 인터페이스를 구현 합니다.  
  
    - 구현에서 언어 서비스를 IDE (통합 개발 환경)에서 사용할 수 있도록 설정 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 합니다.  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>주 언어 서비스 클래스에서 인터페이스를 구현 합니다.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>인터페이스는 핵심 편집기와 언어 서비스 간의 상호 작용을 시작 하는 지점입니다.  
  
### <a name="optional-features"></a>선택적 기능  
 다음 기능은 선택 사항이 며 순서에 관계 없이 구현할 수 있습니다. 이러한 기능은 언어 서비스의 기능을 향상 시킵니다.  
  
- 구문 색 지정  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 인터페이스를 구현합니다. 이 인터페이스의 구현은 적절 한 색 정보를 반환 하기 위해 파서 정보를 지정 해야 합니다.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>메서드는 인터페이스를 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> . 별도의 svc 인스턴스가 각 텍스트 버퍼에 대해 만들어지므로 인터페이스를 개별적으로 구현 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> . 자세한 내용은 [레거시 언어 서비스의 구문 색](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)지정을 참조 하세요.  
  
- 코드 창  
  
   인터페이스를 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 하 여 새 코드 창이 만들어질 때 언어 서비스에서 알림을 받을 수 있도록 합니다.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>메서드는 인터페이스를 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> . 그런 다음 언어 서비스는의 코드 창에 특수 UI를 추가할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> . 언어 서비스는에서 텍스트 뷰 필터를 추가 하는 등의 특수 처리 작업을 수행할 수도 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A> .  
  
- 텍스트 뷰 필터  
  
   언어 서비스에서 IntelliSense 문 완성 기능을 제공 하려면 텍스트 뷰에서 달리 처리할 몇 가지 명령을 가로채 야 합니다. 이러한 명령을 차단 하려면 다음 단계를 완료 합니다.  
  
  - <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>을 구현 하 여 명령 체인에 참여 하 고 편집기 명령을 처리 합니다.  
  
  - 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 하 고 구현에 전달 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 합니다.  
  
  - <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>뷰에서 분리 하는 경우 메서드를 호출 하 여 이러한 명령이 더 이상 사용자에 게 전달 되지 않도록 합니다.  
  
    처리 해야 하는 명령은 제공 되는 서비스에 따라 달라 집니다. 자세한 내용은 [언어 서비스 필터에 대 한 중요 한 명령](../../extensibility/internals/important-commands-for-language-service-filters.md)을 참조 하세요.  
  
  > [!NOTE]
  > 인터페이스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 인터페이스와 동일한 개체에서 구현 되어야 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
- 문 완성  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 인터페이스를 구현합니다.  
  
   문 완성 명령 (즉,)을 지원 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 하 고 인터페이스 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 에서 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 하 여 인터페이스를 전달 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 합니다. 자세한 내용은 [레거시 언어 서비스의 문 완성](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)을 참조 하세요.  
  
- 메서드 팁  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>메서드 팁 창에 대 한 데이터를 제공 하는 인터페이스를 구현 합니다.  
  
   메서드 데이터 팁 창을 표시할 시기를 알 수 있도록 텍스트 뷰 필터를 설치 하 여 명령을 적절 하 게 처리 합니다. 자세한 내용은 [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)를 참조 하세요.  
  
- 오류 표식  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스를 구현합니다.  
  
   인터페이스를 구현 하는 오류 표식 개체를 만들고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 오류 표식 개체의 인터페이스를 전달 합니다.  
  
   일반적으로 각 오류 마커는 작업 목록 창의 항목을 관리 합니다.  
  
- 작업 목록 항목  
  
   인터페이스를 제공 하는 작업 항목 클래스를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> 합니다.  
  
   인터페이스와 인터페이스를 제공 하는 작업 공급자 클래스를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> 합니다.  
  
   인터페이스를 제공 하는 작업 열거자 클래스를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> 합니다.  
  
   작업 목록의 메서드를 사용 하 여 작업 공급자를 등록 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> 합니다.  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>서비스 GUID를 사용 하 여 언어 서비스의 서비스 공급자를 호출 하 여 인터페이스를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .  
  
   새 작업이 있거나 업데이트 된 작업이 있는 경우 작업 항목 개체를 만들고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> 인터페이스에서 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> 합니다.  
  
- 주석 작업 항목  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>인터페이스 및 인터페이스를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> 하 여 주석 작업 토큰을 가져옵니다.  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>서비스에서 인터페이스를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> .  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>메서드에서 인터페이스를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> .  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>토큰 목록에서 변경 내용을 수신 하는 인터페이스를 구현 합니다.  
  
- 개요  
  
   개요를 지원 하기 위한 몇 가지 옵션이 있습니다. 예를 들어 **정의로 축소** 명령을 지원 하거나 편집기에서 제어 하는 개요 영역을 제공 하거나 클라이언트에서 제어 하는 영역을 지원할 수 있습니다. 자세한 내용은 [방법: 레거시 언어 서비스에서 확장 된 개요 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)을 참조 하세요.  
  
- 언어 서비스 등록  
  
   언어 서비스를 등록 하는 방법에 대 한 자세한 내용은 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md) 및 [vspackage 관리](../../extensibility/managing-vspackages.md)를 참조 하세요.  
  
- 상황에 맞는 도움말  
  
   다음 방법 중 하나로 편집기에 컨텍스트를 제공 합니다.  
  
  - 인터페이스를 구현 하 여 텍스트 표식의 컨텍스트를 제공 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 합니다.  
  
  인터페이스를 구현 하 여 모든 사용자 컨텍스트를 제공 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

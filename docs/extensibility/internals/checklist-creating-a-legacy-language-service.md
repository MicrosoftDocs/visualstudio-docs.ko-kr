---
title: '체크리스트: 레거시 언어 서비스 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709784"
---
# <a name="checklist-create-a-legacy-language-service"></a>체크리스트: 레거시 언어 서비스 만들기
다음 검사 목록은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 핵심 편집기의 언어 서비스를 만들기 위해 수행해야 하는 기본 단계를 요약합니다. 언어 서비스를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 통합하려면 디버그 식 계산기를 만들어야 합니다. 자세한 내용은 [Visual Studio 디버거 확장성에서](../../extensibility/debugger/visual-studio-debugger-extensibility.md) [CLR 식 계산기 쓰기를](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) 참조하십시오.

## <a name="steps-to-create-a-language-service"></a>언어 서비스를 만드는 단계

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 인터페이스를 구현합니다.

    - VSPackage에서 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 언어 서비스를 제공하는 인터페이스를 구현합니다.

    - 구현시 IDE(통합 개발 환경)에서 언어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> 서비스를 사용할 수 있도록 합니다.

2. 기본 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 언어 서비스 클래스에서 인터페이스를 구현합니다.

     인터페이스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 핵심 편집기와 언어 서비스 간의 상호 작용의 시작점입니다.

### <a name="optional-features"></a>선택적 기능
 다음 기능은 선택 사항이며 임의의 순서로 구현할 수 있습니다. 이러한 기능은 언어 서비스의 기능을 향상시커줍니다.

- 구문 색 지정

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 인터페이스를 구현합니다. 이 인터페이스를 구현하면 파서 정보가 적절한 색상 정보를 반환해야 합니다.

  메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 인터페이스를 반환합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 각 텍스트 버퍼에 대해 별도의 색칠 모드 인스턴스가 만들어지므로 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 별도로 구현해야 합니다. 자세한 내용은 [레거시 언어 서비스의 구문 색칠을](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)참조하십시오.

- 코드 창

  언어 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 서비스가 새 코드 창이 생성될 때 알림을 받을 수 있도록 인터페이스를 구현합니다.

  메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 인터페이스를 반환합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 그런 다음 언어 서비스에서 코드 창에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>특수 UI를 추가할 수 있습니다. 언어 서비스는 에서 텍스트 보기 필터를 추가하는 것과 같은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>모든 특수 처리를 수행할 수도 있습니다.

- 텍스트 보기 필터

  언어 서비스에서 IntelliSense 문 완료를 제공하려면 텍스트 뷰가 달리 처리할 일부 명령을 가로채야 합니다. 이러한 명령을 가로채려면 다음 단계를 완료합니다.

  - 명령 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 체인에 참여하고 편집기 명령을 처리하도록 구현합니다.

  - 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 호출하고 구현을 전달합니다. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>

  - 이러한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> 명령이 더 이상 전달되지 않도록 뷰에서 분리할 때 메서드를 호출합니다.

  처리해야 하는 명령은 제공되는 서비스에 따라 다릅니다. 자세한 내용은 [언어 서비스 필터에 대한 중요 명령을](../../extensibility/internals/important-commands-for-language-service-filters.md)참조하십시오.

  > [!NOTE]
  > 인터페이스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스와 동일한 개체에서 구현되어야 합니다.

- 문 완성

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 인터페이스를 구현합니다.

  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>문 완성 명령(즉, 즉)을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 지원하고 인터페이스를 전달하는 인터페이스의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 메서드를 호출합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 자세한 내용은 [레거시 언어 서비스의 명령문 완성을](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)참조하십시오.

- 방법 팁

  메서드 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 팁 창에 대한 데이터를 제공하는 인터페이스를 구현합니다.

  메서드 데이터 팁 창을 표시할 시기를 알 수 있도록 명령을 적절하게 처리하도록 텍스트 보기 필터를 설치합니다. 자세한 내용은 [레거시 언어 서비스의 매개 변수 정보를](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)참조하십시오.

- 오류 마커

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 인터페이스를 구현합니다.

  인터페이스를 구현하는 오류 마커 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 개체를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 만들고 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 호출하여 오류 마커 개체의 인터페이스를 전달합니다.

  일반적으로 각 오류 마커는 작업 목록 창에서 항목을 관리합니다.

- 작업 목록 항목

  인터페이스를 제공하는 작업 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> 항목 클래스를 구현합니다.

  인터페이스와 인터페이스를 제공하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> 작업 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> 공급자 클래스를 구현합니다.

  인터페이스를 제공하는 작업 열거자 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> 클래스를 구현합니다.

  작업 목록의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> 메서드를 사용하여 작업 공급자를 등록합니다.

  언어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> 서비스의 서비스 공급자를 서비스 GUID를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>사용하여 인터페이스를 가져옵니다.

  작업 항목 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> 만들고 새 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> 작업 또는 업데이트된 작업이 있을 때 인터페이스에서 메서드를 호출합니다.

- 주석 작업 항목

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> 인터페이스와 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> 사용하여 주석 작업 토큰을 가져옵니다.

  서비스에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> 가져옵니다.

  메서드에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> 가져옵니다.

  토큰 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> 목록의 변경 내용을 수신하는 인터페이스를 구현합니다.

- 개요

  개요를 지원하기 위한 몇 가지 옵션이 있습니다. 예를 들어 정의로 축소 명령을 **지원하거나,** 편집기 제어 개요 영역을 제공하거나, 클라이언트 제어 영역을 지원할 수 있습니다. 자세한 내용은 [레거시 언어 서비스에서 확장된 개요 지원을 제공하는 방법을](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)참조하십시오.

- 언어 서비스 등록

  언어 서비스를 등록하는 방법에 대한 자세한 내용은 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md) 및 [VSPackage 관리 를](../../extensibility/managing-vspackages.md)참조하십시오.

- 상황에 맞는 도움말

  다음 방법 중 하나로 편집기에게 컨텍스트를 제공합니다.

  - 인터페이스를 구현하여 텍스트 마커에 대한 컨텍스트를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> 제공합니다.

  - 인터페이스를 구현하여 모든 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> 사용자 컨텍스트를 제공합니다.

## <a name="see-also"></a>참조
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
- [CLR 식 계산기 작성](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

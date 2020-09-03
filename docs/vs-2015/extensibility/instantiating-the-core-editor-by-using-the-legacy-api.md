---
title: 레거시 API를 사용 하 여 핵심 편집기 인스턴스화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29306a16390039c8ee6e424b81a5ff617e533ab4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203918"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>레거시 API를 사용하여 핵심 편집기 인스턴스화
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기는 삽입, 삭제, 복사 및 붙여넣기와 같은 텍스트 편집 기능을 담당 합니다. 텍스트 색 지정, 들여쓰기 및 IntelliSense 문 완성과 같은 언어 서비스에서 제공 하는 함수와 이러한 기능을 결합 합니다.  
  
 다음 세 가지 방법 중 하나로 핵심 편집기의 인스턴스를 인스턴스화할 수 있습니다.  
  
- 창에서 핵심 편집기의 인스턴스를 명시적으로 만듭니다.  
  
- 핵심 편집기의 인스턴스를 반환 하는 편집기 팩터리를 제공 합니다.  
  
- 프로젝트 계층 구조에서 파일을 엽니다.  
  
  다음 섹션에서는 레거시 API를 사용 하 여 편집기를 인스턴스화하는 방법을 설명 합니다.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>명시적으로 핵심 편집기 인스턴스 열기  
 핵심 편집기의 인스턴스를 명시적으로 가져올 때:  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>편집 중인 문서 데이터 개체를 보관할를 가져옵니다.  
  
- 인터페이스에서 인터페이스를 만들어 문서 데이터 개체의 선 중심 표현을 만듭니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 메서드를 사용 하 여 인터페이스의 기본 구현 인스턴스에 대 한 문서 데이터 개체로 설정 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> 합니다.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 메서드를 사용 하 여 인터페이스에서 인스턴스를 호스팅합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> .  
  
  이 시점에서 인터페이스를 표시 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 핵심 편집기의 인스턴스가 포함 된 창이 제공 됩니다.  
  
  그러나이는 바로 가기 키가 없거나 고급 기능에 대 한 액세스 이기 때문에 매우 유용한 인스턴스가 아닙니다. 바로 가기 키 및 고급 기능에 대 한 액세스 권한을 얻으려면:  
  
- 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 편집기에서 사용 하는 언어 서비스와 문서 데이터 개체를 연결 합니다.  
  
- 사용자 고유의 바로 가기 키를 만들거나 개체 표시 속성을 설정 하 여 시스템 기본값을 사용 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> . 이렇게 하려면 속성을 사용 하 여 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
   비표준 바로 가기 키를 가져오고 사용 하려면. vsct 파일을 사용 하 여 생성 합니다. 자세한 내용은 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)을 참조하세요.  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>편집기 팩터리를 사용 하 여 핵심 편집기를 가져오는 방법  
 메서드를 사용 하 여 편집기 팩터리를 사용 하 여 핵심 편집기를 구현 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 개체에서 문서 데이터 개체를 사용 하 여 명시적으로를 호스트 하려면 이전 섹션에 설명 된 모든 단계를 수행 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> 합니다.  
  
 텍스트를 표시 하려면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 개체에서 인터페이스를 가져온 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 다음 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 합니다.  
  
 언어 서비스를 편집기에 제공 하려면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 메서드 내에서 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 합니다.  
  
 이전 섹션과 달리 기본 바로 가기 키를 가져오려면 메서드에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 핵심 편집기를 가져올 때 메서드에서 반환 하는 명령 컨텍스트를 사용 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>메서드가 텍스트 편집기와 동일한 명령 GUID를 반환 하는 경우 핵심 편집기의 인스턴스는 자동으로 기본 바로 가기 키를 가져옵니다.  
  
 일반 정보는 [연습: 핵심 편집기 만들기 및 편집기 파일 형식 등록](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [핵심 편집기 내부](../extensibility/inside-the-core-editor.md)   
 [프로젝트 항목 열기 및 저장](../extensibility/internals/opening-and-saving-project-items.md)   
 [연습: 코어 편집기 만들기 및 편집기 파일 형식 등록](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)

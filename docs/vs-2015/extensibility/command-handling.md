---
title: 명령 처리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184369"
---
# <a name="command-handling"></a>명령 처리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기에서 새 명령을 정의할 수 있습니다. 명령은 일반적으로 메뉴, 도구 모음 또는 상황에 맞는 메뉴에 표시 됩니다.  
  
 명령 및 메뉴 정의에 대 한 자세한 내용은 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)을 참조 하세요.  
  
 언어 서비스는 열거형을 가로채서 편집기에 표시 되는 상황에 맞는 메뉴를 제어할 수 있습니다 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> . 또는 마커 별로 상황에 맞는 메뉴를 제어할 수 있습니다. 자세한 내용은 [언어 서비스 필터에 대 한 중요 한 명령](../extensibility/internals/important-commands-for-language-service-filters.md)을 참조 하세요.  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>편집기 상황에 맞는 메뉴에 명령 추가  
 상황에 맞는 메뉴에 명령을 추가 하려면 먼저 특정 그룹에 속한 메뉴 명령 집합을 정의 해야 합니다. 다음 예제는 연습 [연습: 사용자 지정 편집기에 기능 추가](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)의 일부로 생성 된. vsct 파일에서 가져옵니다.  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>CustomEditor 상황에 맞는 메뉴\</ButtonText>  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 위 텍스트는 텍스트 **CustomEditor 상황**에 맞는 메뉴를 사용 하 여 상황에 맞는 메뉴 명령을 추가 합니다. 메뉴 GUID는이 편집기를 사용 하 여 만든 명령 집합의이 고, 형식은 "Context"입니다.  
  
 Vsct 파일에 정의 하지 않아도 되는 미리 정의 된 명령을 사용할 수도 있습니다. 예를 들어, Visual Studio 패키지 템플릿에서 생성 된 EditorPane.cs 파일을 검사 하는 경우에 정의 된 것과 같은 미리 정의 된 명령 집합이 <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> onSelectAll 메서드와 같은 명령 처리기에서 처리 되는 것을 알 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)

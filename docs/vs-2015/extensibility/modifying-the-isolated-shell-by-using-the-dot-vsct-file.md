---
title: 을 사용 하 여 격리 된 셸 수정 Vsct 파일 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194225"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>.Vsct 파일을 사용하여 격리 셸 수정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 격리 셸 프로젝트용 UI 프로젝트에는 응용 프로그램에서 사용할 수 있는 응용 프로그램 그룹 및 개별 명령을 지정할 수 있는. vsct 파일이 포함 되어 있습니다. 다음은 수정 되지 않은. vsct 파일에서 발췌 한 것입니다.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 기본적으로 대부분의 명령과 명령 그룹이 포함 됩니다. 명령 또는 명령 그룹을 제외 하려면 해당 명령이 나 그룹의 주석 처리를 제거 하면 됩니다.  
  
 예를 들어 다음 창과 이전 창 명령을 제거 하려면 및 항목의 주석 처리를 제거 합니다 `No_PaneNextPaneCommand` `No_PanePrevPaneCommand` .  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 이러한 사용자 지정 예제에 대 한 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.  
  
## <a name="referenced-files"></a>참조 된 파일  
 응용 프로그램의 기본. vsct 파일은 다음 파일을 참조 합니다. 이러한 파일은 Visual Studio SDK 설치 디렉터리의 \VisualStudioIntegration\Common\Inc\ 하위 디렉터리에 있습니다.  
  
|파일|설명|  
|----------|-----------------|  
|wbids|웹 브라우저 패키지에 대 한 UI id입니다.|  
|AppIDCmdUsed. vsct|기본 Visual Studio UI 요소에 대 한 명령 테이블입니다.|  
|EmulatorCmdUsed|Emacs 및 Brief 편집기 에뮬레이션 UI 요소에 대 한 명령 테이블|  
|Vsdebugguids .h|Visual Studio 디버거의 명령, 옵션 페이지 및 기타 기능의 Guid를 정의 합니다.|  
|VsDbgCmdUsed|디버거에 대 한 명령 테이블입니다.|  
  
 AppIDCmdUsed. vsct 파일에는 응용 프로그램 vsct 파일에 정의 된 기호를 기반으로 하는 Visual Studio UI 요소가 포함 됩니다.  
  
 자세한 내용은 [XML 명령 테이블 디자인 (을 참조 하세요. Vsct) 파일](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) 및 [VSCT XML 스키마 참조를 참조](../extensibility/vsct-xml-schema-reference.md)하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio Shell(격리)](../extensibility/visual-studio-isolated-shell.md)

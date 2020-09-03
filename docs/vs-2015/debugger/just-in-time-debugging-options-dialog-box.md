---
title: 옵션 대화 상자, 디버깅, Just-In-Time | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.JIT
- vs.debug.options.JIT
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Just-In-Time debugging, setting options
- Options dialog box, debugging
ms.assetid: 7f11b2e3-3fb5-449d-b07c-6ecf1d6a487d
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b3bd6c6ee32145a94dbc4b751834ecc003f2bdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201111"
---
# <a name="just-in-time-debugging-options-dialog-box"></a>옵션 대화 상자, 디버깅, Just-In-Time
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Just-In-Time** 페이지에 액세스하려면 **도구** 메뉴로 이동하여 **옵션**을 클릭합니다. **옵션** 대화 상자에서 **디버깅** 노드를 확장하고 **Just-In-Time**을 선택합니다. 이 페이지에서는 관리 코드, 네이티브 코드 및 스크립트에 대해 Just-In-Time 디버깅을 사용하도록 설정할 수 있습니다. 자세한 내용은 [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)을 참조하세요.  
  
 다음과 같은 프로그램 유형에 대해 Just-In-Time 디버깅을 사용하도록 설정할 수 있습니다.  
  
- 관리  
  
- 네이티브  
  
- 스크립트  
  
  Just-In-Time 디버깅은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 외부에서 시작된 프로그램을 디버깅하는 기술입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경 외부에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 만든 프로그램을 실행할 수 있습니다. Just-in-time 디버깅을 사용하도록 설정한 상태에서 프로그램이 충돌하면 디버깅할지 여부를 묻는 대화 상자가 표시됩니다.  
  
## <a name="associated-warnings"></a>관련된 경고  
 **옵션** 대화 상자에서 이 페이지를 열면 다음과 같은 경고 메시지가 표시될 수 있습니다.  
  
 **다른 디버거가 자신을 Just-In-Time 디버거로 등록했습니다. 복구하려면 Just-In-Time 디버깅을 사용하도록 설정하거나 Visual Studio 복구를 실행하십시오.**  
  
 이 메시지는 다른 디버거(예: 이전 버전의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디버거)가 Just-In-Time 디버거로 설정되어 있는 경우에 발생합니다.  
  
 다음과 같은 다른 메시지가 표시될 수도 있습니다.  
  
 **Just-In-Time 디버깅 등록 오류가 발견되었습니다. 복구하려면 Just-In-Time 디버깅을 사용하도록 설정하거나 Visual Studio 복구를 실행하십시오.**  
  
 이러한 경고 중 하나가 표시되는 경우 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 Just-In-Time 디버깅을 수행하려면 문제를 해결할 때까지 관리자 권한이 필요합니다. 이러한 상황에서 관리자 이외의 권한으로 Just-In-Time 디버깅을 사용하도록 설정하려고 하면 다음과 같은 오류 메시지가 표시됩니다.  
  
 **액세스가 거부되었습니다. 관리자에게 문의하여 Just-In-Time 디버깅을 사용하도록 설정하거나 Visual Studio 설치를 복구하십시오.**  
  
## <a name="see-also"></a>관련 항목  
 [옵션 대화 상자, 디버깅](../debugger/debugging-options-dialog-box.md)   
 [방법: 디버거 설정 지정](../debugger/how-to-specify-debugger-settings.md)

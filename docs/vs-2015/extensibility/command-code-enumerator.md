---
title: 명령 코드 열거자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f1a3f7146125e59d02efc72a4d4fc9ab33be39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184382"
---
# <a name="command-code-enumerator"></a>명령 코드 열거자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 열거자는 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 및 [SccPopulateList](../extensibility/sccpopulatelist-function.md)에 대 한 옵션에 사용 되며 옵션이 지정 된 명령을 표시 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## <a name="members"></a>멤버  
 SCC_COMMAND_GET  
 [Sccget](../extensibility/sccget-function.md)에 해당 합니다.  
  
 SCC_COMMAND_CHECKOUT  
 [Scccheckout](../extensibility/scccheckout-function.md)에 해당 합니다.  
  
 SCC_COMMAND_CHECKIN  
 [Scccheckin](../extensibility/scccheckin-function.md)에 해당 합니다.  
  
 SCC_COMMAND_UNCHECKOUT  
 [SccUncheckout](../extensibility/sccuncheckout-function.md)에 해당 합니다.  
  
 SCC_COMMAND_ADD  
 [Sccadd](../extensibility/sccadd-function.md)에 해당 합니다.  
  
 SCC_COMMAND_REMOVE  
 [Sccremove](../extensibility/sccremove-function.md)에 해당 합니다.  
  
 SCC_COMMAND_DIFF  
 [Sccdiff](../extensibility/sccdiff-function.md)에 해당 합니다.  
  
 SCC_COMMAND_HISTORY  
 [Scchistory](../extensibility/scchistory-function.md)에 해당 합니다.  
  
 SCC_COMMAND_RENAME  
 [Sccrename](../extensibility/sccrename-function.md)에 해당 합니다.  
  
 SCC_COMMAND_PROPERTIES  
 [Sccproperties](../extensibility/sccproperties-function.md)에 해당 합니다.  
  
 SCC_COMMAND_OPTIONS  
 [Sccsetoption](../extensibility/sccsetoption-function.md)에 해당 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)

---
title: 명령 코드 열거자 | Microsoft Docs
description: 명령 코드 열거자는 옵션이 지정된 명령을 나타내기 위해 SccGetCommandOptions 및 SccPopulateListto 옵션에 사용됩니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b97d5083c4f262ae2d86aeef5ee2627fdc854bcb
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901385"
---
# <a name="command-code-enumerator"></a>명령 코드 열거자
이 열거자는 옵션이 지정된 명령을 나타내기 위해 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 및 [SccPopulateList에](../extensibility/sccpopulatelist-function.md)대한 옵션에 사용됩니다.

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
SCC_COMMAND_GET [SccGet](../extensibility/sccget-function.md)에 해당합니다.

SCC_COMMAND_CHECKOUT [SccCheckout](../extensibility/scccheckout-function.md)에 해당합니다.

SCC_COMMAND_CHECKIN [SccCheckin](../extensibility/scccheckin-function.md)에 해당합니다.

SCC_COMMAND_UNCHECKOUT [SccUncheckout](../extensibility/sccuncheckout-function.md)에 해당합니다.

SCC_COMMAND_ADD [SccAdd에](../extensibility/sccadd-function.md)해당합니다.

SCC_COMMAND_REMOVE [SccRemove](../extensibility/sccremove-function.md)에 해당합니다.

SCC_COMMAND_DIFF [SccDiff](../extensibility/sccdiff-function.md)에 해당합니다.

SCC_COMMAND_HISTORY [SccHistory 에 해당합니다.](../extensibility/scchistory-function.md)

SCC_COMMAND_RENAME [SccRename](../extensibility/sccrename-function.md)에 해당합니다.

SCC_COMMAND_PROPERTIES [SccProperties 에 해당합니다.](../extensibility/sccproperties-function.md)

SCC_COMMAND_OPTIONS [SccSetOption](../extensibility/sccsetoption-function.md)에 해당합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)

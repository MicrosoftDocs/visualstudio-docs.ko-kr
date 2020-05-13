---
title: 명령 코드 열거자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739792"
---
# <a name="command-code-enumerator"></a>명령 코드 열거자
이 열거자는 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 및 [SccPopulateList에](../extensibility/sccpopulatelist-function.md)대 한 옵션에 대 한 옵션에서 사용 됩니다 옵션을 지정 하는 명령을 나타내는.

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
SCC_COMMAND_GET [SccGet에](../extensibility/sccget-function.md)해당합니다.

SCC_COMMAND_CHECKOUT [SccCheckout에](../extensibility/scccheckout-function.md)해당합니다.

SCC_COMMAND_CHECKIN [SccCheckin에](../extensibility/scccheckin-function.md)해당합니다.

SCC_COMMAND_UNCHECKOUT [SccUncheckout에](../extensibility/sccuncheckout-function.md)해당합니다.

SCC_COMMAND_ADD [SccAdd에](../extensibility/sccadd-function.md)해당합니다.

SCC_COMMAND_REMOVE [SccRemove에](../extensibility/sccremove-function.md)해당합니다.

SCC_COMMAND_DIFF [SccDiff에](../extensibility/sccdiff-function.md)해당합니다.

SCC_COMMAND_HISTORY [SccHistory에](../extensibility/scchistory-function.md)해당합니다.

SCC_COMMAND_RENAME [SccRename에](../extensibility/sccrename-function.md)해당합니다.

SCC_COMMAND_PROPERTIES [SccProperties에](../extensibility/sccproperties-function.md)해당합니다.

SCC_COMMAND_OPTIONS [SccSetOption에](../extensibility/sccsetoption-function.md)해당합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)

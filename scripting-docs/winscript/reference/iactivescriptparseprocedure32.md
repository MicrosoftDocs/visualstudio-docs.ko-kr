---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71a22f422ff04e56a7aaa7a715641d190ade47bf
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144391"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Windows 스크립트 엔진에서 프로시저에 대 한 소스 코드 텍스트를 스크립트에 추가할 수 있는 경우에는 인터페이스를 구현 `IActiveScriptParseProcedure32` 합니다. VBScript와 같이 독립적인 제작 환경이 없는 해석 된 스크립트 언어의 경우 `IActiveScriptParse32` `IPersist` 네임 스페이스에 스크립트 프로시저를 추가 하는 대체 메커니즘 (또는 * 제외)을 제공 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|방법|설명|
|-|-|
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|지정 된 코드 프로시저를 구문 분석 하 고 네임 스페이스에 프로시저를 추가 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)
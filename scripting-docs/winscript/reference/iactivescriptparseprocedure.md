---
title: IActiveScriptParseProcedure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3567a22eac2ad270739e62e0f0fb9914bdf4a9ec
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144573"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Windows 스크립트 엔진에서 프로시저에 대 한 소스 코드 텍스트를 스크립트에 추가할 수 있는 경우에는 인터페이스를 구현 `IActiveScriptParseProcedure` 합니다. VBScript와 같이 독립적인 제작 환경이 없는 해석 된 스크립트 언어의 경우 `IActiveScriptParse` `IPersist` 네임 스페이스에 스크립트 프로시저를 추가 하는 대체 메커니즘 (또는 * 제외)을 제공 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|방법|설명|
|-|-|
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|지정 된 코드 프로시저를 구문 분석 하 고 네임 스페이스에 프로시저를 추가 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)
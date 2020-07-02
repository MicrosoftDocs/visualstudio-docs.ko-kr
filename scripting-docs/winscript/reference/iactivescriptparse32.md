---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 568feacfe75de22a330c892a44fa4f4f6fd0e3b8
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835318"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Windows 스크립트 엔진에서 원시 텍스트 코드 스크립틀릿를 스크립트에 추가 하거나 런타임에 식 텍스트를 평가할 수 있도록 허용 하는 경우에는 인터페이스를 구현 `IActiveScriptParse32` 합니다. VBScript와 같이 독립적인 제작 환경이 없는 해석 된 스크립트 언어의 경우이를 통해 `IPersist*` 스크립트 코드를 스크립팅 엔진으로 가져오고 스크립트 조각을 다양 한 개체 이벤트에 연결 하는 대체 메커니즘 (제외)이 제공 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|스크립트에 scriptlet 코드를 추가 합니다.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|스크립팅 엔진을 초기화 합니다.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|지정 된 코드 scriptlet를 구문 분석 하 여, 이름 공간에 선언을 추가 하 고 코드를 적절 하 게 평가 합니다.|
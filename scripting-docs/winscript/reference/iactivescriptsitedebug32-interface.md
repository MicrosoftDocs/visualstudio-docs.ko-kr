---
title: IActiveScriptSiteDebug32 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835266"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 인터페이스
스마트 호스트는 `IActiveScriptSiteDebug32` 문서 관리를 수행 하 고 디버깅에 참여 하는 인터페이스를 구현 합니다. `IActiveScriptSite`개체는 일반적으로 인터페이스의 구현을 제공 합니다 `IActiveScriptSiteDebug32` . 이 작업이 완료 되 면 메서드를 호출 `IActiveScriptSite::QueryInterface` 하 여 인터페이스를 가져옵니다 `IActiveScriptSiteDebug32` .  
  
 에서 상속 된 메서드 외에도 `IUnknown` 인터페이스는 `IActiveScriptSiteDebug32` 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|이 스크립트 사이트와 연결 된 디버그 응용 프로그램 개체를 반환 합니다.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|언어 엔진에서를 위임 하는 데 사용 `IDebugCodeContext::GetSourceContext` 됩니다.|
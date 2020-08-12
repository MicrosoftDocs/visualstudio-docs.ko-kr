---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcf95f74e05ebff6e1cc430c32b9fd7bdb3b005f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144664"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Windows 스크립트 엔진에 대 한 사이트를 만들기 위해 호스트에서 구현 합니다. 일반적으로이 사이트는 스크립트에 표시 되는 모든 개체 (예: ActiveX 컨트롤)의 컨테이너와 연결 됩니다. 일반적으로이 컨테이너는 표시 되는 문서 또는 페이지에 해당 합니다. 예를 들어 Microsoft Internet Explorer는 표시 되는 각 HTML 페이지에 대 한 컨테이너를 만듭니다. 페이지의 각 ActiveX 컨트롤 (또는 다른 자동화 개체) 및 스크립팅 엔진 자체는이 컨테이너 내에서 열거할 수 있습니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|방법|설명|
|-|-|
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|호스트가 사용자 인터페이스 요소를 표시 하는 데 사용 하는 로캘 식별자를 검색 합니다.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|[IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 메서드를 호출 하 여 엔진에 추가 된 항목에 대 한 정보를 가져옵니다.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|호스트의 관점에서 현재 문서 버전을 고유 하 게 식별 하는 호스트 정의 문자열을 검색 합니다.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|스크립트의 실행이 완료 되 면 호출 됩니다.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|스크립팅 엔진의 상태가 변경 되었음을 호스트에 알립니다.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|엔진에서 스크립트를 실행 하는 동안 실행 오류가 발생 했음을 호스트에 알립니다.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|스크립팅 엔진이 스크립트 코드 실행을 시작 했음을 호스트에 알립니다.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|스크립트 코드를 실행 하 여 스크립팅 엔진이 반환 했음을 호스트에 알립니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)
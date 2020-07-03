---
title: 'IActiveScriptParse32:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9ec8395f6c8f404a1d9010234da030c47594e087
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835747"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
스크립트에 scriptlet 코드를 추가 합니다. 이 메서드는 스크립트의 영구 상태가 호스트 문서와 얽혀 호스트는 인터페이스를 통하지 않고 스크립트를 복원 해야 하는 환경에서 사용 됩니다 `IPersist*` . 기본 예제는 HTML 문서에 포함 된 코드의 스크립틀릿를 내장 이벤트 (예를 들어 ONCLICK = "button1 = ' Exit '")에 연결할 수 있는 HTML 스크립팅 언어입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrDefaultName`  
 진행 Scriptlet와 연결할 기본 이름의 주소입니다. 위의 ONCLICK 예제에서와 같이 scriptlet에 명명 정보가 포함 되어 있지 않은 경우이 이름은 scriptlet를 식별 하는 데 사용 됩니다. 이 매개 변수가 이면 `NULL` 스크립팅 엔진은 필요한 경우 고유한 이름을 제조 합니다.  
  
 `pstrCode`  
 진행 추가할 scriptlet 텍스트의 주소입니다. 이 문자열의 해석은 스크립팅 언어에 따라 달라 집니다.  
  
 `pstrItemName`  
 진행 이 scriptlet 연결 된 항목 이름을 포함 하는 버퍼의 주소입니다. 이 매개 변수는 외에도 `pstrSubItemName` scriptlet가 이벤트 처리기 인 개체를 식별 합니다.  
  
 `pstrSubItemName`  
 진행 이 scriptlet가 연결 된 명명 된 항목의 이름을 포함 하는 버퍼의 주소입니다. `subobject` 이 이름은 명명 된 항목의 형식 정보에서 찾을 수 있어야 합니다. 이 매개 변수는 scriptlet이 대신 명명 된 항목과 연결 될 경우 NULL입니다 `subitem` . 이 매개 변수는 외에도 `pstrItemName` scriptlet가 이벤트 처리기 인 특정 개체를 식별 합니다.  
  
 `pstrEventName`  
 진행 Scriptlet가 이벤트 처리기 인 이벤트의 이름을 포함 하는 버퍼의 주소입니다.  
  
 `pstrDelimiter`  
 진행 Scriptlet 끝 구분 기호의 주소입니다. `pstrCode`매개 변수가 텍스트 스트림에서 구문 분석 되 면 호스트는 일반적으로 두 개의 작은따옴표 (' ')와 같은 구분 기호를 사용 하 여 scriptlet의 끝을 검색 합니다. 이 매개 변수는 호스트에서 사용 하는 구분 기호를 지정 하 여 스크립팅 엔진에서 일부 조건부 기본 전처리를 제공할 수 있도록 합니다. 예를 들어 작은따옴표 [']를 구분 기호로 사용 하기 위한 두 개의 작은따옴표로 바꿉니다. 스크립팅 엔진에서이 정보를 사용 하는 정확한 방법 (및)은 스크립팅 엔진에 따라 달라 집니다. 호스트에서 구분 기호를 사용 하 여 scriptlet의 끝을 표시 하지 않은 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwSourceContextCookie`  
 진행 디버깅 목적으로 사용 되는 응용 프로그램 정의 값입니다.  
  
 `ulStartingLineNumber`  
 진행 구문 분석이 시작 되는 줄을 지정 하는 0부터 시작 하는 값입니다.  
  
 `dwFlags`  
 진행 Scriptlet와 연결 된 플래그입니다. 은 다음 값을 조합 하 여 사용할 수 있습니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|스크립트 텍스트를 스크립트의 이름 공간에서 전역 메서드로 표시 하 고, 따라서 이름으로 호출할 수 있음을 나타냅니다.|  
|SCRIPTTEXT_ISPERSISTENT|이 호출 중에 추가 된 코드는 스크립팅 엔진이 저장 된 경우 (예:에 대 한 호출을 통해 `IPersist*::Save` ) 또는 스크립팅 엔진이 초기화 된 상태로 다시 전환 되는 방식으로 다시 설정 된 경우 저장 되어야 함을 나타냅니다. 이 상태에 대 한 자세한 내용은 스크립트 엔진 상태를 참조 하세요.|  
  
 `pbstrName` ,  
 제한이 Scriptlet를 식별 하는 데 사용 되는 실제 이름입니다. 이는 기본적으로 scriptlet 텍스트에 명시적으로 지정 된 이름,에 제공 된 기본 이름 `pstrDefaultName` 또는 스크립팅 엔진에서 합성 한 고유 이름으로 설정 됩니다.  
  
 `pexcepinfo` ,  
 제한이 예외 정보를 포함 하는 구조체의 주소입니다. DISP_E_EXCEPTION 반환 되는 경우이 구조는 채워야 합니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공.|  
|`DISP_E_EXCEPTION`|Scriptlet을 구문 분석 하는 동안 예외가 발생 했습니다. `pexcepinfo`매개 변수에는 예외에 대 한 정보가 포함 됩니다.|  
|`E_INVALIDARG`|인수가 잘못된 경우.|  
|`E_NOTIMPL`|이 메서드는 지원 되지 않습니다. 스크립팅 엔진은 이벤트 싱크 스크립틀릿을 추가 하는 것을 지원 하지 않습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출을 수행할 수 없습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았기 때문에 실패 했습니다.|  
|`OLESCRIPT_E_INVALIDNAME`|제공 된 기본 이름은이 스크립트 언어에서 사용할 수 없습니다.|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet에서 지정 되지 않은 구문 오류가 발생 했습니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)
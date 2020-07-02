---
title: IActiveScriptParse32::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e26b5cb1790cab38a6544a04307b7e336a952519
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835370"
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
지정 된 코드 scriptlet를 구문 분석 하 여 네임 스페이스에 선언을 추가 하 고 코드를 적절 하 게 평가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|`pstrCode`|진행 평가할 scriptlet 텍스트의 주소입니다. 이 문자열의 해석은 스크립팅 언어에 따라 달라 집니다.|  
|`pstrItemName`|진행 Scriptlet을 평가할 컨텍스트를 제공 하는 항목 이름의 주소입니다. 이 매개 변수가 NULL 이면 스크립팅 엔진의 전역 컨텍스트에서 코드가 평가 됩니다.|  
|`punkContext`|진행 컨텍스트 개체의 주소입니다. 이 개체는 디버깅 환경에서 사용 하도록 예약 되어 있습니다. 이러한 컨텍스트는 디버거에서 활성 런타임 컨텍스트를 나타내는 컨텍스트를 제공할 수 있습니다. 이 매개 변수가 NULL 인 경우 엔진은 `pstrItemName` 를 사용 하 여 컨텍스트를 식별 합니다.|  
|`pstrDelimiter`|진행 Scriptlet 끝 구분 기호의 주소입니다. `pstrCode`가 텍스트 스트림에서 구문 분석 될 때 호스트는 일반적으로 두 개의 작은따옴표 (' ')와 같은 구분 기호를 사용 하 여 scriptlet의 끝을 검색 합니다. 이 매개 변수는 호스트에서 사용 하는 구분 기호를 지정 하 여 스크립팅 엔진에서 일부 조건부 기본 전처리를 제공할 수 있도록 합니다. 예를 들어 작은따옴표 [']를 구분 기호로 사용 하기 위한 두 개의 작은따옴표로 바꿉니다. 스크립팅 엔진에서이 정보를 사용 하는 정확한 방법 (및)은 스크립팅 엔진에 따라 달라 집니다. `NULL`호스트에서 구분 기호를 사용 하 여 scriptlet의 끝을 표시 하지 않은 경우이 매개 변수를로 설정 합니다.|  
|`dwSourceContextCookie`|진행 디버깅 목적으로 사용 되는 쿠키입니다.|  
|`ulStartingLineNumber`|진행 구문 분석이 시작 되는 줄을 지정 하는 0부터 시작 하는 값입니다.|  
|`dwFlags`|진행 Scriptlet와 연결 된 플래그입니다. 는 다음과 같은 값을 조합 하 여 사용할 수 있습니다.|  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|계산 식과 문 간의 차이가 중요 하지만 스크립트 언어에서 구문상 모호한 경우이 플래그는 scriptlet이 문 또는 문 목록이 아니라 식으로 해석 되도록 지정 합니다. 기본적으로 scriptlet 텍스트의 구문에서 올바른 선택 항목을 결정할 수 없으면 문이 가정 됩니다.|  
|SCRIPTTEXT_ISPERSISTENT|이 호출 중에 추가 된 코드는 스크립팅 엔진이 저장 된 경우 (예:에 대 한 호출을 통해 `IPersist*::Save` ) 또는 스크립팅 엔진이 초기화 된 상태로 다시 전환 되는 방식으로 다시 설정 된 경우 저장 되어야 함을 나타냅니다.|  
|SCRIPTTEXT_ISVISIBLE|스크립트 텍스트를 스크립트의 이름 공간에서 전역 메서드로 표시 하 고, 따라서 이름으로 호출할 수 있음을 나타냅니다.|  
  
|||  
|-|-|  
|`pvarResult`|제한이 Scriptlet 처리 결과를 수신 하는 버퍼의 주소 이거나 `NULL` , 호출자가 결과를 예상 하지 않는 경우 (즉, SCRIPTTEXT_ISEXPRESSION 값이 설정 되지 않은 경우)입니다.|  
|`pexcepinfo`|제한이 예외 정보를 받는 구조체의 주소입니다. 이 구조체는 DISP_E_EXCEPTION을 반환 하는 경우 채워집니다 `IActiveScriptParse::ParseScriptText` .|  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공.|  
|`DISP_E_EXCEPTION`|Scriptlet를 처리 하는 동안 예외가 발생 했습니다. `pexcepinfo`매개 변수에는 예외에 대 한 정보가 포함 됩니다.|  
|`E_INVALIDARG`|인수가 잘못된 경우.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_NOTIMPL`|이 메서드는 지원되지 않습니다. 스크립팅 엔진은 식 또는 문의 런타임 계산을 지원 하지 않습니다.|  
|`E_UNEXPECTED`|호출을 사용할 수 없습니다. 예를 들어 스크립팅 엔진이 초기화 되지 않았거나 닫힘 상태 이거나 SCRIPTTEXT_ISEXPRESSION 플래그가 설정 되었으며 스크립팅 엔진이 초기화 된 상태에 있습니다.|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet에서 지정 되지 않은 구문 오류가 발생 했습니다.|  
  
## <a name="remarks"></a>설명  
 스크립팅 엔진이 초기화 된 상태 이면 실제로이 호출 중에 코드는 계산 되지 않습니다. 대신 이러한 코드는 스크립팅 엔진이 시작 됨 상태로 전환 될 때 큐에 대기 되 고 실행 됩니다. 초기화 된 상태에서는 실행이 허용 되지 않기 때문에 초기화 된 상태에 있을 때 SCRIPTTEXT_ISEXPRESSION 플래그를 사용 하 여이 메서드를 호출 하면 오류가 발생 합니다.  
  
 Scriptlet는 식, 문 목록 또는 스크립트 언어에서 허용 하는 모든 것이 될 수 있습니다. 예를 들어이 메서드는 html 태그를 평가 하는 데 사용 됩니다 .이 메서드를 사용 하면 \<SCRIPT> html 페이지가 생성 될 때 스크립트 상태로 컴파일하는 대신 문을 실행할 수 있습니다.  
  
 이 메서드에 전달 된 코드는 유효한 전체 코드 부분 이어야 합니다. 예를 들어 VBScript에서 Sub 함수 (x)를 사용 하 여이 메서드를 한 번 호출한 다음를 사용 하 여이 메서드를 두 번 호출할 수 없습니다 `End Sub` . 파서는 서브루틴을 완료 하기 위해 두 번째 호출이 대기 하지 않고 서브루틴 선언이 시작 되었지만 완료 되지 않았기 때문에 구문 분석 오류를 생성 해야 합니다.  
  
 스크립트 상태에 대 한 자세한 내용은 [Windows 스크립트](../../winscript/windows-script-engines.md)엔진의 스크립트 엔진 상태 섹션을 참조 하십시오.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)
---
title: QUERY[FUNC] | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42f901fa31b3b682c7e19c98f5707adb3b4fb3f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193842"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 [Sccquerychanges](../extensibility/sccquerychanges-function.md) 작업에서 파일 이름의 컬렉션을 열거 하 고 각 파일의 상태를 확인 하는 데 사용 하는 콜백 함수입니다.  
  
 함수에는 `SccQueryChanges` 파일 목록 및 콜백에 대 한 포인터가 제공 됩니다 `QUERYCHANGESFUNC` . 소스 제어 플러그 인은 지정 된 목록에 대해 열거 하 고 목록에 있는 각 파일에 대해이 콜백을 통해 상태를 제공 합니다.  
  
## <a name="signature"></a>서명  
  
```cpp#  
typedef BOOL (*QUERYCHANGESFUNC)(  
   LPVOID pvCallerData,  
   QUERYCHANGESDATA * pChangesData  
);  
```  
  
## <a name="parameters"></a>매개 변수  
 pvCallerData  
 진행 `pvCallerData` 호출자 (IDE)가 [Sccquerychanges](../extensibility/sccquerychanges-function.md)에 전달 하는 매개 변수입니다. 소스 제어 플러그 인은이 값의 내용에 대해 가정 하지 않아야 합니다.  
  
 P) 데이터  
 진행 파일에 대 한 변경 내용을 설명 하는 [querychanges 데이터 구조](#LinkQUERYCHANGESDATA) 구조에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 IDE에서 적절 한 오류 코드를 반환 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|처리를 계속합니다.|  
|SCC_I_OPERATIONCANCELED|처리를 중지합니다.|  
|SCC_E_xxx|적절 한 SCC 오류가 처리를 중지 해야 합니다.|  
  
## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERY데이터 구조  
 각 파일에 대해 전달 되는 구조는 다음과 같습니다.  
  
```cpp#  
struct QUERYCHANGESDATA_A  
{  
    DWORD  dwSize;  
    LPCSTR lpFileName;  
    DWORD  dwChangeType;  
    LPCSTR lpLatestName;  
};  
  
typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;  
  
struct QUERYCHANGESDATA_W  
{  
    DWORD   dwSize;  
    LPCWSTR lpFileName;  
    DWORD   dwChangeType;  
    LPCWSTR lpLatestName;  
};  
```  
  
 dwSize  
 이 구조체의 크기 (바이트)입니다.  
  
 lpFileName  
 이 항목에 대 한 원래 파일 이름입니다.  
  
 dwChangeType  
 파일의 상태를 나타내는 코드입니다.  
  
|코드|Description|  
|----------|-----------------|  
|`SCC_CHANGE_UNKNOWN`|변경 된 내용을 알릴 수 없습니다.|  
|`SCC_CHANGE_UNCHANGED`|이 파일에 대 한 이름 변경 내용이 없습니다.|  
|`SCC_CHANGE_DIFFERENT`|Id가 같지만 데이터베이스에 이름이 같은 파일이 있습니다.|  
|`SCC_CHANGE_NONEXISTENT`|파일이 데이터베이스에 없거나 로컬로 존재 하지 않습니다.|  
|`SCC_CHANGE_DATABASE_DELETED`|파일이 데이터베이스에서 삭제 되었습니다.|  
|`SCC_CHANGE_LOCAL_DELETED`|파일이 로컬에서 삭제 되었지만 파일이 데이터베이스에 여전히 있습니다. 확인할 수 없는 경우를 반환 `SCC_CHANGE_DATABASE_ADDED` 합니다.|  
|`SCC_CHANGE_DATABASE_ADDED`|파일이 데이터베이스에 추가 되었지만 로컬에 없습니다.|  
|`SCC_CHANGE_LOCAL_ADDED`|파일이 데이터베이스에 없고 새 로컬 파일입니다.|  
|`SCC_CHANGE_RENAMED_TO`|파일의 이름이 바뀌었거나 데이터베이스에서로 이동 `lpLatestName` 되었습니다.|  
|`SCC_CHANGE_RENAMED_FROM`|에서 데이터베이스의 이름을 바꾸거나 이동 했습니다. `lpLatestName` 추적 하는 데 비용이 많이 드는 경우와 같은 다른 플래그를 반환 `SCC_CHANGE_DATABASE_ADDED` 합니다.|  
  
 lpLatestName  
 이 항목의 현재 파일 이름입니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDE에서 구현 하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)   
 [오류 코드](../extensibility/error-codes.md)

---
title: 'IDebugSettingsCallback2:: GetEEMetricFile | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricFile
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 30b7822bcabbe2f283c25a3e22f1e650269e7e62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155198"
---
# <a name="idebugsettingscallback2geteemetricfile"></a>IDebugSettingsCallback2::GetEEMetricFile
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이름 또는 메트릭이 지정 된 식 계산기 메트릭 파일을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetEEMetricFile(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetEEMetricFile(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guidLang`  
 진행 프로그래밍 언어의 고유 식별자입니다.  
  
 `guidVendor`  
 진행 공급 업체의 고유 식별자입니다.  
  
 `pszMetric`  
 진행 메트릭의 이름입니다.  
  
 `pbstrValue`  
 제한이 메트릭 파일의 내용을 문자열로 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

---
title: 'Idebug심볼 Providerdirect:: GetMethodFromAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 16ba628887f1910738df825a0965959715c5d250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155108"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 디버그 주소에서 메서드에 대 한 정보를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetMethodFromAddress(  
   IDebugAddress* pAddress,  
   GUID*          pGuid,  
   DWORD*         pAppID,  
   _mdToken*      pTokenClass,  
   _mdToken*      pTokenMethod,  
   DWORD*         pdwOffset,  
   DWORD*         pdwVersion  
);  
```  
  
```csharp  
int GetMethodFromAddress(  
   IDebugAddress pAddress,  
   out Guid      pGuid,  
   out uint      pAppID,  
   out uint      pTokenClass,  
   out uint      pTokenMethod,  
   out uint      pdwOffset,  
   out uint      pdwVersion  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pAddress`  
 진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표시 되는 디버그 주소입니다.  
  
 `pGuid`  
 제한이 모듈의 고유 식별자입니다.  
  
 `pAppID`  
 제한이 응용 프로그램 도메인의 식별자입니다.  
  
 `pTokenClass`  
 제한이 포함 하는 클래스를 나타내는 토큰입니다.  
  
 `pTokenMethod`  
 제한이 모듈을 나타내는 토큰입니다.  
  
 `pdwOffset`  
 제한이 매개 변수의 시작 부분에서의 오프셋 (바이트) `pAddress` 입니다.  
  
 `pdwVersion`  
 제한이 메서드의 버전 번호입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)

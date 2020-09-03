---
title: Idebug기호 Providerdirect | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1ad768419786f78277b791997538785265a24c0f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153091"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

메타 데이터 및 핵심 기호 인터페이스에 직접 액세스할 수 있는 기호 공급자를 나타냅니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>메서드  
 이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|디버그 주소가 지정 된 경우 응용 프로그램 도메인 식별자를 검색 합니다.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|기호 그룹의 모듈에 대 한 정보를 검색 합니다.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|기호 공급자가 멤버인 기호 그룹에 대 한 정보를 검색 합니다.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|메타 데이터 가져오기 정보를 검색 합니다.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|지정 된 디버그 주소에서 메서드에 대 한 정보를 검색 합니다.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|비관리 코드에 대 한 기호 판독기를 검색 합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 대부분의 다른 기호 공급자 인터페이스 대신 사용할 수 있습니다. 메타 데이터 및 인터페이스에 대 한 직접 액세스를 제공 합니다 `CorSym` .  
  
## <a name="requirements"></a>요구 사항  
 헤더: Sh  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

---
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ed8327690c42f54a33209b2f0acfa45a138ec51c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155087"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 메서드는 시각화 도우미 서비스를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `binder`  
 진행 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)에 전달 된 [idebugbinder](../../../extensibility/debugger/reference/idebugbinder.md) 개체입니다.  
  
 `pSymProv`  
 진행 에 전달 된 [Idebug 공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md) 개체 `IDebugParsedExpression::EvaluateSync` 입니다.  
  
 `pAddress`  
 진행 에 전달 된 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체 `IDebugParsedExression::EvaluateSync` 입니다.  
  
 `dataProvider`  
 진행 식 계산기에서 제공 하는 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) 인터페이스를 구현 하는 개체입니다.  
  
 `ppService`  
 제한이 만든 서비스입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 `binder`, `pSymProv` 및 `pAddress` 매개 변수가 모두 메서드에 전달 되었습니다 `IDebugParsedExpression::EvaluateSync` . `CreateVisualizerService` 는 `IDebugParsedExpression::EvaluateSync` 형식 시각화 도우미에 대 한 식 계산기의 지원의 일부로 서만 호출 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [Idebug기호 공급자](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

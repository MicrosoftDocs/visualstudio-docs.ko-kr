---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d68b0db20150bd81a9b2b4aef29c78701a6bc8ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841966"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 방법은 더 이상 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 [Clr 식](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 계산기 및 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)을 참조 하세요.  
  
 관리 되는 배열 개체를 나타내며, 식 계산기 (EE)에서 배열에 대 한 기본 인덱스 (하한값)를 결정 하도록 허용 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 이는 관리 되는 디버그 엔진 (DE)에 의해 구현 됩니다.  
  
## <a name="methods"></a>메서드  
 [Idebugarrayobject](../../../extensibility/debugger/reference/idebugarrayobject.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.  
  
|메서드|Description|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|배열의 차원 수가 지정 된 경우 각 인덱스의 기본 인덱스 (하한값)를 검색 합니다.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|배열에 기본 인덱스 (더 낮은 범위)가 정의 되어 있는지 여부를 확인 합니다.|  
  
## <a name="remarks"></a>설명  
 식 계산기는이 인터페이스를 사용 하 여 구문 분석 트리에서 관리 되는 배열을 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Ee. h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

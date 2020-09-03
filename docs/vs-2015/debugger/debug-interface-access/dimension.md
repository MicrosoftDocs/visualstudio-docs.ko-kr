---
title: 차원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Dimension Symbol
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b760d6a7808154b8daabe43d4cf6399c3b91977
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164337"
---
# <a name="dimension"></a>차원
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

각 포트란 배열에는 기호로 식별 되는 차원이 있습니다 `SymTagDimension` .  
  
## <a name="properties"></a>속성  
 다음 표에서는이 기호 형식에 대 한 추가 유효한 속성을 보여 줍니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|`IDiaSymbol*`|포트란 배열 차원의 하 한입니다.|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|`DWORD`|하위 바운드 기호의 ID입니다.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|기호의 인덱스 ID입니다.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|`SymTagDimension` [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 값 중 하나를 반환 합니다.|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|포트란 배열 차원의 상한입니다.|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|상한 기호의 ID입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [기호 형식의 클래스 계층 구조](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

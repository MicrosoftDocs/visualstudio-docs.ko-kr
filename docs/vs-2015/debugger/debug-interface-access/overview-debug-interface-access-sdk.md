---
title: 개요 (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179205"
---
# <a name="overview-debug-interface-access-sdk"></a>개요(디버그 인터페이스 액세스 SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

DIA SDK를 사용 하 여 Microsoft 디버그 정보에 액세스 합니다. DIA SDK는 Microsoft에서 디버그 정보 형식을 변경할 때마다 코드를 다시 작성할 필요가 없도록 하는 COM 기반 API 집합을 제공 합니다. DIA SDK를 사용 하 여 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 버전 5.0 이상에서 생성 된 .pdb 및 dbg 파일에 있는 이전 버전의 디버그 정보를 선택할 수도 있습니다.  
  
 DIA SDK의 각 인터페이스는 별도로 명시 된 경우를 제외 하 고 다른 COM 개체를 나타냅니다. 추가 인터페이스 및 따라서 추가 개체는 기존 인터페이스 포인터에서를 호출 하는 대신 [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) 또는 [IDiaSession:: findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md)과 같은 명시적 쿼리를 통해 생성 됩니다 `QueryInterface` .  
  
## <a name="see-also"></a>관련 항목  
 [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

---
title: 포트 공급자 구현 및 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842111"
---
# <a name="implementing-and-registering-a-port-supplier"></a>포트 공급자 구현 및 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

포트 공급자의 역할은 포트를 추적 하 고 제공 하 여 프로세스를 관리 하는 것입니다. 포트를 만들어야 할 때 포트 공급자는 포트 공급자의 GUID를 사용 하 여 CoCreate를 사용 하 여 인스턴스화됩니다 (세션 디버그 관리자 [SDM]은 사용자가 선택한 포트 공급자 또는 프로젝트 시스템에서 지정한 포트 공급자를 사용 함). 그러면 SDM이 [Canaddport](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) 를 호출 하 여 포트를 추가할 수 있는지 확인 합니다. 포트를 추가할 수 있는 경우 [Addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 를 호출 하 고 포트를 설명 하는 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) 를 전달 하 여 새 포트를 요청 합니다. `AddPort` 는 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스로 표시 되는 새 포트를 반환 합니다.  
  
## <a name="discussion"></a>토론(Discussion)  
 포트 공급자가 포트를 만든 후 컴퓨터 또는 디버그 서버와 연결 합니다. 서버는[Enumportsuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 메서드를 통해 해당 포트 공급자를 열거할 수 있으며, 포트 공급자는 [enumports](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 메서드를 통해 해당 포트를 열거할 수 있습니다.  
  
 일반적인 COM 등록 외에도 포트 공급자는 특정 레지스트리 위치에 CLSID와 이름을 배치 하 여 Visual Studio에 등록 해야 합니다. 이라는 디버깅 SDK 도우미 함수는 `SetMetric` 이 chore를 처리 합니다. 즉, 등록할 각 항목에 대해 한 번씩 호출 됩니다.  
  
```cpp#  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricCLSID,  
          <CLSID of your port supplier>,  
          false,  
          NULL)  
SetMetric(metrictypePortSupplier,  
          <GUID of your port supplier>,  
          metricName,  
          <name of your port supplier>,  
          false,  
          NULL);  
```  
  
 포트 공급자는 `RemoveMetric` 등록 된 각 항목에 대해 한 번씩 (다른 디버깅 SDK 도우미 함수)를 호출 하 여 자체의 등록을 취소 합니다. 따라서 다음이 수행 됩니다.  
  
```cpp#  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricCLSID,  
             NULL);  
RemoveMetric(metrictypePortSupplier,  
             <GUID of your port supplier>,  
             metricName,  
             NULL);  
```  
  
> [!NOTE]
> [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` 는 `RemoveMetric` dbgmetric에 정의 되 고 ad2de로 컴파일되는 정적 함수입니다. `metrictypePortSupplier`, `metricCLSID` 및 도우미는 `metricName` dbgmetric에도 정의 되어 있습니다.  
  
 포트 공급자는 [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) 및 [getportsupplierid](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)메서드를 통해 각각 이름 및 GUID를 제공할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [포트 공급자 구현](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [포트 공급자](../../extensibility/debugger/port-suppliers.md)

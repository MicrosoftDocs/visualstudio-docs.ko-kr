---
title: UnInit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0bec86a7f872057b7a0d652df6346e3a1ef2ff8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197933"
---
# <a name="uninit"></a>UnInit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 로그 파일을 종료하고 닫고 앱이 그래픽 정보를 기록하는 동안 사용된 리소스를 확보합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void UnInit();  
```  
  
## <a name="remarks"></a>설명  
 `UnInit` 클래스의 인스턴스가 소멸될 때 `VsgDbg` 가 자동으로 호출됩니다. `VsgDbg` 인스턴스가 그래픽 정보를 기록하지 않는 경우 아무런 영향이 없습니다.  
  
 `UnInit` 클래스의 인스턴스에서 `VsgDbg`가 호출된 경우 `Init`를 호출하여 새 그래픽 로그 파일을 만들고 `UnInit`를 호출하여 종료할 수 있습니다. 동일한 `VsgDbg` 인스턴스를 사용하여 원하는 횟수만큼 이 작업을 반복하여 여러 독립 그래픽 로그 파일을 만들 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Init](../debugger/init.md)

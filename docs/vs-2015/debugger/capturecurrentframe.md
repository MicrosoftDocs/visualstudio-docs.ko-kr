---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2718e800e2a31eb66319259ed1e43f2ab8b084c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161641"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 로그 파일에 현재 프레임의 나머지 부분을 캡처합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## <a name="remarks"></a>설명  
 다른 캡처가 현재 진행 중인 경우(예: `BeginCapture` 함수에 의해 시작된 캡처) 해당 캡처를 완료하고 그래픽 로그에 다른 프레임으로 기록합니다. 이후에 즉시 그래픽 진단에서 다른 프레임으로도 기록되는 현재 프레임의 나머지 부분 캡처를 시작합니다. 현재 프레임의 끝은 호출로 표시됩니다.  
  
 프레임을 캡처하려면 그래픽 정보를 캡처하고 기록하도록 앱을 준비해야 합니다. 즉, `CaptureCurrentFrame`을 호출하기 전에 `VsgDbg` 클래스의 인스턴스를 통해 [Init](../debugger/init.md)을 호출해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Cloud-init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)

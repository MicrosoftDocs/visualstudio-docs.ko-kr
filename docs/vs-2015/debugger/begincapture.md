---
title: BeginCapture | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b16fdc4d0a12d7082400e697ca44a7ca4c549f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431799"
---
# <a name="begincapture"></a>BeginCapture
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`EndCapture`로 종료되는 캡처 간격을 시작합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
void BeginCapture();  
```  
  
## <a name="remarks"></a>설명  
 캡처 간격은 일반적으로 특정 그리기 호출 종류에 대한 그래픽 정보만 호출하려고 할 때와 같이 한 프레임의 하위 집합을 확장합니다. 캡처 간격이 존재하는 호출을 확장하는 경우 그래픽 정보의 두 프레임이 캡처됩니다. 첫 번째 프레임은 `BeginCapture`에 대한 호출과 존재하는 호출 간에 간격을 확장하고 두 번째 프레임은 존재하는 호출 이후 첫 번째 Direct3D 이벤트와 `EndCapture`에 대한 호출 간의 간격을 확장합니다.  
  
 간격을 캡처하려면 그래픽 정보를 캡처하고 기록하도록 앱을 준비해야 합니다. 즉, `BeginCapture` 또는 `EndCapture`를 호출하기 전에 `VsgDbg` 클래스의 인스턴스를 통해 [Init](../debugger/init.md)를 호출했어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)

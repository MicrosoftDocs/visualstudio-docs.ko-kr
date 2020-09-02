---
title: VsgDbg::VsgDbg(생성자) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157435"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg(생성자)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 진단의 사용자 앱 구성 요소를 준비하거나 준비하지 않고 `VsgDbg` 클래스의 인스턴스를 생성하여 지정된 Boolean 매개 변수에 따라 그래픽 정보를 캡처하고 기록합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `bDefaultInit`  
 `true` 그래픽 정보를 적극적으로 캡처하고 기록 하도록 그래픽 진단의 앱 내 구성 요소를 준비 하도록 지정 하려면 지금은 `false` 응용 프로그램에서 그래픽 정보를 적극적으로 캡처하고 기록 하도록 준비 하지 않도록 지정 합니다.  
  
## <a name="remarks"></a>설명  
 생성자가 `true`로 설정된 `bDefaultInit`로 호출되는 경우 그래픽 로그 파일의 파일 이름이 앱에 `vsgcapture.h`가 포함되기 전에 `DONT_SAVE_VSGLOG_TO_TEMP` 및 `VSG_DEFAULT_RUN_FILENAME` 전처리기 기호가 정의되는 방식에 따라 결정됩니다.  
  
 `bDefaultInit`이 `false`로 설정된 상태로 생성자가 호출되면 `Init` 함수를 호출하여 나중에 그래픽 정보를 캡처하고 기록하도록 그래픽 진단의 사용자 앱 구성 요소를 준비할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [VsgDbg:: ~ VsgDbg (소멸자)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Cloud-init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)

---
title: VsgDbg::~VsgDbg(소멸자) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200298"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg(소멸자)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`VsgDbg` 클래스의 인스턴스를 제거합니다. 그래픽 정보가 활발히 기록되고 있는 경우 그래픽 로그 파일은 종료되고 닫히며 그래픽 정보를 활발히 캡처하는 동안 사용된 리소스는 해제됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>관련 항목  
 [VsgDbg::VsgDbg(생성자)](../debugger/vsgdbg-vsgdbg-constructor.md)

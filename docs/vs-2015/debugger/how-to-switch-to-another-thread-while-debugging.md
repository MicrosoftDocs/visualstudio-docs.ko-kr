---
title: '방법: 디버깅 중 다른 스레드로 전환 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176518"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>방법: 디버깅 중 다른 스레드로 전환
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다중 스레드 애플리케이션을 디버깅하는 경우 작업 중인 스레드에서 다른 스레드로 컨텍스트를 전환하는 여러 가지 방법 중 하나를 사용할 수 있습니다.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>스레드 창에 나타나는 스레드로 전환하려면  
  
- 스레드를 두 번 클릭합니다.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>소스 창에서 스레드를 전환하려면  
  
- 왼쪽 여백에서 스레드 표시기를 마우스 오른쪽 단추로 클릭 하 고 **전환**을 가리킨 다음 전환 하려는 스레드의 이름을 클릭 합니다. 특정 위치의 스레드만 바로 가기 메뉴에 표시됩니다.  
  
     표시기가 표시 되지 않으면 **스레드** 창을 마우스 오른쪽 단추로 클릭 하 고 **소스에 스레드 표시** 가 선택 되어 있는지 확인 합니다.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>디버그 위치 도구 모음에서 스레드로 전환하려면  
  
1. **디버그 위치** 도구 모음에서 **스레드** 상자를 클릭 합니다.  
  
2. 목록에서 전환할 스레드를 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)

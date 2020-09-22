---
title: '방법: ETW(Windows용 이벤트 추적) 데이터 수집 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d113a32622c40c68a030fdbc670ec19c6038de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841859"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>방법: ETW(Windows용 이벤트 추적) 데이터 수집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ETW(Windows용 이벤트 추적)는 프로파일러 로그 커널 이벤트나 애플리케이션에서 거부된 이벤트를 사용하도록 설정하는 효율적인 커널 수준 추적 기능입니다. 이벤트 공급자에서 수집된 데이터를 보려면 [VSPerfReport](../profiling/vsperfreport.md) 명령줄 도구의 /**Summary:ETW** 옵션을 사용해야 합니다. 이 보고서를 사용하여 애플리케이션에서 성능 문제가 발생하는 위치를 확인합니다.  
  
 **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
### <a name="to-enable-event-trace-providers"></a>이벤트 추적 공급자를 사용하도록 설정하려면  
  
1. **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
2. **속성 페이지**에서 **Windows 이벤트** 속성을 클릭합니다.  
  
3. **데이터를 수집할 이벤트 추적 공급자 선택** 목록에서 애플리케이션을 프로파일링하는 데 사용할 이벤트 공급자를 선택합니다.  
  
## <a name="see-also"></a>참고 항목  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)

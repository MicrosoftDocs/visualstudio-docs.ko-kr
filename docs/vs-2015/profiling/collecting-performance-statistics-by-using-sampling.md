---
title: 샘플링을 사용하여 성능 통계 수집 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b84674eafde85528e04157ab213913e57d27e60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842210"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>샘플링을 사용하여 성능 통계 수집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

기본적으로는 [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] 프로파일링 도구 샘플링 방법은 10,000,000 프로세서 주기마다(1GHz 컴퓨터에서 약 1/100초마다) 프로파일링 정보를 수집합니다. 샘플링 방법은 프로세서 사용률 문제를 찾는 데 유용하며, 대부분의 성능 조사를 시작할 수 있는 방법으로 제안됩니다.  
  
 **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. Windows 스토어 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.  
  
 다음 절차 중 하나를 사용하여 샘플링 방법을 지정할 수 있습니다.  
  
- 프로파일링 마법사의 첫 번째 페이지에서 **CPU 샘플링(권장)** 을 클릭합니다.  
  
- **성능 탐색기** 도구 모음의 **메서드** 목록에서 **샘플링**을 클릭합니다.  
  
- 성능 세션에 대한 속성 대화 상자의 **일반** 페이지에서 **샘플링**을 클릭합니다.  
  
## <a name="common-tasks"></a>일반 태스크  
 성능 세션의 _성능 세션_**속성 페이지** 대화 상자에서 추가 옵션을 지정할 수 있습니다. 이 대화 상자를 열려면  
  
- **성능 탐색기**에서 성능 세션 이름을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.  
  
  다음 표의 작업에서는 샘플링 방법을 사용 하 여 프로 파일링 할 때 _성능 세션_**속성 페이지** 대화 상자에서 지정할 수 있는 옵션을 설명 합니다.  
  
|작업|관련 내용|  
|----------|---------------------|  
|**일반** 페이지에서 .NET 메모리 할당 및 수명 데이터 수집을 추가하고 생성된 프로파일링 데이터(.vsp) 파일에 대한 이름 지정 세부 정보를 지정합니다.|-   [.NET 메모리 할당 및 수명 데이터 수집](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [방법: 성능 데이터 파일 이름 옵션 설정](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**샘플링** 페이지에서 샘플링 주기를 변경하고 프로세서 클록 주기에서 다른 프로세서 성능 카운터로 샘플링 이벤트를 변경하거나 둘 모두를 변경...|-   [방법: 샘플링 이벤트 선택](../profiling/how-to-choose-sampling-events.md)|  
|**시작** 페이지에서 코드 솔루션에 여러 .exe 프로젝트가 있는 경우 시작할 애플리케이션 및 시작 순서를 지정합니다.|-   [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)|  
|**계층 상호 작용** 페이지에서 프로파일링 실행 시 수집된 데이터에 ADO.NET 호출 정보를 추가합니다.|-   [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)|  
|**Windows 이벤트** 페이지에서 샘플링 데이터로 수집할 ETW(Windows용 이벤트 추적) 이벤트를 하나 이상 지정합니다.|-   [방법: ETW (ETW(Windows용 이벤트 추적)) 데이터 수집](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|**Windows 카운터** 페이지에서 프로파일링 데이터에 표시로 추가할 운영 체제 성능 카운터를 하나 이상 지정합니다.|-   [방법: Windows 카운터 데이터 수집](../profiling/how-to-collect-windows-counter-data.md)|  
|**고급** 페이지에서, 애플리케이션 모듈이 여러 버전을 사용하는 경우 프로파일링할 .NET Framework 런타임의 버전을 지정합니다. 기본적으로 첫 번째 로드된 버전이 프로파일링됩니다.|-   [방법: .NET Framework 런타임 지정](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|

---
title: 성능 탐색기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance
- vs.performance.wizard.website
helpviewer_keywords:
- performance tools [Visual Studio ALM]
ms.assetid: df52b717-a55d-4b1d-8c2e-d5a6a38042f4
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 251b805367922d032eb90a70a9ba8ae9d8bd01f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155499"
---
# <a name="performance-explorer"></a>성능 탐색기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개발자는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구를 사용하여 코드의 성능 관련 문제를 측정, 평가 및 조정할 수 있습니다. 이러한 도구는 IDE에 완벽하게 통합되어 원활하고 편리한 사용자 환경을 제공합니다.  
  
 애플리케이션을 프로파일링하는 것은 간단합니다. 먼저 새 성능 세션을 만듭니다. Visual Studio Team System Development Edition에서는 성능 세션 마법사를 사용해서 새 성능 세션을 만들 수 있습니다. 성능 세션이 끝난 후 프로파일링하는 동안 수집된 데이터가 .vsp 파일에 저장됩니다. IDE 안에서 .vsp 파일을 볼 수 있습니다. 수집된 데이터에서 성능 문제를 시각화하고 감지하기 위해 여러 보고서 뷰를 사용할 수 있습니다.  
  
 명령줄에서 프로파일링 도구도 사용할 수 있습니다. 이를 통해 유연하게 명령줄에서 이러한 도구를 실행할 수도 있고 이러한 도구로 스크립트를 사용하는 작업을 자동화할 수도 있습니다.  
  
 성능 및 프로파일링과 관련된 현재 및 고급 항목에 대한 자세한 내용을 보려면 Microsoft Developer Network에서 항목 및 Microsoft 블로그를 검색하세요. “엔터프라이즈 성능 도구 팀” 키워드를 사용하세요.  
  
## <a name="common-tasks"></a>일반 태스크  
  
|Task|관련 내용|  
|----------|---------------------|  
|**Windows 8에 대한 새로운 기술**|[Windows 8 및 Windows Server 2012 응용 프로그램의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)|  
|**프로파일링 개념 이해:** 프로파일링 도구를 사용하여 코드 성능을 수집하고, 보고, 분석하는 데 사용하는 개념 및 용어에 대해 알아봅니다.|[개요](../profiling/overviews-performance-tools.md)|  
|**시작 및 작업:** 프로파일링 도구를 사용하여 코드 성능을 수집하고, 보고, 분석할 때 사용하는 기본적인 절차에 대해 알아봅니다. 실전 연습을 수행해 보세요.|[시작](../profiling/getting-started-with-performance-tools.md)|  
|**프로파일링 세션 구성:** 프로파일링할 프로젝트 또는 이진 파일을 지정하고, 프로파일링 방법을 선택하고, 수집할 성능 데이터를 선택하고, 기타 프로파일링 세션 옵션을 설정하는 고급 방법을 알아봅니다.|[성능 세션 구성](../profiling/configuring-performance-sessions.md)|  
|**프로파일러가 수집하는 데이터 제어:** 성능 세션 속성 및 대화형 절차를 사용하여 프로파일링을 시작 및 중지하는 방법, 원하는 정보만 수집하는 성능 데이터를 제한하는 방법을 알아봅니다.|[데이터 수집 제어](../profiling/controlling-data-collection.md)|  
|**성능 문제 찾기:** 프로파일링 도구 보고서 뷰 창에서 수집된 성능 데이터를 보고 분석하는 방법을 알아봅니다.|[성능 도구 데이터 분석](../profiling/analyzing-performance-tools-data.md)|  
|**성능 변경 분석:** 두 프로파일러 데이터 파일을 비교하여 성능 변경을 분석하는 방법을 알아봅니다.|[성능 데이터 파일 비교](../profiling/comparing-performance-data-files.md)|  
|**결과 저장 및 공유:** 보관 또는 공유를 위해 프로파일링 데이터를 저장하는 방법을 알아봅니다.|[성능 도구 데이터 저장 및 내보내기](../profiling/saving-and-exporting-performance-tools-data.md)|  
|**프로파일링 자동화:** 명령 프롬프트에서 프로파일링 도구를 사용하는 방법을 알아봅니다.|[명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)|  
|**프로그래밍 방식으로 프로파일링 제어:** 관리 및 네이티브 프로파일링 도구 API를 사용하여 소스 코드에서 직접 데이터 컬렉션을 제어하는 방법을 알아봅니다.|[프로파일링 도구 API](../profiling/profiling-tools-apis.md)|  
|**프로파일링 문제 해결**|[성능 도구 문제 해결](../profiling/troubleshooting-performance-tools-issues.md)|  
  
## <a name="see-also"></a>관련 항목  
 [프로파일링 도구](../profiling/profiling-tools.md)

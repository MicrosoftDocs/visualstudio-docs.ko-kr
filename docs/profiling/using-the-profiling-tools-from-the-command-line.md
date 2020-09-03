---
title: 명령줄에서 프로파일링 도구 사용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dea893340c038909057dd652472c10c8264786a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85328342"
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>명령줄에서 프로파일링 도구 사용
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구의 명령줄 도구를 사용하면 명령 프롬프트에서 애플리케이션을 프로파일링하고 배치 파일 및 스크립팅을 통해 프로파일링을 자동화할 수 있습니다. 또한 명령 프롬프트에서 보고서 파일을 생성할 수 있습니다. 간단한 독립 실행형 프로파일러를 사용하여 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]가 설치되어 있지 않은 컴퓨터에서 데이터를 수집할 수 있습니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

## <a name="common-tasks"></a>일반 작업

| Task | 관련 내용 |
| - | - |
| **기호 위치 설정:** 함수 및 매개 변수의 이름을 표시하려면 프로파일러가 프로파일링된 이진 파일의 기호(.*pdb*) 파일에 액세스할 수 있어야 합니다. 이러한 파일은 분석에서 확인하려는 Microsoft 운영 체제 및 애플리케이션의 기호 파일을 포함해야 합니다. 공용 Microsoft 기호 서버를 통해 올바른 Microsoft 이진 파일용 .*pdb* 파일이 있는지 확인할 수 있습니다. | -   [방법: 명령줄에서 기호 파일 위치 지정](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md) |
| **애플리케이션 프로파일링:** 대상 애플리케이션을 프로파일링하는 데 사용하는 명령줄 도구 및 옵션은 애플리케이션의 유형, 프로파일링 방법 및 대상이 관리되는 애플리케이션인지 아니면 기본 애플리케이션인지에 따라 달라집니다. | -   [명령줄에서 프로파일링 방법 사용](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [서비스 프로파일링](../profiling/command-line-profiling-of-services.md) |
| **.xml 및.csv 보고서 만들기:** 명령 프롬프트에서 프로파일링을 수행하면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 인터페이스에서 볼 수 있는 데이터 파일이 만들어집니다. VSPerfReport 명령줄 도구를 사용하여 데이터의 .*xml* 또는 .*csv*(쉼표로 구분된 값) 파일을 생성할 수도 있습니다. | -   [명령줄에서 프로파일러 보고서 만들기](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md) |
| **Visual Studio가 없는 컴퓨터에서 코드 프로파일링:** 프로파일링 도구의 독립 실행형 프로파일러를 사용하여 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]가 설치되어 있지 않은 컴퓨터에서 애플리케이션의 데이터를 수집할 수 있습니다. | -   [방법: 독립 실행형 프로파일러 설치](../profiling/how-to-install-the-stand-alone-profiler.md) |

## <a name="reference"></a>참조
- [명령줄 프로파일링 도구 참조](../profiling/command-line-profiling-tools-reference.md)

## <a name="see-also"></a>참고 항목
- [성능 탐색기](../profiling/performance-explorer.md)

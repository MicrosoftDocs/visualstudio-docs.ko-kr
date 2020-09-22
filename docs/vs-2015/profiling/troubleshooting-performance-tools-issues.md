---
title: 성능 도구 문제 해결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: troubleshooting
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 575f17c641eb057dc01fb3302098bd9f8b47f9c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841946"
---
# <a name="troubleshooting-performance-tools-issues"></a>성능 도구 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로파일링 도구를 사용할 때는 다음 문제 중 하나가 발생할 수 있습니다.  
  
- [프로파일링 도구에서 데이터를 수집 하지 않습니다.](#NoDataCollected)  
  
- [성능 보기 및 보고서 함수 이름에 대 한 숫자 표시](#NoSymbols)  
  
## <a name="no-data-is-collected-by-the-profiling-tools"></a><a name="NoDataCollected"></a> 프로파일링 도구에서 데이터를 수집 하지 않습니다.  
 애플리케이션을 프로파일링한 후에 프로파일링 데이터(.vsp) 파일이 생성되지 않으며 출력 창이나 명령 창에 다음 경고가 표시됩니다.  
  
 PRF0025: 수집한 데이터가 없습니다.  
  
 이 문제는 여러 가지 원인으로 인해 발생할 수 있습니다.  
  
- 샘플링 또는 .NET 메모리 방법을 사용하여 프로파일링된 프로세스가 자식 프로세서를 시작했으며, 자식 프로세스가 애플리케이션 작업을 수행하는 프로세스가 되었습니다. 예를 들어 일부 애플리케이션은 명령줄을 읽어 Windows 애플리케이션으로 시작되었는지 아니면 명령줄 애플리케이션으로 시작되었는지를 확인합니다. Windows 애플리케이션이 요청된 경우 원래 프로세스는 Windows 애플리케이션으로 구성된 새 프로세스를 시작하며 원래 프로세스는 종료됩니다. 프로파일링 도구는 자식 프로세스에 대한 데이터를 자동으로 수집하지 않으므로 데이터는 수집되지 않습니다.  
  
     이러한 상황에서 프로파일링 데이터를 수집하려면 애플리케이션을 프로파일러와 함께 시작하는 대신 자식 프로세스에 프로파일러를 연결합니다. 자세한 내용은 [방법: 실행 중인 프로세스에 성능 도구 연결 및 분리](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) 및 [연결 (VSPerfCmd)](../profiling/attach.md) 을 참조 하세요.  
  
## <a name="performance-views-and-reports-display-numbers-for-function-names"></a><a name="NoSymbols"></a> 성능 보기 및 보고서 함수 이름에 대 한 숫자 표시  
 애플리케이션을 프로파일링한 후에 보고서와 뷰에 함수 이름이 아닌 숫자가 표시됩니다.  
  
 이 문제는 프로파일링 도구 분석 엔진이 함수 이름 및 줄 번호 등의 소스 코드 정보를 컴파일된 파일에 매핑하는 기호 정보가 포함된 .pdb 파일을 읽을 수 없는 경우에 발생합니다. 기본적으로 컴파일러는 애플리케이션 파일을 빌드할 때 .pdb 파일을 만듭니다. .pdb 파일의 로컬 디렉터리에 대한 참조는 컴파일된 애플리케이션에 저장됩니다. 분석 엔진은 참조된 디렉터리에서 .pdb 파일을 찾은 다음 현재 애플리케이션 파일이 포함된 파일에서 .pdb 파일을 찾습니다. .pdb 파일이 없는 경우 분석 엔진은 함수 이름 대신 함수 오프셋을 사용합니다.  
  
 두 가지 방법 중 하나로 문제를 해결할 수 있습니다.  
  
- .pdb 파일을 찾아 애플리케이션 파일과 같은 디렉터리에 저장합니다.  
  
- 프로파일링 데이터(.vsp) 파일에 기호 정보를 포함합니다. 자세한 내용은 [성능 데이터 파일을 사용하여 기호 정보 저장](../profiling/saving-symbol-information-with-performance-data-files.md)을 참조하세요.  
  
> [!NOTE]
> 분석 엔진이 정상적으로 작동하려면 .pdb 파일의 버전이 컴파일된 애플리케이션과 같아야 합니다. 이전 또는 이후 애플리케이션 파일 빌드의 .pdb 파일은 사용할 수 없습니다.

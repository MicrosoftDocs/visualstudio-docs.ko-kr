---
title: '방법: 추가 계측 옵션 지정 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4bc6eeb208ab6d80168431f110f0f6169abbc82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841578"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>방법: 추가 계측 옵션 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE(통합 개발 환경) 내에서 또는 명령줄 도구를 사용하여 이진을 계측할 수 있습니다. IDE 내에서 이진 파일을 계측할 경우 [VSInstr](../profiling/vsinstr.md) 도구에 대한 추가적인 계측 옵션을 지정하여 계측 중에 수집된 데이터 볼륨을 제어할 수 있습니다. 이러한 옵션은 세션 또는 대상 수준에서 사용할 수 있습니다. 예를 들어 계측 프로세스 중에 특정 함수를 포함하거나 제외하려면 대상 수준에서 추가적인 계측 옵션을 사용합니다.  
  
 **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> 삽입된 모든 프로브는 원래 프로그램의 동작을 약간 수정합니다. 이 수정으로 인해 분석 시 오버헤드가 발생합니다. 이 오버헤드의 근사치를 빼더라도 다중 스레드 애플리케이션의 타이밍에 약간의 영향을 미칩니다. [VSInstr](../profiling/vsinstr.md) 도구 옵션을 통해 프로파일링 중에 데이터 수집을 제어할 수 있습니다.  
  
### <a name="to-specify-additional-instrumentation-option"></a>추가적인 계측 옵션을 지정하려면  
  
1. **성능 탐색기**에서 **성능 세션**을 선택한 다음 마우스 오른쪽 단추를 클릭하고 **속성**을 클릭합니다.  
  
2. **속성 페이지**에서 **고급** 속성을 클릭합니다.  
  
3. **추가 계측 옵션** 상자에 옵션을 입력합니다.  
  
     예를 들어 /CONTROL:THREAD를 사용하여 프로파일링 수준을 지정합니다. 전체 옵션 목록을 보려면 [VSInstr](../profiling/vsinstr.md)를 참조하세요.  
  
4. **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)   
 [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)

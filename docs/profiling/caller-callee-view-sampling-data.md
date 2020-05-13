---
title: 호출자/호출 수신자 뷰 - 샘플링 데이터 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 008aa6bd9402cde760ffc61a613aba778c8ec96f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773272"
---
# <a name="callercallee-view---sampling-data"></a>호출자/호출 수신자 뷰 - 샘플링 데이터
호출자/호출 수신자 뷰는 선택한 함수와 해당 부모 및 자식 함수에 대한 프로파일링 정보를 표시합니다. 호출자/호출 수신자 뷰에는 세 개의 표가 포함되어 있습니다.

 **현재 함수**는 가운데 표에 표시되며, 선택한 함수에 대한 프로파일링 정보를 보여 줍니다. 값에는 함수에 대한 모든 샘플링 호출이 포함되어 있습니다.

 **현재 함수를 호출한 함수**는 위쪽 표에 표시되며, 선택(현재) 함수의 값에 대한 호출자(부모) 함수의 개별 기여를 보여 줍니다.

 **현재 함수에서 호출된 함수**는 아래쪽 표에 표시되며, 현재 함수가 자식 함수를 호출한 경우 선택한 함수의 호출 수신자(자식) 함수에 대한 프로파일링 정보를 보여 줍니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

|열|Description|
|------------|-----------------|
|**프로세스 ID**|프로파일링 실행의 PID(프로세스 ID)입니다.|
|**프로세스 이름**|프로세스의 이름입니다.|
|**모듈 이름**|함수가 포함된 모듈의 이름입니다.|
|**모듈 경로**|함수가 포함된 모듈의 경로입니다.|
|**원본 파일**|이 함수의 정의가 포함된 소스 파일입니다.|
|**함수 이름**|함수의 정규화된 이름입니다.|
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|
|**함수 주소**|함수의 주소입니다.|
|**형식**|함수의 컨텍스트:<br /><br /> -   **0** - 현재 함수<br />-   **1** - 현재 함수를 호출하는 함수<br />-   **2** - 현재 함수가 호출하는 함수|
|**루트 함수 이름**|현재 함수의 이름입니다.|
|**포괄 샘플**|- 현재 함수의 경우 해당 함수 또는 자식 함수 중 하나가 실행되고 있긴 하지만 수집된 샘플 수입니다.<br />- 호출자 함수의 경우 이 함수가 현재 함수를 호출했을 때 수집된 현재 함수의 포괄 샘플 수입니다.<br />- 호출 수신자 함수의 경우 현재 함수가 이 함수를 호출했을 때 수집된 이 함수의 포괄 샘플 수입니다.|
|**포괄 샘플 비율(%)**|프로파일링 실행 시, 이 함수의 포괄 샘플이었던 모든 샘플의 비율입니다.|
|**전용 샘플**|- 현재 함수의 경우 이 함수가 직접 실행되고 있을 때(즉, 이 함수가 호출 스택의 맨 위에 있을 때) 수집된, 프로파일링 실행 시 샘플 수입니다. 이 함수의 자식 함수가 실행될 때 수집된 샘플은 전용 개수에 포함되지 않습니다.<br />- 호출자 함수의 경우 이 함수가 현재 함수를 호출했을 때 수집된 현재 함수의 전용 샘플 수입니다.<br />- 호출 수신자 함수의 경우 현재 함수가 이 함수를 호출했을 때 수집된 이 함수의 전용 샘플 수입니다.|
|**전용 샘플 비율(%)**|프로파일링 실행 시, 이 함수의 전용 샘플이었던 모든 샘플의 비율입니다.|

## <a name="see-also"></a>참고 항목
- [호출자/호출 수신자 뷰 - .NET 메모리 샘플링 데이터](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [호출자/호출 수신자 뷰 - .NET 메모리 계측 데이터](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [호출자/호출 수신자 뷰 - 계측 데이터](../profiling/caller-callee-view-instrumentation-data.md)

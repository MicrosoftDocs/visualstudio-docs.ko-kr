---
title: 모듈 뷰 - 샘플링 데이터 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7ead219ddf482af5917842118d386c6fefe67973
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772716"
---
# <a name="modules-view---sampling-data"></a>모듈 뷰 - 샘플링 데이터
샘플링 데이터의 모듈 뷰에는 프로파일링 데이터에서 샘플링된 모듈별로 그룹화된 성능 데이터가 표시됩니다. 각 모듈은 계층 트리의 루트입니다. 모듈의 샘플링된 함수는 모듈 노드 아래에 나열됩니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

 샘플을 수집할 때 함수가 실행 중이었다면, 즉 함수가 호출 스택 맨 위에 있었다면 실행 중이었던 소스 줄 및 명령 주소가 함수 노드 아래에 나열됩니다. 소스 줄이나 명령을 실행할 때는 해당 줄 또는 명령 포인터에 대한 데이터가 수집되므로, 줄 데이터 및 명령 데이터에 대한 포괄 값과 전용 값은 항상 동일합니다.

|열|Description|
|------------|-----------------|
|**이름**|모듈, 함수, 줄 번호 또는 명령 포인터 주소의 이름입니다.|
|**프로세스 ID**|프로파일링 실행의 PID(프로세스 ID)입니다.|
|**프로세스 이름**|프로세스의 이름입니다.|
|**모듈 이름**|함수, 줄 또는 명령 포인터가 포함된 모듈의 이름입니다.|
|**모듈 경로**|모듈, 함수, 줄 또는 명령 포인터가 포함된 모듈의 경로입니다.|
|**원본 파일**|이 함수의 정의가 포함된 소스 파일입니다.|
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|
|**포괄 샘플**|-   함수의 경우 이  함수나 이 함수가 호출한 함수가 실행되었던 샘플의 수(이 함수가 포함된 호출 스택 샘플의 수)입니다.<br />-   모듈의 경우 모듈의 함수가 하나 이상 실행되었던 샘플의 수입니다.<br />-   줄이나 명령의 경우 이 줄이나 명령이 실행되었던 샘플의 수입니다.|
|**포괄 샘플 비율(%)**|-   함수나 모듈의 경우 프로파일링 실행의 모든 샘플 중 이 함수나 모듈의 포괄 샘플이었던 샘플의 백분율입니다.<br />-   줄이나 명령의 경우 프로파일링 실행의 모든 샘플 중 이 줄이나 명령이 실행되었던 샘플의 백분율입니다.|
|**전용 샘플**|-   함수의 경우 이 함수가 직접 실행된 호출 스택 샘플의 수(이 함수가 호출 스택 맨 위에 있었던 샘플의 수)입니다.<br />-   모듈의 경우 모듈 내 함수의 전용 샘플 합입니다.<br />-   줄이나 명령의 경우 이 줄이나 명령이 실행되었던 샘플의 수입니다.|
|**전용 샘플 비율(%)**|-   함수나 모듈의 경우 프로파일링 실행의 모든 샘플 중 이 함수나 모듈의 전용 샘플이었던 샘플의 백분율입니다.<br />-   줄이나 명령의 경우 프로파일링 실행의 모든 샘플 중 이 줄이나 명령이 실행되었던 샘플의 백분율입니다.|

## <a name="see-also"></a>참고 항목
- [모듈 뷰 - 샘플링](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [모듈 뷰 - 계측](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [모듈 뷰](../profiling/modules-view-instrumentation-data.md)

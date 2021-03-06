---
title: 함수 뷰 - 샘플링 데이터 | Microsoft 문서
description: 프로파일링 생성 중에 샘플링된 함수를 나열하는 샘플링 프로필 방법의 함수 보고서 뷰에 관해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 82b48689b6348c7d003f5418224260b7939e907a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907358"
---
# <a name="functions-view---sampling-data"></a>함수 뷰 - 샘플링 데이터
샘플링 프로필 방법의 함수 보고서 뷰는 프로파일링 생성 중에 샘플링된 함수를 나열합니다.

> [!NOTE]
> Windows 8 및 Windows Server 2012의 강화된 보안 기능을 위해 Visual Studio 프로파일러가 이러한 플랫폼에서 데이터를 수집하는 방법을 상당히 변경해야 했습니다. 또한 UWP 앱에는 새로운 수집 기술도 필요합니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요.

|열|설명|
|------------|-----------------|
|**프로세스 ID**|프로파일링 실행의 PID(프로세스 ID)입니다.|
|**프로세스 이름**|프로세스의 이름입니다.|
|**모듈 이름**|함수가 포함된 모듈의 이름입니다.|
|**모듈 경로**|함수가 포함된 모듈의 경로입니다.|
|**원본 파일**|이 함수의 정의가 포함된 소스 파일입니다.|
|**함수 이름**|함수의 정규화된 이름입니다.|
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|
|**함수 주소**|함수의 주소입니다.|
|**포괄 샘플**|이 함수가 실행될 때 수집된 총 샘플 수(즉, 이 함수가 호출 스택에 있을 때 수집된 샘플 수)입니다. 이 수에는 해당 함수에 의해 호출된 함수를 실행할 때 수집된 샘플이 포함됩니다.|
|**포괄 샘플 비율(%)**|프로파일링 실행 시, 이 함수의 포괄 샘플이었던 모든 샘플의 비율입니다.|
|**전용 샘플**|이 함수 본문의 코드가 실행될 때(즉, 이 함수가 호출 스택의 맨 위에 있을 때) 수집된 총 샘플 수입니다. 해당 함수가 호출한 함수에서 수집된 샘플은 포함되지 않습니다.|
|**전용 샘플 비율(%)**|프로파일링 실행 시, 이 함수의 전용 샘플이었던 모든 샘플의 비율입니다.|

## <a name="see-also"></a>참고 항목
- [방법: 보고서 보기 열 사용자 지정](../profiling/how-to-customize-report-view-columns.md)
- [함수 뷰 - 계측](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [함수 뷰 - 샘플링](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [함수 뷰](../profiling/functions-view-instrumentation-data.md)

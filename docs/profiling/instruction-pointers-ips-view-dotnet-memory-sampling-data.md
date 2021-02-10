---
title: IP(명령 포인터) 뷰 - .NET 메모리 샘플링 데이터
description: 샘플링 방법을 사용하여 수집된 .NET 메모리 할당 프로파일링 데이터의 IP 뷰는 메모리를 할당한 어셈블리 명령을 나열합니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 51f7c9faee3b93a11b3a2a304654005c80b8ad87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906837"
---
# <a name="instruction-pointers-ips-view---net-memory-sampling-data"></a>IP(명령 포인터) 뷰 - .NET 메모리 샘플링 데이터
샘플링 방법을 사용하여 수집된 .NET 메모리 할당 프로파일링 데이터에 대한 IP 뷰는 프로파일링 실행 중 메모리를 할당한 어셈블리 명령을 나열합니다. 뷰의 열은 할당의 크기와 할당 수도 나열합니다.

 전용 값만 나열됩니다.

|열|설명|
|------------|-----------------|
|**프로세스 ID**|프로파일링 실행의 PID(프로세스 ID)입니다.|
|**프로세스 이름**|프로세스의 이름입니다.|
|**모듈 이름**|명령이 포함된 모듈의 이름입니다.|
|**모듈 경로**|명령이 포함된 모듈의 경로입니다.|
|**원본 파일**|명령이 포함된 소스 파일입니다.|
|**함수 이름**|함수의 이름입니다.|
|**함수 줄 번호**|소스 파일에서 이 함수가 시작되는 줄 번호입니다.|
|**함수 주소**|함수의 시작 주소입니다.|
|**소스 줄 시작**|할당이 발생한 소스 파일의 시작 줄 번호입니다.|
|**소스 줄 끝**|할당이 발생한 소스 파일의 끝 줄 번호입니다.|
|**소스 문자 시작**|소스 파일 줄에서 할당이 발생한 시작 문자의 오프셋입니다.|
|**소스 문자 끝**|소스 파일 줄에서 할당이 발생한 끝 문자의 오프셋입니다.|
|**명령 주소**|명령의 주소입니다.|
|**제외 할당**|명령에서 생성된 개체의 총 수입니다.|
|**제외 할당 비율(%)**|명령에서 할당되고 프로파일링 실행 시에 생성된 모든 개체의 백분율입니다.|
|**제외 바이트**|명령에서 할당되고 프로파일링 실행 시에 할당된 메모리의 바이트 수입니다.|
|**제외 바이트(%)**|명령에서 할당되고 프로파일링 실행 시에 할당된 모든 메모리 바이트의 백분율입니다.|

## <a name="see-also"></a>참고 항목
- [IP(명령 포인터) 뷰](../profiling/instruction-pointers-ips-view-sampling-data.md)

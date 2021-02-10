---
title: 현재 탭 | Microsoft 문서
description: 스레드 뷰의 현재 탭을 선택하여 CPU 스레드 세그먼트 또는 차단 세그먼트에 대한 호출 스택을 확인합니다. DirectX 세그먼트에 관한 정보도 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4125a40ea0be18cceb99e7f3a8118a10d26a5437
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955868"
---
# <a name="current-tab"></a>현재 탭
**현재** 탭을 클릭하면 CPU 스레드 세그먼트가 선택된 경우 타임라인에서 현재 선택 지점과 가장 가까운 호출 스택(사용 가능한 경우)을 볼 수 있습니다.  이 경우, 선택 지점은 타임라인 위에 검은색 화살표 또는 캐럿으로 표시됩니다. 차단 세그먼트가 선택되어 있으면 이 세그먼트에는 실행 항목이 없었으므로 캐럿이 표시되지 않습니다. 하지만 세그먼트가 여전히 강조 표시되어 있고 호출 스택이 표시됩니다.

 또한 **현재** 탭에는 DirectX 작업 세그먼트, 표식 및 I/O 액세스에 대한 정보가 표시됩니다.  DirectX 작업 세그먼트의 경우 DMA 패킷이 하드웨어 큐에서 처리되는 방법에 대한 자세한 내용이 표시됩니다.  표식의 경우, 설명 및 표식 유형에 대한 정보가 표시됩니다.  I/O 액세스의 경우 파일 및 읽거나 쓴 바이트 수에 대한 정보가 표시됩니다.

## <a name="see-also"></a>참조
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)
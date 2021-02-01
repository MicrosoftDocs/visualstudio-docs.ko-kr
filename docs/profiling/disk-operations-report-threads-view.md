---
title: 디스크 작업 보고서(스레드 뷰) | Microsoft 문서
description: 디스크 작업 보고서에는 디스크 채널의 디스크 I/O 작업이 표시됩니다. 각 디스크 액세스에 대해 보고되는 정보를 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.diskoperations
helpviewer_keywords:
- Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44975999c71b1c331d90aa10f709071cef466cb1
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686534"
---
# <a name="disk-operations-report-threads-view"></a>디스크 작업 보고서(스레드 뷰)
디스크 작업 보고서에는 디스크 채널의 디스크 I/O 작업이 표시됩니다.

 현재 표시되는 기간에 프로파일링 중인 프로세스를 대신해서 발생하는 각 디스크 액세스에 대해서는 다음 정보가 보고됩니다.

- 디스크 액세스를 수행한 프로세스의 이름 및 PID

- 디스크에 액세스한 스레드의 ID

- 액세스된 파일의 이름

- 파일당 읽기 횟수

- 읽은 바이트 수

- 읽기 대기 시간(밀리초)

- 쓰기 횟수

- 기록한 바이트 수

- 쓰기 대기 시간(밀리초)

## <a name="see-also"></a>참조
- [스레드 뷰](../profiling/threads-view-parallel-performance.md)
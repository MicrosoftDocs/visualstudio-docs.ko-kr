---
title: 명령줄에서 보고서 필터링 | Microsoft Docs
description: VSPerfReport.exe를 사용하여 보고를 특정 기간 또는 선택한 프로세스 및 스레드로 제한합니다. 이 문서에는 옵션과 설명이 나와 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6e9b140f-b44f-4a5c-bd65-d868ddc94023
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dda6b89dcdfacc286417924c666b3ebd805f1cc0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897715"
---
# <a name="how-to-filter-reports-from-the-command-line"></a>방법: 명령줄에서 보고서 필터링
**VSPerfReport** 명령에 대한 옵션을 사용하여 프로파일링 데이터 파일의 특정 시간 세그먼트에 대한 보고서를 필터링하거나 데이터를 하나 이상의 프로세스 또는 스레드로 제한할 수 있습니다. 이 명령에 대한 자세한 내용은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요.

|옵션|설명|
|-------------|-----------------|
|**StartTime:** [*Value*]|value 이후에 수집된 데이터만 표시합니다(밀리초).|
|**EndTime:** [*Value*]|value 이전에 수집된 데이터만 표시합니다(밀리초).|
|**FilterFile:** `VSPFFile`|**Visual Studio 성능 보고서** 창에서 생성된 필터 파일의 위치를 지정합니다.|
|**MsFilter:** [*StartTime,Duration*]|`StartTime`부터 `Duration` 길이(밀리초)까지의 데이터만 표시합니다.|
|**Process:** [*Pid*]|지정한 프로세스의 데이터만 표시합니다.|
|**Thread:** [*ThreadID*]|지정한 스레드의 데이터만 표시합니다.|
|**Thread:** [*ThreadID,ProcessID*]|지정한 프로세스와 관련된 특정 스레드의 데이터만 표시합니다.|

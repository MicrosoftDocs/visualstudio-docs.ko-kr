---
title: 파일 추적 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9335ca6608d36edbd17e47a441e13aecaa41c890
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634203"
---
# <a name="file-tracking"></a>파일 추적

파일 추적은 프로세스 및 해당 자식 프로세스에 Windows 파일 시스템에 대한 호출을 기록합니다. 프로그램은 아래에 나열된 함수를 호출하여 이 로깅 기능을 켜고 끄는 시점을 제어하고 사용할 로그 파일을 지정합니다.

- [EndTrackingContext](../msbuild/endtrackingcontext.md) 현재 컨텍스트의 추적을 중지합니다.

- [ResumeTracking](../msbuild/resumetracking.md)[SuspendTracking](../msbuild/suspendtracking.md)을 호출한 후에 추적을 다시 시작합니다.

- [SetThreadCount](../msbuild/setthreadcount.md) 추적에 사용할 스레드 수를 설정합니다.

- [StartTrackingContext](../msbuild/starttrackingcontext.md) 새 추적 컨텍스트를 시작합니다.

- [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md) 지정된 루트를 사용하여 새 추적 컨텍스트를 시작합니다.

- [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md) 사용되는 추적 및 릴리스 리소스를 종료합니다.

- [SuspendTracking](../msbuild/suspendtracking.md) 추적을 일시적으로 중단합니다.

- [WriteAllTLogs](../msbuild/writealltlogs.md) 모든 컨텍스트에 대한 추적 로그를 작성합니다.

- [WriteContextTLogs](../msbuild/writecontexttlogs.md) 현재 컨텍스트에 대한 추적 로그를 작성합니다.

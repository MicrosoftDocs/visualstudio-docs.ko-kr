---
title: ETW(Windows용 이벤트 추적) 보고서 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 19412d184377637c29f34b2fe3ffd033f176b97c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779300"
---
# <a name="event-tracing-for-windows-etw-report"></a>ETW(Windows용 이벤트 추적) 보고서
ETW(Windows용 이벤트 추적) 보고서에는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구의 성능 세션에서 기록된 ETW 이벤트가 나열됩니다. ETW 데이터는 이진(.*etl*) 파일에 수집됩니다.

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 인터페이스에는 ETW 보고서를 표시할 수 없습니다.

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 인터페이스에서 프로파일링 도구를 사용하여 ETW 데이터를 수집하는 방법에 대한 자세한 내용은 [방법: ETW(Windows용 이벤트 추적) 데이터 수집](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)을 참조하세요.

- [VSPerfCmd](../profiling/vsperfcmd.md) 명령줄 도구를 사용하여 ETW 데이터를 수집하는 방법에 대한 자세한 내용은 [이벤트](../profiling/events-vsperfcmd.md)를 참조하세요.

- **VSReport/Summary:ETW** 명령을 사용하여 ETW 보고서를 생성합니다. 자세한 내용은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요.

|열|Description|
|------------|-----------------|
|**Timestamp**|이벤트가 발생한 시기를 식별합니다.|
|**프로세스 ID**|이벤트를 생성한 프로세스를 식별합니다.|
|**스레드 ID**|이벤트를 생성한 스레드를 식별합니다.|
|**설명**|이벤트 공급자를 식별합니다.|
|**형식**|이벤트 유형을 식별합니다.|
|**속성**|이벤트의 속성입니다. 각 이벤트는 쉼표로 구분되며, 대괄호로 묶인 이름 값 쌍입니다.|

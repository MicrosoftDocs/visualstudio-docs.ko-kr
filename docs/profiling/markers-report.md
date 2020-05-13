---
title: 표식 보고서 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.markers
ms.assetid: 829ce099-172e-4c7e-bbd0-578b110c59bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9502d2cf0081985cfbee2283af820c06d681ad9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "64808256"
---
# <a name="markers-report"></a>표식 보고서
표식 보고서에는 표시된 기간 중의 표식이 나열됩니다.  이동이나 확대/축소 또는 레인 숨기기에 따라 표식이 나타나거나 사라질 수 있습니다. 보고서에는 각 표식에 대해 다음 정보가 포함됩니다.

- 추적 시작을 기준으로 시작된 시간입니다.

- 해당 기간입니다. 플래그 및 메시지는 인스턴트 항목이므로 기간이 0입니다.

- 표식을 생성한 스레드의 ID입니다.

- 표식을 생성한 ETW(Windows용 이벤트 추적) 공급자입니다.

- 표식이 작성된 표식 계열입니다.

- 표식이 속하는 이벤트 범주입니다.

- 중요도 수준입니다.

- 해당 형식(범위, 플래그 또는 메시지)입니다.

- 표식이 나타내는 항목에 대한 고급 설명입니다.

  표식 보고서를 CSV 파일로 저장하려면 **내보내기** 단추를 선택합니다. CSV 파일의 데이터는 다른 응용 프로그램 또는 도구에서 사용할 수 있습니다.

> [!NOTE]
> 표식 보고서는 1,000개의 표식을 표시할 수 있습니다. 모든 표식을 보려면 전체 보고서를 CSV 파일로 내보냅니다.
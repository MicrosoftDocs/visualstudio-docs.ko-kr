---
title: 최근 작업 보기
description: 작업을 제출하면 작업 목록을 보고 해당 상태, 기간 등을 확인할 수 있습니다.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 13d78913e0d5d708c5e75a80611ae9cc1c2f7366
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841434"
---
# <a name="view-recent-job-performance-and-details"></a>최근 작업 성능 및 세부 정보 보기

작업을 제출하면 작업 목록을 보고 해당 상태, 기간 등을 확인할 수 있습니다.

1. **서버 탐색기** 에서 특정 컴퓨팅 컨텍스트를 확장합니다.
2. **작업** 을 두 번 클릭합니다.
3. 해당 컴퓨팅 컨텍스트에 제출된 작업 목록을 확인합니다.
4. 목록에서 특정 **작업** 을 선택하여 세부 정보를 봅니다.

![monitor jobs](media/job-details/monitor-jobs.png)

> Linux VM으로 제출된 작업 기록은 /tmp 디렉터리의 VM에 저장됩니다. 그러므로 다시 부팅될 때마다 작업 기록이 정리됩니다. 작업 기록의 영구 레코드의 경우 Azure Machine Learning에서 VM을 컴퓨팅 컨텍스트로 구성하고 VM을 컴퓨팅 컨텍스트로 선택하여 작업을 Azure Machine Learning으로 제출합니다.

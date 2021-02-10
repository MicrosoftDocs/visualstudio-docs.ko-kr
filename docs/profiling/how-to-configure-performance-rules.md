---
title: 성능 규칙 구성 | Microsoft Docs
description: Visual Studio 프로파일링 도구에서 발생하는 경고에 유의합니다. 해당 경고는 수집 방법을 개선하는 데 도움이 될 수 있습니다. 해당 경고는 오류 목록 창에서 찾을 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.ruleseditor
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0a9e28b0e1c3e82cb9416a376603e8f4a560f02c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948142"
---
# <a name="how-to-configure-performance-rules"></a>방법: 성능 규칙 구성
Visual Studio 프로파일링 도구의 성능 경고는 프로파일링된 애플리케이션에서 프로그램 실행 속도를 저하할 수 있는 문제를 나타냅니다. 또한 경고는 보다 유용한 데이터를 수집하기 위해 수집 방법을 변경해야 할 수 있음을 나타낼 수도 있습니다. 성능 경고는 프로파일링 세션에서 자동으로 생성되며 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]에서 프로파일링 데이터 파일을 열 때 **오류 목록** 창에 표시됩니다. 특정 경고가 관심 있는 시나리오에 적용되지 않을 수도 있고 일부 경고가 부정확하게 발생할 수도 있습니다. 특정 경고를 표시하거나 숨기도록 성능 경고를 구성할 수 있습니다.

### <a name="to-configure-profiler-performance-warnings"></a>프로파일러 성능 경고를 구성하려면

1. **도구** 메뉴에서 **옵션** 을 클릭합니다.

2. **성능 도구** 를 확장하고 **규칙** 을 클릭합니다.

3. 경고를 사용하거나 사용하지 않도록 설정하려면 경고 **ID** 및 이름 옆의 확인란을 선택하거나 선택 취소합니다.

4. 규칙의 경고 수준을 지정하려면 규칙 옆의 **작업** 셀을 클릭하고 경고 수준을 클릭합니다.

    - **사용 안 함** - 규칙을 사용하지 않도록 설정합니다(규칙 ID 옆의 확인란을 선택 취소하는 것과 같음).

    - **경고** - 규칙을 경고로 표시합니다.

    - **오류** - 프로파일링 실행을 정지하고 규칙을 오류로 표시합니다.

    - **정보** - 규칙을 정보 제공용으로만 표시합니다.

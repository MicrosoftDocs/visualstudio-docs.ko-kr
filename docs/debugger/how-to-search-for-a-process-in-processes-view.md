---
title: 프로세스 뷰에서 프로세스 검색 | Microsoft Docs
description: Visual Studio에서 디버그할 때 프로세스 ID 또는 모듈 문자열을 검색 조건으로 사용하여 Spy++ 도구의 프로세스 뷰에서 특정 프로세스를 검색합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 85b2c2bab29316846620c7dbec935b41eec1d9df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99845076"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>방법: 프로세스 뷰에서 프로세스 검색
프로세스 뷰에서 프로세스 ID 또는 모듈 문자열을 검색 조건으로 사용하여 특정 프로세스를 검색할 수 있습니다. 검색의 초기 방향을 지정할 수도 있습니다. 대화 상자의 필드에는 프로세스 트리에서 선택한 프로세스의 특성이 표시됩니다.

### <a name="to-search-for-a-process-in-processes-view"></a>프로세스 뷰에서 프로세스를 검색하려면

1. Spy++와 활성 [프로세스 뷰](../debugger/processes-view.md) 창이 보이도록 창을 정렬합니다.

2. **검색** 메뉴에서 **프로세스 찾기** 를 선택합니다.

    [프로세스 검색 대화 상자](../debugger/process-search-dialog-box.md)가 열립니다.

3. 검색 조건으로 프로세스 ID나 모듈 문자열을 입력합니다.

4. 값을 지정하지 않을 필드의 선택을 취소합니다.

   > [!TIP]
   > 모듈이 소유한 모든 프로세스를 찾으려면 **프로세스** 상자의 선택을 취소하고 **모듈** 상자에 모듈 이름을 입력합니다. 그리고 **다음 찾기** 를 사용하여 계속해서 프로세스를 검색합니다.

5. 검색의 초기 방향으로 **위로** 또는 **아래로** 를 선택합니다.

6. **확인** 을 클릭합니다.

   일치하는 프로세스가 검색되면 **프로세스 뷰** 창에 강조 표시됩니다.
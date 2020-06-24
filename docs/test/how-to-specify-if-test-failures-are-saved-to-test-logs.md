---
title: 테스트 실패에 대한 부하 테스트 로그 저장
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaef2888cecc7622a3dc589a6bab816b0c134668
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287508"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>방법: 부하 테스트 편집기를 사용하여 테스트 실패를 테스트 로그에 저장할지 여부 지정

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 부하 테스트 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다. [연습: 부하 테스트 생성 및 실행](../test/walkthrough-create-and-run-a-load-test.md)을 참조합니다. **테스트 실패 시 로그 저장** 속성을 변경하여 부하 테스트에서 테스트가 실패할 경우 테스트 로그가 저장되도록 할 것인지 여부를 지정할 수 있습니다.

> [!NOTE]
> 실행 설정 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)을 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>시나리오에서 테스트가 실패할 때 테스트 로그가 저장되는지 여부를 지정하려면

1. 부하 테스트를 엽니다.

     **부하 테스트 편집기**가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리 **실행 설정** 폴더에서 최대 테스트 반복 횟수를 지정할 실행 설정 노드를 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택합니다.

     실행 설정 범주와 속성이 **속성** 창에 표시됩니다.

4. **테스트 실패 시 로그 저장** 속성에서 **True** 또는 **False**를 선택하여 시나리오에서 테스트가 실패할 경우 테스트 로그를 저장할 것인지 여부를 지정합니다.

     속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다.

     로그에 저장된 데이터는 부하 테스트 분석기의 테이블 뷰를 사용하여 볼 수 있습니다. 자세한 내용은 [테이블 뷰에서 부하 테스트 결과 및 오류 분석](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [부하 테스트 시나리오 편집](../test/edit-load-test-scenarios.md)
- [연습: 부하 테스트 생성 및 실행](../test/walkthrough-create-and-run-a-load-test.md)

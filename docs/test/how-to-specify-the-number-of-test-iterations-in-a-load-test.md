---
title: 부하 테스트 실행 설정에서 테스트 반복 횟수 지정
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b022c747235f131f530df62e49c7204a97ce0872
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287482"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>방법: 부하 테스트 실행 설정에서 테스트 반복 횟수 지정

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 시나리오 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다. 자세한 내용은 [연습: 부하 테스트 만들기 및 실행](../test/walkthrough-create-and-run-a-load-test.md)을 참조하세요.

**부하 테스트 편집기**를 사용하여 **속성** 창에서 실행 설정 값의 **테스트 반복** 속성을 편집할 수 있습니다. **부하 테스트 편집기**의 **테스트 반복** 속성은 부하 테스트의 모든 시나리오에 포함된 모든 웹 성능 및 단위 테스트를 실행할 반복 횟수를 지정합니다.

> [!NOTE]
> 실행 설정 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)을 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>실행 설정의 테스트 반복 횟수를 지정하려면

1. 부하 테스트를 엽니다.

     **부하 테스트 편집기**가 나타나고 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리의 **실행 설정** 폴더에서 실행 설정을 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택하여 부하 실행 설정의 범주와 속성을 확인합니다.

4. **테스트 반복 사용** 속성을 **True**로 설정합니다.

5. **테스트 반복** 속성에서 부하 테스트 중 실행할 테스트 반복 횟수를 나타내는 숫자를 입력합니다.

6. 속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 **테스트 반복** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)
- [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)

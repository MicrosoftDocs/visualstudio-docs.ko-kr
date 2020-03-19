---
title: '방법: 부하 테스트 실행 설정에 대한 샘플링 주기 지정'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63b6b9479347b076b7bd9e350e80e4bfa2a36d69
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594827"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>방법: 부하 테스트 실행 설정에 대한 샘플 속도 지정

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**부하 테스트 편집기**를 사용하여 **속성** 창에서 실행 설정의 **샘플링 주기** 속성 값을 편집할 수 있습니다. 실행 설정 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)을 참조하세요.

부하 테스트 실행 설정에서 부하 테스트 길이에 따라 적절한 **샘플링 주기** 속성 값을 선택합니다. 기본값인 5초와 같이 샘플링 주기 값이 작으면 부하 테스트 결과 데이터베이스에 더 많은 공간이 필요합니다. 부하 테스트가 긴 경우 샘플링 주기를 늘리면 수집되는 데이터 양이 줄어듭니다. 자세한 내용은 [방법: 부하 테스트 실행 설정에 대한 샘플 속도 지정](../test/how-to-specify-the-sample-rate-for-a-load-test.md)을 참조하세요.

다음은 샘플링 주기에 대한 몇 가지 지침입니다.

|부하 테스트 지속 시간|권장 샘플링 주기|
|-|-----------------------------|
|\< 1시간|5초|
|1-8시간|15초|
|8-24시간|30초|
|24시간 초과|60초|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>실행 설정에서 성능 카운터 샘플링 주기를 지정하려면

1. 부하 테스트를 엽니다.

     **부하 테스트 편집기**가 나타납니다. 부하 테스트 트리가 표시됩니다.

2. 부하 테스트 트리의 **실행 설정** 폴더에서 샘플링 주기를 지정할 실행 설정을 선택합니다.

3. **보기** 메뉴에서 **속성 창**을 선택합니다.

     부하 실행 설정의 범주와 속성이 **속성** 창에 표시됩니다.

4. **샘플링 주기** 속성에 부하 테스트 시 성능 카운터 데이터를 수집할 빈도를 나타내는 시간 값을 입력합니다.

5. 속성 변경을 마친 다음, **파일** 메뉴에서 **저장**을 선택합니다. 그러면 새 **샘플링 주기** 값을 사용하여 부하 테스트를 실행할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)
- [부하 테스트 시나리오 속성](../test/load-test-scenario-properties.md)

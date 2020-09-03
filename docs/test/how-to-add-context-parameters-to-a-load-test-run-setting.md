---
title: 부하 테스트 실행 설정에 컨텍스트 매개 변수 추가
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, context parameters
- load tests, context parameters
ms.assetid: a8a0b97e-8040-4711-85ab-36548b130ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 10a410b18391b3fbaee98f10be56cdc70c0f3562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288418"
---
# <a name="how-to-add-context-parameters-to-a-load-test-run-setting"></a>방법: 부하 테스트 실행 설정에 컨텍스트 매개 변수 추가

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 시나리오 속성을 테스트 요구 사항 및 목표에 맞게 변경할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> 실행 설정 속성의 전체 목록과 해당 설명을 보려면 [부하 테스트 실행 설정 속성](../test/load-test-run-settings-properties.md)을 참조하세요.

부하 테스트 편집기를 사용하여 부하 테스트 실행 설정에 사용할 컨텍스트 매개 변수를 만들 수 있습니다. 컨텍스트 매개 변수를 사용하면 문자열을 매개 변수화할 수 있습니다.

예를 들어 부하 테스트에 포함된 웹 성능 테스트에서 이미 컨텍스트 매개 변수를 사용하여 매개 변수가 있는 웹 서버 URL을 사용하고 있다고 가정합니다. 이 경우 웹 성능 테스트에 사용되는 것과 동일한 이름 값을 사용하는 컨텍스트 매개 변수를 부하 테스트 실행 설정에 추가할 수 있습니다. 그러면 부하 테스트를 실행할 때 웹 성능 테스트가 다른 서버에 매핑됩니다. 예를 들어 부하 테스트에 포함된 웹 성능 테스트에서 URL의 웹 서버 이름에 WebServer1이라는 컨텍스트 매개 변수를 사용하는 경우, 부하 테스트 실행 설정에도 WebServer1이라는 컨텍스트 매개 변수를 지정하면 부하 테스트 시 부하 테스트 실행 설정에 할당한 컨텍스트 매개 변수가 사용됩니다. 정리하면, 부하 테스트의 웹 성능 테스트에서 부하 테스트의 컨텍스트 매개 변수와 동일한 컨텍스트 매개 변수 이름을 사용하는 경우, 부하 테스트의 컨텍스트 매개 변수가 웹 성능 테스트에 사용되는 컨텍스트 매개 변수를 재정의합니다.

> [!WARNING]
> 실행 설정에 컨텍스트 매개 변수를 사용하는 경우에는 실수로 웹 성능 테스트의 컨텍스트 매개 변수를 재정의하지 않도록 주의하세요. 필요한 경우가 아니면 동일한 컨텍스트 매개 변수 이름을 사용하지 않는 것이 좋습니다.

`http://CorporateStagingWebServer`에 Webserver1 컨텍스트 매개 변수 값을 할당하면 부하 테스트 전체에 `WebServer1`을 사용할 수 있으며 언제든지 이 값을 다른 웹 서버로 쉽게 변경할 수 있습니다.

또한 다음과 같이 다른 부하 테스트 실행 설정에서 동일한 이름을 사용하는 컨텍스트 매개 변수에 다른 값을 할당하면 부하 테스트를 다른 환경에서 실행할 수 있습니다.

- 회사 스테이징 웹 서버 실행 설정: `WebServer1=http://CorporateStagingWebServer`라는 컨텍스트 매개 변수

- 회사 프로덕션 웹 서버 실행 설정: `WebServer1=http://CorporateProductionWebServer`라는 컨텍스트 매개 변수

  **명령줄에서 실행 설정 변경**

  명령줄에서 다른 실행 설정을 사용하여 컨텍스트 매개 변수 전략을 활용하려면 다음 명령을 사용합니다.

  **Set Test.UseRunSetting= CorporateStagingWebServer**

  및

  **mstest /testcontainer:loadtest1.loadtest**

## <a name="to-add-a-context-parameter-to-a-run-setting"></a>컨텍스트 매개 변수를 실행 설정에 추가하려면

1. 부하 테스트를 엽니다.

2. 부하 테스트 편집기에서 부하 테스트 트리의 **실행 설정** 폴더를 확장합니다.

3. 컨텍스트 매개 변수를 추가할 특정 실행 설정을 마우스 오른쪽 단추로 클릭하고 **컨텍스트 매개 변수 추가**를 선택합니다.

     새 컨텍스트 매개 변수가 부하 테스트 트리의 **실행 설정** 폴더에 있는 **컨텍스트 매개 변수** 폴더에 추가됩니다.

     또는

     실행 설정에 이미 **컨텍스트 매개 변수** 폴더가 있는 경우 이 폴더를 마우스 오른쪽 단추로 클릭하고 **컨텍스트 매개 변수 추가**를 선택합니다.

4. **속성** 창에서 **Name** 값을 적절한 값(예: WebServer1)으로 변경합니다. **속성** 창에서 **Value**을 사용할 매개 변수(예: `http://CorporateStagingWebServer`)로 변경합니다.

5. (선택 사항) **Value** 속성에 다른 문자열(예: `http://CorporateProductionWebServer`)을 사용하여 3-5단계를 반복합니다.

6. 활성 상태로 설정할 실행 설정을 선택합니다. 실행 설정에 대한 바로 가기 메뉴를 열고 **활성 상태로 설정**을 선택합니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 실행 설정 구성](../test/configure-load-test-run-settings.md)

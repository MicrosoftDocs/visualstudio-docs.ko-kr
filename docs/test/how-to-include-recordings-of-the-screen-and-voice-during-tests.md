---
title: 테스트 중에 화면 및 음성 기록
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, recording desktop video
ms.assetid: 2cefe8c2-430a-4cb4-bbe0-f3edb2e5bc03
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94d8fdc2765b3a073ca481d09bc38dfbc9b38f2c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589021"
---
# <a name="how-to-include-recordings-of-the-screen-and-voice-during-tests-using-test-settings"></a>방법: 테스트 설정을 사용하여 테스트를 수행하는 중에 화면 및 음성의 녹화/녹음 포함

Visual Studio의 구성 편집기에서 화면 및 테스트를 실행하는 사용자의 음성을 기록하는 진단 데이터 어댑터를 구성할 수 있습니다. 이 진단 데이터 어댑터는 테스트 중 데스크톱 세션의 화면 및 음성 기록을 저장합니다. 기록은 테스트 결과와 함께 저장 되거나 또는 버그에 첨부될 수 있습니다. 다른 팀 멤버가 기록을 사용해서 재현하기 어려운 애플리케이션 결함을 격리할 수 있습니다.

> [!WARNING]
> 화면 및 음성 기록에서는 다중 모니터 구성이 지원되지 않습니다.

화면 및 음성 레코더는 수동 또는 자동 테스트에서 사용할 수 있습니다. 예를 들어 코딩된 UI 테스트를 원격으로 실행하는 경우 컴퓨터 화면을 녹화하여 코딩된 UI 테스트가 실행되는 과정을 확인할 수 있습니다. 원격으로 화면 및 음성 기록을 캡처하는 방법에 대한 자세한 내용은 [방법: 데스크톱과 상호 작용하는 테스트를 실행하기 위해 테스트 에이전트 설정](../test/how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop.md)을 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-configure-screen-and-voice-recording-for-your-test-settings"></a>테스트 설정에 대한 화면 및 음성 기록을 구성하려면

1. 화면 및 음성을 기록하기 위해 구성할 테스트 설정을 엽니다. 자세한 내용은 [테스트하는 동안 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts) 또는 [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)을 참조하세요.

2. 테스트 설정에서 화면 및 음성을 기록하는 데 사용할 **역할**을 선택합니다.

    > [!NOTE]
    > 수동 테스트 및 자동화된 테스트의 경우 이 역할은 테스트를 실행하는 컴퓨터가 맡습니다.

3. **화면 및 음성 레코더**를 선택한 다음, **구성**을 선택합니다.

     **진단 데이터 어댑터 구성 - 화면 및 음성 레코더** 대화 상자가 표시됩니다.

     ![비디오 구성](../test/media/testsettingvideoconfiggdr.png)

4. (선택 사항) **음성 기록 사용**을 선택하여 기록에서 오디오 콘텐츠를 캡처합니다.

5. (선택 사항) 실패한 테스트와 성공한 테스트 모두에 대해 화면 및 음성 기록을 저장하도록 지정하려면 **테스트 사례가 통과하면 기록 저장** 옆의 확인란을 선택합니다.

    > [!WARNING]
    > **테스트 사례가 통과하면 기록 저장**을 선택하는 경우 서버의 스토리지 공간을 사용하여 테스트 결과와 함께 기록이 저장됩니다. 이러한 첨부 파일은 **테스트 첨부 파일 정리기** 도구를 사용하여 정리할 수 있습니다.

6. **화면 기록 품질**에서 다음 드롭다운 목록 옵션을 구성합니다.

    1. **프레임 속도:** 화면 및 음성 기록에 사용할 초당 프레임 수를 지정합니다. 기본값은 초당 4개의 프레임입니다. 2에서 20 사이의 값을 지정할 수 있습니다.

    2. **비트 전송률:** 화면 및 음성 기록에 사용할 초당 킬로바이트 수를 지정합니다. 기본값은 512입니다. 512에서 10,000 사이의 값을 지정할 수 있습니다.

    3. **품질(1-100):** 1에서 100 사이의 값을 선택하여 화면 및 음성 기록의 품질을 지정할 수 있습니다. 기본값은 50(중간 범위)입니다.

7. **확인**을 선택합니다. 테스트 설정에 대해 진단 추적 수집기 설정이 구성 및 저장됩니다.

    > [!TIP]
    > 이 진단 데이터 어댑터의 구성을 다시 설정하려면 Visual Studio의 경우 **기본 구성으로 다시 설정**을 선택하고 Microsoft Test Manager의 경우에는 **기본값으로 다시 설정**을 선택합니다.

## <a name="see-also"></a>참고 항목

- [테스트하는 동안 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [수동 테스트에서 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)
- [수동 테스트 실행(Azure Test Plans)](/azure/devops/test/run-manual-tests?view=vsts)

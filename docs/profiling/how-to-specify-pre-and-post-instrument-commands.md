---
title: 계측 전 명령 및 계측 후 명령 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 904a5086af4fbbd9c1ef174cae63013cb8c96ad9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851803"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>방법: 계측 전 명령 및 계측 후 명령 지정

성능 세션의 이진 파일이 계측되기 전이나 계측된 후 실행되는 명령을 지정할 수 있습니다. 명령줄에서 실행될 수 있는 모든 명령을 계측 전 또는 계측 후 이벤트로 지정할 수 있습니다. 예를 들어 이진 파일이 계측된 후 실행되는 배치 파일에서 강력한 이름 키를 사용하여 어셈블리 재서명을 자동화하는 명령을 지정할 수 있습니다.

프로파일링 실행의 모든 계측된 이진 파일에 대한 명령이나 개별 이진 파일에 대한 명령을 지정합니다. 그러나 계측 프로세스 전에 실행할 계측 전 명령을 하나만 지정하고 계측 프로세스 후에 실행할 계측 후 명령을 하나만 지정할 수 있습니다. 모든 이진 파일 및 개별 이진 파일에 대한 명령을 둘 다 지정할 수는 없습니다. 모든 이진 파일에 대한 명령을 지정하면 세션에서 각 이진 파일의 계측 이전 또는 이후에 명령이 실행됩니다.

명령이 실행되는 작업 디렉터리는 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]를 실행 중인 운영 체제 및 프로파일링된 애플리케이션의 대상 플랫폼에 따라 달라집니다.

프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요.

## <a name="to-specify-pre-instrument-commands"></a>계측 전 명령을 지정하려면

1. 다음 단계 중 하나를 수행합니다.

    - 성능 세션에서 모든 이진 파일에 대한 계측 전 명령을 지정하려면 **성능 탐색기**에서 성능 세션을 선택하고 나서 마우스 오른쪽 단추를 클릭하고 **속성**을 선택합니다.

    - 특정 이진 파일에 대한 계측 전 명령을 지정하려면 성능 세션의 **대상** 목록에서 이진 파일의 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

2. **속성 페이지**에서 **계측**을 클릭합니다.

3. **계측 전 이벤트** 아래 **명령줄** 텍스트 상자에 명령을 입력합니다.

    > [!NOTE]
    > **명령줄** 상자에 인접한 줄임표 단추 **(...)** 를 클릭하여 해당하는 .exe, .cmd 또는 .bat 파일로 이동하고 파일을 선택합니다.

4. **확인**을 클릭합니다.

     명령을 제거하지 않고 명령이 실행되지 않게 하려면 **계측에서 제외** 확인란을 선택합니다. 컴파일러 또는 링커 설정을 수정하려면 프로젝트 속성 페이지를 사용합니다.

## <a name="to-specify-post-instrument-commands"></a>계측 후 명령을 지정하려면

1. 다음 단계 중 하나를 수행합니다.

    - 성능 세션에서 모든 이진 파일에 대한 계측 후 명령을 지정하려면 **성능 탐색기**에서 성능 세션을 선택하고 나서 마우스 오른쪽 단추를 클릭하고 **속성**을 선택합니다.

    - 특정 이진 파일에 대한 계측 후 명령을 지정하려면 성능 세션의 **대상** 목록에서 이진 파일의 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

2. **속성 페이지**에서 **계측**을 클릭합니다.

3. **계측 후 이벤트** 아래 **명령줄** 텍스트 상자에 명령을 입력합니다.

    > [!NOTE]
    > **명령줄** 상자에 인접한 줄임표 단추 **(...)** 를 클릭하여 해당하는 .exe, .cmd 또는 .bat 파일로 이동하고 파일을 선택합니다.

4. **확인**을 클릭합니다.

     명령을 제거하지 않고 명령이 실행되지 않게 하려면 **계측에서 제외** 확인란을 선택합니다. 컴파일러 또는 링커 설정을 수정하려면 프로젝트 속성 페이지를 사용합니다.

## <a name="see-also"></a>참조

[성능 세션 구성](../profiling/configuring-performance-sessions.md)

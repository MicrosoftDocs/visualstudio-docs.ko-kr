---
title: ActiveX 컨트롤 디버그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc15d42aa2984a7257687eeb051ce754bace9e81
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852167"
---
# <a name="how-to-debug-an-activex-control"></a>방법: ActiveX 컨트롤 디버그

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

ActiveX 컨트롤을 디버깅하려면 컨트롤을 실행할 컨테이너(실행 파일)를 지정해야 합니다.

## <a name="to-specify-a-container-for-the-debug-session"></a>디버그 세션에 사용할 컨테이너를 지정하려면

1. 솔루션 탐색기에서 프로젝트를 선택합니다.

2. **보기** 메뉴에서 **속성 페이지**를 선택합니다.

3. **프로젝트 속성 페이지** 대화 상자에서 **구성 속성** 폴더를 열고 **디버깅**을 선택합니다.

4. **디버깅** 범주에서 **명령** 속성을 찾습니다.

5. 컨테이너의 경로 이름을 지정하십시오. 예를 들어, C:\Program Files\Internet Explorer\IEXPLORE.EXE와 같이 입력하십시오.

6. Internet Explorer를 컨테이너로 지정하고 Active Desktop을 사용하는 경우에는 **명령 인수** 상자에 `/new`를 입력합니다.

7. **확인**을 클릭합니다.

     **프로젝트 속성 페이지** 대화 상자에서 컨테이너를 지정하지 않은 경우에는 디버깅을 시작할 때 컨테이너를 지정할 수 있습니다. 디버깅을 시작하는 실행 명령을 선택하면 [디버깅 세션에 사용할 실행 파일 대화 상자](../debugger/executable-for-debugging-session-dialog-box.md)가 나타납니다. 대화 상자에서 컨테이너의 경로 이름을 지정합니다.

## <a name="see-also"></a>참조

- [ActiveX 컨트롤](/cpp/mfc/activex-controls)
- [테스트 컨테이너로 속성 및 이벤트 테스트](/cpp/mfc/testing-properties-and-events-with-test-container)
- [COM 및 ActiveX 디버깅](../debugger/com-and-activex-debugging.md)
- [Visual Studio의 디버깅](../debugger/index.yml)
- [디버거 소개](../debugger/debugger-feature-tour.md)
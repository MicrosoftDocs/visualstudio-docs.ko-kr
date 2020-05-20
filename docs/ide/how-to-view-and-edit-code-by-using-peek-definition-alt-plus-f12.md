---
title: 정의 피킹(Peeking) 사용
ms.date: 01/10/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9eac5c8c47c208f39f74f542fbbff89c8340a93f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591348"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>방법: 정의 피킹(Peeking)을 사용하여 코드 보기 및 편집(Alt+F12)

**정의 피킹(Peeking)** 명령을 사용하여 작성하고 있는 코드에서 전환하지 않고 코드를 보고 편집할 수 있습니다. **정의 피킹(Peeking)** 및 **정의로 이동**은 같은 정보를 표시하지만 **정의 피킹(Peeking)** 은 팝업 창에 표시하고 **정의로 이동**은 별도의 코드 창에 코드를 표시합니다. **정의로 이동**을 사용하면 컨텍스트(즉, 활성 코드 창, 현재 줄 및 커서 위치)를 정의 코드 창으로 전환합니다. **정의 피킹(Peeking)** 을 사용하면 정의를 보고 편집하며 정의 파일 내부로 이동하여 원래 코드 파일을 유지할 수 있습니다.

**정의 피킹(Peeking)** 은 C#, Visual Basic 및 C++ 코드에서 사용할 수 있습니다. Visual Basic에서 **정의 피킹(Peeking)** 은 정의 메타데이터가 없는 기호에 대한 **개체 브라우저** 링크를 보여 줍니다(예: 기본 제공되는 .NET 형식).

## <a name="use-peek-definition"></a>정의 피킹(Peeking) 사용

### <a name="open-a-peek-definition-window"></a>정의 피킹(Peeking) 창 열기

1. 검색하려는 형식 또는 멤버의 오른쪽 클릭 메뉴에서 **정의 피킹**을 선택하여 정의를 피킹할 수 있습니다. 이 옵션을 설정하는 경우, **Ctrl** 키(또는 다른 한정자)를 누르고 멤버 이름을 클릭하여 마우스를 사용하는 정의를 피킹할 수도 있습니다. 또는 키보드에서 **Alt**+**F12**를 누릅니다.

     이 그림은 `Print()`라는 메서드에 대한 **정의 피킹(Peeking)** 창을 보여 줍니다.

     ![피크(Peek) 창](../ide/media/peekwindow.png)

     정의 창은 원본 파일에서 아래에 표시된 `printer.Print("Hello World!")` 줄로 나타납니다. 창에 기존 파일의 코드를 전부 숨기지 않습니다. `printer.Print("Hello World!")` 뒤에 나오는 줄은 정의 창 아래에 나타납니다.

1. [정의 피킹(Peeking)] 창에서 여러 위치로 커서를 이동할 수 있습니다. 원본 코드 창에서 계속 이동할 수 있습니다.

1. 정의 창에서 문자열을 복사하여 원본 코드에 붙여 넣을 수 있습니다. 정의 창에서 삭제하지 않고도 정의 창에서 원래 코드로 문자열을 끌어서 놓을 수도 있습니다.

1. **Esc** 키를 선택하거나 정의 창 탭에서 **닫기** 단추를 선택하여 정의 창을 닫을 수 있습니다.

### <a name="open-a-peek-definition-window-from-within-a-peek-definition-window"></a>정의 피킹(Peeking) 창 내에서 정의 피킹(Peeking) 창 열기

이미 **정의 피킹(Peeking)** 창이 열려 있는 경우 해당 창에 있는 코드에서 **정의 피킹(Peeking)** 을 다시 호출할 수 있습니다. 다른 정의 창이 열립니다. 일련의 breadcrumb 점은 정의 창 사이를 탐색하는 데 사용할 수 있는 정의 창 탭 옆에 나타납니다. 각 점의 도구 설명에는 점이 나타내는 파일 이름 및 정의 파일의 경로가 나와 있습니다.

   ![피크(Peek) 창 내부의 피크(Peek) 창](../ide/media/peekwithinpeek.png)

### <a name="peek-definition-with-multiple-results"></a>여러 결과에서 정의 피킹

둘 이상의 정의가 있는 코드에서 **정의 피킹(Peeking)** 을 사용하는 경우(예: 부분 클래스) 결과 목록이 코드 정의 보기 오른쪽에 나타납니다. 목록에서 결과를 선택하여 해당 정의를 표시할 수 있습니다.

   ![여러 결과의 피크(Peek) 창](../ide/media/peekmultiple.png)

### <a name="edit-inside-the-peek-definition-window"></a>정의 피킹(Peeking) 창 내에서 편집

이 **정의 피킹(Peeking)** 창 내에서 편집을 시작하는 경우, 수정하고 있는 파일은 코드 편집기의 별도 탭으로 자동으로 열리고 변경한 내용을 반영합니다. **정의 피킹(Peeking)** 창에서 계속 변경, 실행 취소, 변경 내용 저장을 할 수 있고 탭은 그러한 변경 내용을 계속 반영합니다. 변경 내용을 저장하지 않고 **정의 피킹** 창을 닫더라도 정확히 **정의 피킹** 창에서 중단한 지점에서 탭의 더 많은 내용을 변경, 실행 취소, 저장할 수 있습니다.

   ![피킹(Peek) 창에서 편집](../ide/media/peekedit.png)

### <a name="to-change-options-for-peek-definition"></a>정의 피킹에 대한 옵션을 변경하려면

1. **도구** > **옵션** > **텍스트 편집기** > **일반**으로 이동합니다.

1. **피킹 보기에서 정의 열기** 옵션을 선택합니다.

1. **확인** 을 클릭하여 **옵션** 대화 상자를 닫습니다.

   ![마우스 클릭 정의 피킹 옵션 설정](../ide/media/editor_options_peek_view.png)

### <a name="keyboard-shortcuts-for-peek-definition"></a>정의 피킹에 대한 바로 가기 키

**정의 피킹(Peeking)** 창에 사용할 수 있는 바로 가기 키는 다음과 같습니다.

|기능|바로 가기 키|
|-------------------|:-----------------------:|
|정의 창 열기|**Alt**+**F12**|
|정의 창 닫기|**Esc**|
|정의 창을 일반 문서 탭으로 승격|**Shift**+**Alt**+**Home**|
|정의창 사이 탐색|**Ctrl**+**Alt**+ **-** 및 **Ctrl**+**Alt**+ **=**|
|여러 결과 사이 이동|**F8** 및 **Shift**+**F8**|
|코드 편집기 창 또는 정의 창으로 전환|**Shift**+**Esc**|

> [!NOTE]
> **정의 피킹(Peeking)** 창에서 코드를 편집하기 위해 Visual Studio의 다른 위치에서 사용할 때와 같은 바로 가기 키를 사용할 수도 있습니다.

## <a name="see-also"></a>참고 항목

- [코드 탐색](../ide/navigating-code.md)
- [정의로 이동 및 정의 피킹(Peeking)](../ide/go-to-and-peek-definition.md)
- [Visual Studio의 생산성 기능](../ide/productivity-features.md)

---
title: 형식 정의 보기
ms.date: 01/10/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ef13b959d4e106b451ea0cfb336835059667ce4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592076"
---
# <a name="view-type-and-member-definitions"></a>형식 및 멤버 정의 보기

개발자는 종종 코드에서 사용하는 형식 또는 클래스 멤버에 대한 소스 코드 정의를 확인해야 합니다. Visual Studio에서는 **정의로 이동** 및 **정의 피킹(Peeking)** 기능을 사용하여 형식 또는 멤버의 정의를 쉽게 볼 수 있습니다. 소스 코드를 사용할 수 없는 경우 메타데이터가 대신 표시됩니다.

## <a name="go-to-definition"></a>정의로 이동

**정의로 이동** 기능은 형식 또는 멤버의 소스로 이동하고 새 탭에 결과를 엽니다. 키보드 사용자인 경우 텍스트 커서를 기호 이름의 어딘가에 놓고 **F12** 키를 누릅니다. 마우스 사용자인 경우 오른쪽 클릭 메뉴에서 **정의로 이동**을 선택하거나 다음 섹션에 설명된 **Ctrl-클릭** 기능을 사용합니다.

### <a name="ctrl-click-go-to-definition"></a>Ctrl 키를 누른 채로 [정의로 이동] 클릭

**Ctrl**+**클릭**은 마우스 사용자가 **정의로 이동**에 빠르게 액세스할 수 있는 바로 가기입니다. 기호는 **Ctrl** 키를 누르고 해당 형식이나 멤버 위로 마우스를 가져 가면 클릭할 수 있게 됩니다. 기호 정의로 빠르게 이동하려면 **Ctrl** 키를 누른 상태에서 기호를 클릭합니다. 너무나 쉽습니다!

![마우스 클릭 정의로 이동 애니메이션](../ide/media/click_gotodef.gif)

**도구** > **옵션** > **텍스트 편집기** > **일반**으로 이동하고 **보조 키 사용** 드롭다운에서 **Alt** 또는 **Ctrl**+**Alt**를 선택하여 **정의로 이동**에 대한 보조 키를 변경할 수 있습니다. **마우스를 클릭하면 정의로 이동하도록 허용** 확인란을 선택 취소하여 마우스 클릭 **정의로 이동**을 사용하지 않도록 설정할 수도 있습니다.

![마우스 클릭 정의로 이동 사용](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>정의 피킹(Peeking)

**정의 피킹** 기능을 사용하면 편집기에서 현재 위치를 벗어나지 않고 형식 정의를 미리 볼 수 있습니다. 키보드 사용자인 경우 텍스트 커서를 형식 또는 멤버 이름의 어딘가에 놓고 **Alt + F12** 키를 누릅니다. 마우스 사용자인 경우 오른쪽 클릭 메뉴에서 **정의 피킹**을 선택할 수 있습니다.

**Ctrl**+**클릭** 기능을 사용하려면 **도구** > **옵션** >  **텍스트 편집기** > **일반**으로 이동합니다. **Peek 뷰에서 정의 열기** 옵션을 선택하고 **확인**을 클릭하여 **옵션** 대화 상자를 닫습니다.

![마우스 클릭 정의 피킹 옵션 설정](../ide/media/editor_options_peek_view.png)

그런 다음 **Ctrl**(또는 **옵션**에서 선택한 보조 키) 키를 누르고 형식 또는 멤버를 클릭합니다.

![정의 피킹 애니메이션](../ide/media/peek_definition.gif)

팝업 창에서 다른 정의를 피킹하는 경우 팝업 위에 표시되는 원과 화살표를 사용하여 탐색할 수 있는 이동 경로가 시작됩니다.

자세한 내용은 [방법: 정의 피킹(Peeking)을 사용하여 코드 보기 및 편집(Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)을 참조하세요.

## <a name="view-metadata-as-source-code-c"></a>메타데이터를 소스 코드로 보기(C#)

소스 코드를 사용할 수 없는 C# 형식 또는 멤버의 정의를 볼 경우 해당 메타데이터가 대신 표시됩니다. 형식 및 멤버의 선언을 볼 수 있지만 해당 구현은 볼 수 없습니다.

소스 코드를 사용할 수 없는 항목에 대해 **정의로 이동** 또는 **정의 피킹(Peeking)** 명령을 실행하면 해당 항목의 메타데이터가 소스 코드로 표시된 보기를 포함하는 탭 문서가 코드 편집기에 나타납니다. 뒤에 **[메타데이터에서]** 가 추가된 형식 이름이 문서 탭에 나타납니다.

예를 들어 <xref:System.Console>에 대해 **정의로 이동** 명령을 실행하는 경우 <xref:System.Console>에 대한 메타데이터가 코드 편집기에 C# 소스 코드로 나타납니다. 코드는 선언과 유사하지만 구현을 표시하지는 않습니다.

![소스로서의 메타데이터](../ide/media/metadatasource.png)

> [!NOTE]
> 내부로 표시된 형식 또는 멤버에 대해 **정의로 이동** 또는 **정의 피킹(Peeking)** 명령을 실행하려고 하면 참조하는 어셈블리가 friend인지 여부에 관계없이 Visual Studio에서 해당 메타데이터를 소스 코드로 표시하지 않습니다.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>메타데이터 대신 디컴파일된 소스 정의 보기(C#)

소스 코드를 사용할 수 없는 C# 형식 또는 멤버의 정의를 볼 때 디컴파일된 소스 코드를 볼 수 있는 옵션을 설정할 수 있습니다. 이 기능을 켜려면 메뉴 모음에서 **도구** > **옵션**을 선택합니다. 그런 다음 **텍스트 편집기** > **C#**  > **고급**을 확장하고 **디컴파일된 소스에 대한 탐색 사용**을 선택합니다.

![디컴파일된 정의 보기](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio는 ILSpy 디컴파일을 사용하여 메서드 본문을 다시 만듭니다. 이 기능에 처음으로 액세스할 때는 소프트웨어 라이선스와 저작권 및 상표 관련 법률에 관한 법적 고지 사항에 동의해야 합니다.

## <a name="see-also"></a>참조

- [코드 탐색](../ide/navigating-code.md)
- [방법: 정의 피킹(Peeking)을 사용하여 코드 보기 및 편집(Alt+F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

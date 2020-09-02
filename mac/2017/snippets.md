---
title: 코드 조각
description: Mac용 Visual Studio에서 코드 조각을 사용하여 효율적으로 프로그래밍하는 방법
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 0FE27C0C-A861-4133-A74E-8D0505CF5342
ms.openlocfilehash: 96344b72dd27095f8b9060078112fb767b1338fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984815"
---
# <a name="code-snippets"></a>코드 조각

_코드 템플릿_이라고도 하는 코드 조각은 미리 작성된 코드 블록을 삽입하고 편집하여 프로그래밍의 능률을 높이는 데 유용합니다. 코드 조각을 사용하면 공통 패턴을 빠르게 추가하거나 개발자가 구문을 잘 모르는 경우 새로운 패턴을 배우는 데도 편리합니다. C#, F#, HTML, XML, Python 및 Razor용 템플릿이 제공됩니다.

이 섹션에서는 코드 조각을 만들고, 삽입하고, 사용하는 방법을 설명합니다.

## <a name="inserting-a-snippet"></a>코드 조각 삽입

다양한 방법으로 코드 조각을 추가할 수 있으며, 아래에서는 그중 일부를 설명합니다.

- **탭 확장** &ndash; 템플릿 이름을 입력하여 목록에서 해당 이름을 선택하고 **탭** 및 **탭** 키를 눌러 다음을 추가합니다.

  ![코드의 탭 확장](media/source-editor-image13.png)

- **도구 상자** &ndash; 도구 상자 패드를 사용하여 모든 코드 조각의 목록을 표시합니다. 도구 상자의 템플릿을 소스 코드에서 올바른 위치에 끌어 놓습니다.

  [![도구 상자의 코드 조각](media/source-editor-image14-sml.png)](media/source-editor-image14.png#lightbox)

- **템플릿 삽입 명령** &ndash; 현재는 템플릿 삽입 기능에 설정된 기본 키 바인딩이 없습니다. 키 바인딩을 만들려면 **Visual Studio > 기본 설정 > 키 바인딩**으로 이동하고 `template`을 검색합니다. 이렇게 하면 [바인딩 편집] 필드에 원하는 키 바인딩을 추가한 다음 **적용**을 클릭할 수 있습니다.

  ![템플릿 삽입 명령](media/source-editor-image15.png)

## <a name="creating-a-new-template"></a>새 템플릿 만들기

다양한 언어로 작성된 수많은 기존 템플릿을 사용하고 편집할 수 있지만, **Visual Studio > 기본 설정 > 텍스트 편집기 > 코드 조각**으로 이동하여 새 템플릿을 추가할 수도 있습니다.

![새 템플릿 삽입](media/source-editor-image12.png)

**추가** 또는 **편집** 단추를 눌러 코드 조각을 만들거나 편집합니다.

## <a name="keywords-in-code-snippets"></a>코드 조각의 키워드

코드 조각이 편집기에 삽입되면 정의된 모든 키워드가 강조 표시되고 탭으로 이동하며 편집할 수 있습니다. 키워드는 코드 조각에서 “변수”처럼 행동하며 키워드 이름 앞과 뒤에 달러 기호(`$`)를 배치하여 정의됩니다. 

**템플릿 편집** 창이 아래에 표시되어, 기본 제공 `prop` 코드 조각을 편집할 수 있습니다. 코드 조각에는 창의 오른쪽에 추가 속성 집합(기본값, 도구 설명 등)을 가질 수 있는 &ndash; `$type$` 및 `$name$` &ndash; 등 두 개의 키워드가 포함되어 있습니다.

![템플릿 편집 창](media/source-editor-image12z.png)

다음 필드는 코드 조각을 정의하는 데 사용됩니다.

- **바로 가기** &ndash; 사용자가 코드 조각을 삽입할 때 입력하는 텍스트입니다.
- **그룹** &ndash; 코드 조각은 이 값을 사용하여 코드 조각 콘텐츠 메뉴에 그룹화됩니다.
- **설명** &ndash; 코드 조각의 용도에 대한 설명입니다.
- **MIME** &ndash; 코드 조각을 사용할 수 있는 파일 형식을 제어합니다.
- **Is expandable template**(확장 가능한 템플릿임) &ndash; 바로 가기를 입력하여 커서에서 코드 조각을 삽입할 수 있도록 하려면 이 옵션을 선택합니다.
- **Is surround with template**(코드 감싸기 템플릿임) &ndash; 편집기의 **코드 감싸기...** 콘텐츠 메뉴에 이 바로 가기가 나타나도록 하려면 이 옵션을 선택합니다.
- **템플릿 텍스트** &ndash; 편집기에 삽입될 실제 코드 조각입니다. 키워드 자리 표시자는 달러 기호로 토큰을 둘러싸서 정의할 수 있습니다. 예: `$type$`.
- **Keyword property panel**(키워드 속성 패널) &ndash; 창 오른쪽에서 맨 위에 있는 드롭다운 목록을 사용하여 키워드(예: `type`)를 선택하고 기본값 및 도구 설명과 같은 속성을 편집합니다.

## <a name="using-keywords-in-the-editor"></a>편집기에서 키워드 사용

위에 정의된 것과 같이 키워드가 포함된 코드 조각을 사용하려면 바로 가기를 입력하고 **Tab** 키를 두 번 누릅니다. 그러면 커서에 코드 조각 콘텐츠가 삽입됩니다.

![키워드를 표시하는 삽입된 코드 조각](media/source-editor-image12a.png)

**Tab** 키를 눌러 `object` 및 `MyProperty` 사이를 이동하며 클래스에 대한 코드 조각을 사용자 지정합니다.

키워드를 하나의 코드 조각에서 반복할 수 있습니다. 이 `for` 예제의 경우 `$i$` 키워드가 3번 표시됩니다.

![반복되는 키워드가 있는 코드 조각 템플릿](media/source-editor-image12b.png)

편집기에서 사용할 경우 **Tab** 키가 첫 번째 `i` 및 `max` 사이에 전환됩니다. 다른 변수 이름을 가진 `i`를 겹쳐쓰는 경우 세 인스턴스가 모두 업데이트됩니다.

![여러 키워드를 표시하는 삽입된 코드 조각](media/source-editor-image12c.png)

### <a name="reserved-keywords"></a>예약 키워드

코드 조각에서 사용할 수 있는 두 개의 예약 키워드가 있습니다.

- `$selected$` &ndash; 코드 조각에 **Is surround with template**(감싸기 템플릿임)이 선택되어 있는 경우 이 키워드는 코드 조각 선택 시 편집기에서 강조 표시된 텍스트로 바뀝니다.
- `$end$` &ndash; 사용자가 코드 조각의 키워드 편집을 완료하면 커서가 `$end$` 키워드의 위치에 배치됩니다.

이전 섹션의 `for` 코드 조각은 이러한 두 예약 키워드의 예제입니다.

자세한 내용은 [Visual Studio code snippets reference](/visualstudio/ide/code-snippets-schema-reference#keywords)(Visual Studio 코드 조각 참조)를 참조하세요.

## <a name="see-also"></a>추가 정보

- [코드 조각(Windows의 Visual Studio)](/visualstudio/ide/code-snippets)
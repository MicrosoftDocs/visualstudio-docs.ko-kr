---
title: 찾기/명령 상자
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findcommandbox
helpviewer_keywords:
- Find/Command box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99b50c0503d313d4482d8370071220dbf1403d9a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591530"
---
# <a name="findcommand-box"></a>찾기/명령 상자

텍스트를 검색하고 **찾기/명령** 상자에서 Visual Studio 명령을 실행할 수 있습니다. **찾기/명령** 상자를 도구 모음 컨트롤로 사용할 수 있지만 이 상자는 더 이상 기본적으로 표시되지 않습니다. **찾기/명령** 상자를 표시하려면 **표준** 도구 모음에서 **단추 추가/제거**를 선택하고 나서 **찾기**를 선택합니다.

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 명령을 실행하려면 앞에 보다 큼( **>** ) 기호를 붙입니다.

**찾기/명령** 상자는 입력된 마지막 20개 항목을 유지하고 드롭다운 목록에 표시합니다. **화살표 키**를 선택하여 목록을 이동할 수 있습니다.

![찾기&#47;명령 상자](../ide/media/findcommandbox.png)

## <a name="searching-for-text"></a>텍스트 검색

기본적으로 **찾기/명령** 상자에 텍스트를 지정한 다음 **Enter** 키를 선택하면 Visual Studio는 **파일에서 찾기** 대화 상자에 지정된 옵션을 사용하여 현재 문서 또는 도구 창을 검색합니다. 자세한 내용은 [텍스트 찾기 및 바꾸기](../ide/finding-and-replacing-text.md)를 참조하세요.

## <a name="entering-commands"></a>명령 입력

**찾기/명령** 상자를 사용하여 텍스트 검색이 아닌 단일 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 명령이나 별칭을 실행하려면 해당 명령 앞에 보다 큼( **>** ) 기호를 배치합니다. 다음은 그 예입니다.

```
>File.NewFile c:\temp\MyFile /t:"General\Text File"
```

또는 **명령** 창을 사용하여 단일 또는 여러 명령을 입력하고 실행할 수도 있습니다. 일부 명령 또는 별칭은 직접 입력 및 실행할 수 있으며 구문에 인수가 필요한 명령도 있습니다. 인수가 있는 명령 목록은 [Visual Studio 명령](../ide/reference/visual-studio-commands.md)을 참조하세요.

## <a name="escape-characters"></a>이스케이프 문자

명령의 캐럿( **^** ) 문자는 캐럿 바로 뒤의 문자가 제어 문자가 아닌 문자 그대로 해석된다는 것을 의미합니다. 이스케이프 문자는 매개 변수 또는 스위치 값에 곧은 큰따옴표( **"** ), 공백, 선행 슬래시, 캐럿 등 또는 리터럴 문자를 포함하기 위해 사용할 수 있습니다(스위치 이름 제외). 다음은 그 예입니다.

```
>Edit.Find ^^t /regex
```

캐럿은 따옴표 내부에 있든 외부에 있든 기능이 동일합니다. 캐럿이 줄에서 마지막 문자인 경우 무시됩니다.

## <a name="see-also"></a>참고 항목

- [명령 창](../ide/reference/command-window.md)
- [텍스트 찾기 및 바꾸기](../ide/finding-and-replacing-text.md)

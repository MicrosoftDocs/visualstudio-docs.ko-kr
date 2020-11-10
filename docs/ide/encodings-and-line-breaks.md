---
title: 인코딩 및 줄 바꿈 문자
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6634a0b2715fb83a397b5e8cd0c8c68274771e2a
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93045598"
---
# <a name="encodings-and-line-endings"></a>인코딩 및 줄 끝

Visual Studio에서 다음 문자는 줄 바꿈으로 해석됩니다.

- CR LF: 캐리지 리턴 + 줄 바꿈, 유니코드 문자 000D + 000A

- LF: 줄 바꿈, 유니코드 문자 000A

- NEL: 다음 줄, 유니코드 문자 0085

- LS: 줄 구분 기호, 유니코드 문자 2028

- PS: 단락 구분 기호, 유니코드 문자 2029

다른 애플리케이션에서 복사되는 텍스트는 원래 인코딩 및 줄 바꿈 문자를 유지합니다. 예를 들어 메모장에서 텍스트를 복사하고 Visual Studio의 텍스트 파일로 붙여넣으면 텍스트에는 메모장의 텍스트와 같은 설정이 포함됩니다.

다른 줄 바꿈 문자가 포함된 파일을 열 경우 일치하지 않는 줄 바꿈 문자를 정규화할지 여부 및 선택할 줄 바꿈 형식을 묻는 대화 상자가 표시될 수 있습니다.

## <a name="advanced-save-options"></a>고급 저장 옵션

**파일** > **고급 저장 옵션** 대화 상자를 사용하여 원하는 줄 바꿈 문자의 형식을 결정할 수 있습니다. 같은 설정을 사용하여 파일의 인코딩을 변경할 수도 있습니다.

![고급 저장 옵션 대화 상자](media/line_endings.png)

> [!NOTE]
> **파일** 메뉴에서 **고급 저장 옵션** 이 보이지 않으면 추가할 수 있습니다. 
> 1. **도구** , **사용자 지정** 을 선택합니다. 
> 1. **명령** 탭을 선택하고 **메뉴 표시줄** 라디오 단추를 선택한 다음 해당 드롭다운 목록에서 **파일** 을 선택합니다. **명령 추가** 단추를 선택합니다. 
> 1. **명령 추가** 대화 상자의 **범주** 에서 **파일** 을 선택한 다음, **명령** 목록에서 **고급 저장 옵션** 을 선택합니다. **확인** 단추를 선택합니다.
> 1. **위로 이동** 및 **아래로 이동** 단추를 사용하여 명령을 메뉴의 원하는 위치로 이동합니다. **닫기** 를 선택하여 **사용자 지정** 대화 상자를 닫습니다. 
> 자세한 내용은 [메뉴 및 도구 모음 사용자 지정](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu)을 참조하세요.
>
> 또는 **파일** > **다른 이름으로 \<file\> 저장** 을 선택하여 **고급 저장 옵션** 대화 상자에 액세스할 수 있습니다. **다른 이름으로 파일 저장** 대화 상자에서 **저장** 단추 옆의 드롭다운 삼각형을 선택한 다음 **인코딩하여 저장** 을 선택합니다.

## <a name="see-also"></a>참고 항목

- [코드 편집기의 기능](../ide/writing-code-in-the-code-and-text-editor.md)

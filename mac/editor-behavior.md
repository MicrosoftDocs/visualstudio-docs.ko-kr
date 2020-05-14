---
title: 코드 서식
description: 이 문서는 Mac용 Visual Studio에서 텍스트 편집기 동작을 수정하는 데 사용할 수 있는 여러 옵션을 설명합니다.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.assetid: 81EE4460-26EB-4BB0-9297-932E1F88E4B8
ms.openlocfilehash: 20363d5497ea5897cb2685ca838da44b8c21d3df
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "67823170"
---
# <a name="editor-behavior"></a>편집기 동작

작성된 대로 코드에 형식이 지정될 수 있도록 편집기 동작을 설정할 수 있습니다. 이러한 작업은 **Visual Studio > 기본 설정 > 텍스트 편집기 > 동작**에서 설정되며, 아래에서는 자주 사용하는 몇 가지 기능에 대해 설명합니다.

![편집기 동작 옵션](media/source-editor-image9.png)

* 새 클래스, 메서드 또는 속성을 만들 때 일치하는 닫는 중괄호를 코드에 자동으로 추가할 수 있습니다. 이 옵션을 선택한 경우 `{`를 입력하면 `}`가 자동으로 추가됩니다.
* 세미콜론 또는 중괄호와 같은 문자 누르기에 의해 즉석 코드 형식 지정이 트리거되어 설정된 형식 지정 기본 설정을 에뮬레이트합니다.
* 저장할 때 파일의 형식을 지정하도록 선택할 수도 있습니다. 이 경우 필요에 따라 코드를 작성할 수 있으며 IDE에서 기존 기본 설정에 따라 코드 형식을 지정합니다.
* 들여쓰기를 없음, 자동 또는 스마트로 설정할 수 있습니다. 각 옵션은 다음 작업을 수행합니다.
  * 없음 - 캐럿을 다음 줄의 시작 부분에 설정합니다.
  * 자동 - 캐럿을 다음 줄의 동일한 열에 설정합니다.
  * 스마트 - 코드에 따라 다음 줄을 들여씁니다.
* 단어 분리 동작은 OS마다 차이가 있으며, 탐색을 위해 텍스트 편집기에서 단어의 시작 위치나 끝 위치를 알아야 합니다. 형식 지정을 Unix 또는 Windows로 설정할 수 있습니다.

XML, CSS, HTML 및 JSON에 대한 형식 지정 규칙을 설정할 수도 있습니다.

## <a name="see-also"></a>참고 항목

- [코드 스타일 기본 설정(Windows의 Visual Studio)](/visualstudio/ide/code-styles-and-quick-actions)

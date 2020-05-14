---
title: 파일로 이동, 기호로 이동, 줄로 이동
ms.date: 08/14/2018
ms.topic: conceptual
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb39f1d395e48351aeacb587556224b0f86aac3e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593787"
---
# <a name="find-code-using-go-to-commands"></a>이동 명령을 사용하여 코드 찾기

Visual Studio의 **이동** 명령은 지정한 항목을 찾기 쉽도록 포커스가 있는 코드 검색을 수행합니다. 간단한 통합 인터페이스에서 특정 줄, 형식, 기호, 파일 및 멤버로 이동할 수 있습니다.

## <a name="how-to-use-it"></a>사용 방법

입력 | 함수
------------ | ---
**키보드** | **Ctrl**+**T** 또는 **Ctrl**+ **,** 를 누름
**마우스** | **편집** > **이동** > **전체로 이동**을 선택

코드 편집기의 오른쪽 위에 작은 창이 표시됩니다.

![전체로 이동 창](media/go-to-all.png)

텍스트 상자에서 입력 시 텍스트 상자 아래의 드롭다운 목록에 결과가 나타납니다. 요소로 이동하려면 목록에서 선택합니다.

![탐색 창](../ide/media/vside_navigatetowindow.png)

물음표( **?** )를 입력하여 추가 도움말을 확인할 수도 있습니다.

![전체로 이동 도움말](media/go-to-all-help.png)

## <a name="filtered-searches"></a>필터링된 검색

기본적으로 모든 솔루션 항목에서 지정된 항목만 검색됩니다. 그러나 검색 용어 앞에 특정한 문자를 넣어 코드 검색을 구체적인 요소 유형으로 제한할 수 있습니다. **이동** 대화 상자 도구 모음에서 단추를 선택하여 검색 필터를 빠르게 변경할 수도 있습니다. 형식 필터를 변경하는 단추는 왼쪽에 있고 검색 범위를 변경하는 단추는 오른쪽에 있습니다.

![멤버 이동](../ide/media/vside_navigation_toolbar.png)

### <a name="filter-to-a-specific-type-of-code-element"></a>특정 형식의 코드 요소를 필터링합니다.

특정 형식의 코드 요소로 검색을 제한하려면 검색 상자에서 접두사를 지정하거나 다섯 개의 필터 아이콘 중 하나를 선택합니다.

접두사 | 아이콘 | 바로 가기 | Description
:-: | - | - | -
:| ![줄 아이콘](media/gotoall-line-icon.png) | **Ctrl**+**G** | 지정된 줄 번호로 이동합니다.
f| ![파일 아이콘](media/gotoall-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**F** | 지정된 파일로 이동합니다.
r| ![최근에 사용한 파일 아이콘](media/gotoall-recent-files-icon.png) | **Ctrl**+**1**, **Ctrl**+**R** | 지정되고 최근에 방문한 파일로 이동
t| ![형식 아이콘](media/gotoall-types-icon.png) | **Ctrl**+**1**, **Ctrl**+**T** | 지정된 형식으로 이동합니다.
m| ![멤버 아이콘](media/gotoall-members-icon.png) | **Ctrl**+**1**, **Ctrl**+**M** | 지정된 멤버로 이동합니다.
\#| ![기호 아이콘](media/gotoall-symbols-icon.png) | **Ctrl**+**1**, **Ctrl**+**S** | 지정된 기호로 이동합니다.

### <a name="filter-to-a-specific-location"></a>특정 위치로 필터링합니다.

특정 위치로 검색을 제한하려면 두 개의 문서 아이콘 중 하나를 선택합니다.

아이콘 | Description
---- | ---
![현재 문서](media/gotoall_currentdocument.png) | 현재 문서에서만 검색합니다.
![외부 문서](media/gotoall_external.png) | 프로젝트/솔루션에 있는 문서와 외부 문서를 검색합니다.

## <a name="camel-casing"></a>카멜식 대/소문자

코드에서 [카멜식 대/소문자](https://en.wikipedia.org/wiki/Camel_case)를 사용하는 경우 코드 요소 이름의 대문자만 입력하여 코드 요소를 더 빠르게 찾을 수 있습니다. 예를 들어 코드에 `CredentialViewModel`이라는 형식이 있는 경우에는 **형식** 필터(**t**)를 선택한 다음, 이동 대화 상자에서 이름을 대문자로만 입력하여(`CVM`) 검색 범위를 좁힐 수 있습니다. 이 기능은 코드 이름이 긴 경우에 유용합니다.

![창 탐색 - 대문자를 사용한 검색](../ide/media/vside_capitalsearch.png)

## <a name="settings"></a>설정

기어 아이콘 선택 ![기어 아이콘](media/gotoall_gear.png) 을 클릭하면 이 기능의 작동 방식을 변경할 수 있습니다.

설정 | Description
------- | ---
미리 보기 탭 사용 | 선택한 항목을 IDE의 미리 보기 탭에서 즉시 표시합니다.
자세한 정보 표시 | 문서 주석의 프로젝트, 파일, 줄 및 요약 정보를 창에 표시합니다.
창 가운데 맞춤 | 이 창을 코드 편집기의 오른쪽 위가 아니라 가운데 위로 이동합니다.

## <a name="see-also"></a>참고 항목

- [코드 탐색](../ide/navigating-code.md)
- [줄 이동 대화 상자](../ide/reference/go-to-line.md)
- [정의로 이동 및 정의 피킹(Peeking)](../ide/go-to-and-peek-definition.md)

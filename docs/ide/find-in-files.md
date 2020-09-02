---
title: 파일에서 찾기
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1f067df647f843819e085f283005606699f3bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595477"
---
# <a name="find-in-files"></a>파일에서 찾기

**파일에서 찾기**를 사용하여 지정된 파일 집합을 검색할 수 있습니다. 찾은 일치 항목과 수행된 작업이 **결과 옵션**에서 선택된 **결과 찾기** 창에 나열됩니다.

다음 방법 중 하나를 사용하여 **찾기 및 바꾸기** 창에서 **파일에서 찾기**를 표시할 수 있습니다.

## <a name="to-display-find-in-files"></a>파일에서 찾기를 표시하려면

1. 메뉴 모음에서 **편집** > **찾기 및 바꾸기**를 선택합니다.

1. **파일에서 찾기**를 선택합니다.

찾기 작업을 취소하려면 **Ctrl** + **중단**을 누릅니다.

> [!NOTE]
> 찾기 및 바꾸기 도구는 `Hidden` 또는 `System` 특성이 포함된 디렉터리를 검색하지 않습니다.

## <a name="find-what"></a>찾을 내용

새 텍스트 문자열이나 식을 검색하려면 상자에 지정합니다. 가장 최근에 검색한 20개 문자열 중 하나를 검색하려면 드롭다운 목록을 열고 문자열을 선택합니다. 검색 문자열에 하나 이상의 정규식을 사용하려는 경우 인접한 **식 작성기** 단추를 선택합니다. 자세한 내용은 [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)을 참조하세요.

> [!NOTE]
> **찾기 옵션** 아래에서 **정규식 사용**을 선택한 경우에만 **식 작성기** 단추를 사용할 수 있습니다.

## <a name="look-in"></a>찾는 위치

**찾는 위치** 드롭다운 목록에서 선택한 옵션에 따라 **파일에서 찾기** 에서 현재 활성화된 파일만 검색할지 아니면 특정 폴더에 저장되어 있는 모든 파일을 검색할지 여부가 결정됩니다. 목록에서 검색 범위를 선택하거나 **찾아보기(...)** 단추를 클릭하여 **검색 폴더 선택** 대화 상자를 표시하고 고유한 디렉터리 집합을 입력합니다. **찾는 위치** 상자에 경로를 직접 입력할 수도 있습니다.

> [!WARNING]
> **전체 솔루션** 또는 **현재 프로젝트** 옵션을 사용할 경우 프로젝트 및 솔루션 파일이 검색되지 않습니다. 프로젝트 파일을 확인하려는 경우 검색 폴더를 선택합니다.

> [!NOTE]
> 선택한 **찾는 위치** 옵션으로 인해 소스 코드 제어에서 체크 아웃한 파일이 검색되는 경우 로컬 컴퓨터에 다운로드된 파일 버전만 검색됩니다.

## <a name="include-subfolders"></a>하위 폴더 포함

**찾는 위치** 폴더의 하위 폴더가 검색되도록 지정합니다.

## <a name="find-options"></a>찾기 옵션

**찾기 옵션** 섹션을 확장하거나 축소할 수 있습니다. 다음 옵션을 선택하거나 선택 취소할 수 있습니다.

**대/소문자 구분**

선택하면 **찾기 결과** 검색에서 대/소문자를 구분합니다.

**단어 단위로**

선택하면 **찾기 결과** 창에 단어 단위로 일치하는 항목만 반환됩니다.

**정규식 사용**

이 확인란을 선택하면 특수 표기법을 사용하여 **찾을 내용** 또는 **바꿀 내용** 텍스트 상자에서 일치시킬 텍스트 패턴을 정의할 수 있습니다. 이러한 표기법 목록은 [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)을 참조하세요.

**이 파일 형식 보기**

이 목록은 **찾는 위치** 디렉터리에서 검색할 파일 형식을 나타냅니다. 이 필드를 비워 두면 **찾는 위치** 디렉터리의 모든 파일이 검색됩니다.

목록에서 항목을 선택하여 이러한 특정 형식의 파일을 찾을 미리 구성된 검색 문자열을 입력합니다.

## <a name="result-options"></a>결과 옵션

**결과 옵션** 섹션을 확장하거나 축소할 수 있습니다. 다음 옵션을 선택하거나 선택 취소할 수 있습니다.

**찾기 결과 1 창**

이 옵션을 선택하면 현재 검색 결과로 **찾기 결과 1** 창 내용이 바뀝니다. 이 창은 자동으로 열려 검색 결과를 표시합니다. 이 창을 수동으로 열려면 **보기** 메뉴에서 **다른 창**을 선택하고 **찾기 결과 1**을 선택합니다.

**찾기 결과 2 창**

이 옵션을 선택하면 현재 검색 결과로 **찾기 결과 2** 창 내용이 바뀝니다. 이 창은 자동으로 열려 검색 결과를 표시합니다. 이 창을 수동으로 열려면 **보기** 메뉴에서 **다른 창**을 선택하고 **찾기 결과 2**를 선택합니다.

**파일 이름만 표시**

검색 일치 항목 자체를 표시하는 대신 검색 일치 항목을 포함하는 파일 목록을 표시합니다.

**결과 추가**

검색 결과를 이전 검색 결과에 추가합니다.

## <a name="see-also"></a>추가 정보

- [텍스트 찾기 및 바꾸기](../ide/finding-and-replacing-text.md)
- [파일에서 바꾸기](../ide/replace-in-files.md)
- [Visual Studio 명령](../ide/reference/visual-studio-commands.md)

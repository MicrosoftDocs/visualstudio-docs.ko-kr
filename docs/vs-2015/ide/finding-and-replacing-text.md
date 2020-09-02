---
title: 텍스트 찾기 및 바꾸기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 025ba2eb95514efc740d1f8f7b3bf674d6bf237a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645644"
---
# <a name="finding-and-replacing-text"></a>Finding and Replacing Text
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**찾기 및 바꾸기** 컨트롤 또는 **파일에서 찾기/바꾸기**를 사용하여 **찾기 결과** 창과 같은 특정 텍스트 기반 출력 창 또는 Visual Studio Code 편집기에서 텍스트를 찾아서 바꿀 수 있습니다. XAML 디자이너, Windows Forms 디자이너와 같은 일부 디자이너 창 및 도구 창에서 검색하여 바꿀 수도 있습니다.

 검색 범위를 현재 문서, 현재 솔루션 또는 사용자 지정 폴더 집합으로 지정할 수 있습니다. 다중 파일 검색을 위해 파일 이름 확장명 집합을 지정할 수도 있습니다. .NET 정규식을 사용하여 검색 구문을 사용자 지정할 수 있습니다.

 정규식을 찾아서 바꾸려면 [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)을 참조 하세요.

> [!TIP]
> **찾기/명령** 상자를 도구 모음 컨트롤로 사용할 수 있지만 이 상자는 더 이상 기본적으로 표시되지 않습니다. **찾기/명령** 상자를 표시하려면 **표준** 도구 모음에서 **단추 추가/제거**를 선택하고 나서 **찾기**를 선택합니다. 자세한 내용은 [찾기/명령 상자](../ide/find-command-box.md)를 참조 하세요.

## <a name="find-and-replace-control"></a>찾기 및 바꾸기 컨트롤
 **찾기 및 바꾸기** 컨트롤은 코드 편집기 창의 오른쪽 위 모퉁이에 표시됩니다. **찾기 및 바꾸기** 컨트롤은 현재 문서에서 지정된 검색 문자열이 나타나는 모든 항목을 즉시 강조 표시합니다. 발생 항목 간에 이동하려면 검색 컨트롤에서 **다음 찾기** 단추 또는 **이전 찾기** 단추를 선택합니다.

 바꾸기 옵션에 액세스하려면 **찾기** 텍스트 상자 옆의 단추를 선택합니다. 한 번에 하나를 바꾸려면 **바꾸기** 텍스트 상자 옆의 **다음 찾기** 단추를 선택합니다. 모든 일치 항목을 바꾸려면 **모두 바꾸기** 단추를 선택합니다.

 일치 항목의 강조 색을 변경하려면 **도구** 메뉴를 선택하고, **옵션**, **환경**을 차례로 선택하고 나서, **글꼴 및 색**을 선택합니다. **설정 표시** 목록에서 **텍스트 편집기**를 선택하고, **표시 항목** 목록에서 **강조 찾기(확장)** 를 선택합니다.

### <a name="searching-tool-windows"></a>검색 도구 창
 **편집** 메뉴에서 **찾기 및 바꾸기** 를 선택 하 여 코드 또는 텍스트 창에서 **찾기 컨트롤을** 사용 하거나 (CTRL + F)를 사용 하 여 결과 **창을** **찾을** 수 있습니다.

 특정 버전의 찾기 컨트롤을 일부 도구 창에서 사용할 수도 있습니다. 예를 들어 이제 검색 상자에 텍스트를 입력하면 **도구 상자** 창에서 컨트롤 목록을 필터링할 수 있습니다. 현재 포함된 콘텐츠를 검색할 수 있는 기타 도구 창에는 **솔루션 탐색기**, **속성** 창 및 **팀 탐색기**가 포함됩니다.

## <a name="findreplace-in-files"></a>파일에서 찾기/바꾸기
 **파일에서 찾기/바꾸기**는 검색 범위를 정의할 수 있다는 점을 제외하고 **찾기 및 바꾸기** 컨트롤과 비슷하게 작동합니다. 편집기에서 현재 열린 파일을 검색할 수 있고 모든 열린 문서, 전체 솔루션, 현재 프로젝트 및 선택한 폴더 집합을 검색할 수도 있습니다. 파일 이름 확장명을 기준으로 검색할 수도 있습니다. **파일에서 찾기/바꾸기** 대화 상자에 액세스 하려면 **편집** 메뉴에서 **찾기 및 바꾸기** 를 선택 합니다 (또는 CTRL + SHIFT + F).

 **모두 찾기**를 선택하면 **찾기 결과** 창이 열리고 검색과 일치하는 항목이 나열됩니다. 목록에서 결과를 선택하면 연결된 파일이 표시되고 일치 항목이 강조 표시됩니다. 해당 파일이 편집하도록 열려 있지 않으면 탭 오른쪽의 미리 보기 탭에서 열립니다. **찾기** 컨트롤을 사용하여 **찾기 결과** 목록을 검색할 수 있습니다.

### <a name="creating-custom-search-folder-sets"></a>사용자 지정 검색 폴더 집합 만들기
 **찾는 위치** 상자 옆에 있는 **검색 폴더 선택** 단추 ( **...**)를 선택 하 여 검색 범위를 정의할 수 있습니다. **검색 폴더 선택** 대화 상자에서 검색할 폴더 집합을 지정할 수 있고 해당 지정 내용을 저장하여 나중에 다시 사용할 수도 있습니다. 드라이브를 로컬 컴퓨터에 매핑한 경우에만 원격 컴퓨터에서 폴더를 지정할 수 있습니다.

### <a name="creating-custom-component-sets"></a>사용자 지정 구성 요소 집합 만들기
 **찾는 위치** 상자 옆에 있는 **사용자 지정 구성 요소 집합 편집** 단추를 선택하여 구성 요소 집합을 검색 범위로 정의할 수 있습니다. 설치된 .NET 또는 COM 구성 요소, 솔루션에 포함된 Visual Studio 프로젝트, 혹은 어셈블리나 형식 라이브러리(.dll, .tlb, .olb, .exe 또는 .ocx)를 지정할 수 있습니다. 참조를 검색하려면 **참조에서 찾기** 상자를 선택합니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)

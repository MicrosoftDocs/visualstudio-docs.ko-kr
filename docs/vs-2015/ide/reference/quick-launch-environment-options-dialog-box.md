---
title: 빠른 실행, 환경, 옵션 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.QuickLaunch
- vs.quicklaunch
helpviewer_keywords:
- searching IDE
- IDE, searching
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: abd8f8e9ee35c234a79af74199b11d5491e6fbee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851631"
---
# <a name="quick-launch-environment-options-dialog-box"></a>옵션 대화 상자, 환경, 빠른 실행
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**빠른 실행**을 사용하면 옵션, 템플릿, 메뉴 등의 IDE 자산에 대해 신속하게 검색하고 동작을 실행할 수 있습니다. 코드 및 기호를 검색하는 데는 **빠른 실행**을 사용할 수 없습니다. **빠른 실행** 검색 상자는 메뉴 모음의 오른쪽 위 모서리에 있으며 Ctrl+Q 키를 선택하여 액세스할 수 있습니다. 간단히 상자에 검색 문자열을 입력합니다. @ 이 포함된 문자열을 검색하려면 ”@@” 을 사용합니다.

 **빠른 실행**은 Visual Studio를 설치하면 기본적으로 활성화됩니다. 메뉴 모음에서 **도구**, **옵션**을 선택하여 **빠른 실행**을 표시하거나 숨길 수 있습니다. **환경** 노드를 확장한 다음 **빠른 실행**을 선택합니다. **빠른 실행 사용** 확인란을 선택하거나 선택 취소합니다. 이 페이지에서 검색 범주를 사용하거나 사용하지 않도록 설정할 수도 있습니다.

## <a name="category-list"></a>범주 목록
 빠른 실행 검색 결과는 다음 네 가지 범주로 나타납니다. **가장 최근에 사용됨**, **메뉴**, **옵션** 및 **문서 열기** 등 범주의 항목 수와 함께 나타납니다. 범주별로 검색 결과를 트래버스하려면 Ctrl+Q를 선택하여 다음 범주의 모든 결과를 표시합니다. 마지막 범주가 나타난 후에는 Ctrl+Q를 누르면 각 범주의 몇몇 결과가 표시됩니다. Ctrl+Shift+Q를 사용하면 범주를 역순으로 탐색할 수 있습니다. 범주 아래의 모든 검색 결과를 보려면 범주 이름을 선택합니다.

 다음 바로 가기 키를 사용하여 검색을 특정 범주로 제한할 수 있습니다.

|범주|바로 가기|바로 가기 설명|
|--------------|--------------|--------------------------|
|가장 최근에 사용됨|@mru<br /><br /> 예를 들면 `@mru font`과 같습니다.|**가장 최근에 사용됨** 범주의 항목을 최대 5개까지 표시합니다.|
|메뉴|@menu<br /><br /> 예를 들면 `@menu font`과 같습니다.|검색을 메뉴 항목으로 제한합니다.|
|옵션|@opt<br /><br /> 예를 들면 `@opt font`과 같습니다.|검색을 **옵션** 대화 상자의 설정으로 제한합니다.|
|문서|@doc<br /><br /> 예를 들면 `@doc font`과 같습니다.|열린 문서에 대해 검색 조건에 맞는 파일 이름 및 경로로 검색을 제한합니다. 그러나 파일 자체 내부의 텍스트는 검색하지 않습니다.|

> [!NOTE]
> **옵션** 대화 상자에 있는 **키보드** 페이지의 **일반**에서 바로 가기 키를 변경할 수 있습니다.

## <a name="show-previous-results"></a>이전 결과 표시
 기본적으로 입력하는 검색어는 검색 세션 간에 지속되지 않습니다. 용어를 검색하고 **빠른 실행** 영역 바깥으로 커서를 움직인 후 다시 돌아가면 검색 문자열이 지워집니다. 검색 결과를 유지하려면 **옵션** 대화 상자로 이동하고 **빠른 실행**을 선택한 다음 **빠른 실행을 활성화하면 이전 검색의 검색 결과 표시** 확인란을 선택합니다. 다음에 검색하고 빠른 실행 영역을 종료했다가 돌아오면 빠른 실행에서 마지막으로 사용된 검색어를 보유하고 검색 결과도 표시합니다.

 **빠른 실행** 사용과 관련한 가장 최근의 팁과 요령을 보려면 [Visual Studio 블로그](https://blogs.msdn.com/b/visualstudio/)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [일반 사용자 인터페이스 요소 (Visual Studio)](../../ide/reference/general-user-interface-elements-visual-studio.md) [환경 옵션 대화 상자](../../ide/reference/environment-options-dialog-box.md)

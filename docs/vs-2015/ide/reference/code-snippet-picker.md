---
title: 코드 조각 선택 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2918826d6923efa3db42f4f572c416b9668513a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660893"
---
# <a name="code-snippet-picker"></a>코드 조각 선택
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 코드 편집기는 사용자가 몇 번의 마우스 클릭으로 현재 문서에 미리 만들어진 코드 블록을 삽입할 수 있는 **코드 조각 선택**을 제공합니다.

 **코드 조각 선택**을 표시하는 프로시저는 사용 중인 언어에 따라 달라집니다.

- [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] - 코드 편집기에서 원하는 위치를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 표시하고 **조각 삽입**을 선택합니다.

- [!INCLUDE[csprcs](../../includes/csprcs-md.md)] -코드 편집기에서 원하는 위치를 마우스 오른쪽 단추로 클릭 하 여 바로 가기 메뉴를 표시 하 고 **조각 삽입** 또는 코드 **감싸기**를 클릭 합니다.

- [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] - **코드 조각 선택**을 사용할 수 없습니다.

- Visual F# - **코드 조각 선택**을 사용할 수 없습니다.

- [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] - 코드 편집기에서 원하는 위치를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 표시하고 **조각 삽입** 또는 **코드 감싸기**를 클릭합니다.

- XML - 코드 편집기에서 원하는 위치를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 표시하고 **조각 삽입** 또는 **코드 감싸기**를 클릭합니다.

- HTML - 코드 편집기에서 원하는 위치를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 표시하고 **조각 삽입** 또는 **코드 감싸기**를 클릭합니다.

- SQL - 코드 편집기에서 원하는 위치를 마우스 오른쪽 단추로 클릭하여 바로 가기 메뉴를 표시하고 **조각 삽입**을 클릭합니다.

  대부분의 Visual Studio 개발 언어에서 **코드 조각 관리자**를 사용하여 **코드 조각 선택**이 XML 코드 조각 파일을 검사하는 **폴더 목록**에 폴더를 추가할 수 있습니다. 또한 사용자 고유의 조각을 만들어 목록에 추가할 수 있습니다. 자세한 내용은 [연습: 코드 조각 만들기](../../ide/walkthrough-creating-a-code-snippet.md)를 참조 하세요.

## <a name="uielement-list"></a>UIElement 목록
 항목 이름 **항목 목록**에서 선택한 항목의 이름을 표시 하는 편집 가능한 텍스트 필드입니다. 원하는 항목에 대한 증분 검색을 수행하려면 이 필드에 해당 이름을 입력하기 시작합니다. **항목 목록**에서 원하는 항목이 선택될 때까지 문자를 계속 추가합니다.

 항목 목록 삽입할 수 있는 코드 조각 목록 또는 코드 조각을 포함 하는 폴더 목록입니다. 코드 조각을 삽입하거나 폴더를 확장하려면 원하는 항목을 선택하고 Enter 키를 누릅니다.

## <a name="see-also"></a>관련 항목
 [코드 조각을 사용 하는 방법에 대 한 유용한 정보](../../ide/best-practices-for-using-code-snippets.md) [IntelliSense 코드 조각 Visual Basic](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643) [코드에 책갈피 설정](../../ide/setting-bookmarks-in-code.md) [방법: 코드 감싸기 코드 조각 사용](../../ide/how-to-use-surround-with-code-snippets.md)

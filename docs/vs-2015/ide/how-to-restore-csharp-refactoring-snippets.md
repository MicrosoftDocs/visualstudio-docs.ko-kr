---
title: '방법: C# 리팩터링 코드 조각 복원 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ae3f1d74a482192d3782aaa87baa816694abcf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670794"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>방법: C# 리팩터링 코드 조각 복원
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C# 리팩터링 작업은 다음 디렉터리에 있는 코드 조각을 사용합니다.

 *Installation directory*\Microsoft Visual Studio 14.0\VC#\Snippets\\*language ID*\Refactoring

 이 Refactoring 디렉터리나 이 디렉터리의 파일이 삭제되거나 손상되면 C# 리팩터링 작업이 IDE에서 작동하지 않을 수 있습니다. 다음 절차를 통해 C# 리팩터링 코드 조각을 복원할 수 있습니다.

### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>코드 조각 관리자를 통해 C# 리팩터링 코드 조각을 사용할 수 있는지 확인하려면

1. **도구** 메뉴에서 **코드 조각 관리자**를 선택합니다.

2. **코드 조각 관리자** 대화 상자의 **언어** 드롭다운 목록에서 **Visual C#** 을 선택합니다.

     **Refactoring** 폴더가 트리 뷰 폴더 목록에 표시되어야 합니다.

### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>리팩터링을 복원하려면 코드 조각 관리자에서 주석 참조

1. **Refactoring** 폴더가 코드 조각 관리자의 트리 뷰 폴더 목록에 나타나지 않으면 이 절차에 따라 리팩터링 조각을 다시 코드 조각 관리자에 추가하세요.

2. **도구** 메뉴에서 **코드 조각 관리자**를 선택합니다.

3. **코드 조각 관리자** 대화 상자의 **언어** 드롭다운 목록에서 **Visual C#** 을 선택합니다.

4. **추가**를 클릭합니다. 코드 조각 관리자에 다시 추가할 디렉터리를 찾아서 지정하도록 도와주는 **코드 조각 디렉터리** 대화 상자가 표시됩니다.

5. 다음 디렉터리 경로에서 **Refactoring** 폴더를 찾습니다.

     *Installation directory*\Microsoft Visual Studio 14.0\VC#\Snippets\\*language ID*\Refactoring

     기본 설치에 대한 실제 경로는 다음과 비슷합니다.

     C:\Program Files\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.

6. **코드 조각 디렉터리** 대화 상자에서 **열기**를 클릭하고 코드 조각 관리자에서 **확인**을 클릭합니다.

## <a name="see-also"></a>관련 항목
 [Visual c # 코드 조각](../ide/visual-csharp-code-snippets.md) [리팩터링 (c #)](../csharp-ide/refactoring-csharp.md) [코드 조각](../ide/code-snippets.md)

---
title: 단위 테스트 프로젝트 만들기 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: a608bfba-1a43-4a60-b73a-1fe53ef58098
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfc85b0616fdf8f30732f2409a1a15040967dbb3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660646"
---
# <a name="create-a-unit-test-project"></a>단위 테스트 프로젝트 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

단위 테스트는 종종 테스트 중인 코드의 구조를 반영합니다. 예를 들어 프로젝트의 각 코드 프로젝트에 대해 단위 테스트 프로젝트를 만들 수 있습니다. 테스트 프로젝트는 프로덕션 코드와 동일한 솔루션에 있거나 개별 솔루션에 있을 수 있습니다. 한 솔루션에 여러 개의 테스트 프로젝트를 포함할 수 있습니다.

> [!NOTE]
> 네이티브 코드의 유닛 테스트 위치와 테스트 프로젝트 구조는 이 항목에서 설명하는 구조와 다를 수 있습니다. 자세한 내용은 [기존 C++ 애플리케이션에 단위 테스트 추가](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)를 참조하세요.

## <a name="to-create-a-unit-test-project"></a>단위 테스트 프로젝트를 만들려면:

1. **파일** 메뉴에서 **새로 만들기** 를 선택한 후 **프로젝트** 를 선택합니다(키보드 Ctrl+Shift+N).

2. 새 프로젝트 대화 상자에서 **설치됨** 노드를 확장하고 테스트 프로젝트에 사용하려는 언어를 선택한 후 **테스트**를 선택합니다.

3. Microsoft 단위 테스트 프레임워크 중 하나를 사용하려면 프로젝트 템플릿 목록에서 **단위 테스트 프로젝트** 를 선택합니다. 그렇지 않으면 사용하려는 단위 테스트 프레임워크의 프로젝트 템플릿을 선택합니다. 이 예제의 Accounts 프로젝트를 테스트하기 위해 프로젝트 이름을 AccountsTests로 지정합니다.

4. 단위 테스트 프로젝트에서 테스트 중인 코드에 대한 참조를 추가합니다.  동일한 솔루션에서 코드 프로젝트에 대한 참조를 만드는 방법은 다음과 같습니다.

    1. 솔루션 탐색기에서 프로젝트를 선택합니다.

    2. **프로젝트** 메뉴에서 **참조 추가**를 선택합니다.

    3. 참조 관리자 대화 상자에서 **솔루션** 노드를 열고 **프로젝트**를 선택합니다. 코드 프로젝트 이름을 선택하고 대화 상자를 닫습니다.

5. 테스트하려는 코드가 다른 위치에 있는 경우 참조 추가에 대한 자세한 내용은 [프로젝트의 참조 관리](../ide/managing-references-in-a-project.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계
 **단위 테스트 작성**

 다음 섹션 중 하나를 참조하십시오.

- [관리 코드용 Microsoft 단위 테스트 프레임워크를 사용하여 .NET Framework용 단위 테스트 작성](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

- [C++용 Microsoft 유닛 테스트 프레임워크를 사용하여 C/C++용 유닛 테스트 작성](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)

  **단위 테스트 실행**

  [테스트 탐색기를 사용하여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md)

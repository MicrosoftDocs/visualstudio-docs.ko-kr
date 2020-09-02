---
title: '리팩터링 (c #) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667510"
---
# <a name="refactoring-c"></a>리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

리팩터링은 코드의 외부 동작을 변경 하지 않고 코드의 내부 구조를 변경 하 여 코드를 작성 한 후 코드를 개선 하는 프로세스입니다.

 Visual c #에서는 **리팩터링** 메뉴에서 다음 리팩터링 명령을 제공 합니다.

- [메서드 추출 리팩터링(C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [이름 바꾸기 리팩터링(C#)](../csharp-ide/rename-refactoring-csharp.md)

- [필드 캡슐화 리팩터링(C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [인터페이스 추출 리팩터링(C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [매개 변수 제거 리팩터링(C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [매개 변수 다시 정렬 리팩터링(C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>다중 프로젝트 리팩터링
 Visual Studio는 동일한 솔루션에 있는 프로젝트에 대해 다중 프로젝트 리팩터링을 지원 합니다. 여러 파일에 대 한 참조를 수정 하는 모든 리팩터링 작업은 동일한 언어의 모든 프로젝트에서 해당 참조를 수정 합니다. 이는 프로젝트 간 참조에 대해 작동 합니다. 예를 들어 클래스 라이브러리를 참조 하는 콘솔 응용 프로그램이 있는 경우 리팩터링 작업을 사용 하 여 클래스 라이브러리 형식의 이름을 바꾸면 `Rename` 콘솔 응용 프로그램의 클래스 라이브러리 형식에 대 한 참조도 업데이트 됩니다.

## <a name="changes-preview"></a>변경 내용 미리 보기
 많은 리팩터링 작업을 통해 해당 변경 내용을 커밋하기 전에 리팩터링 작업이 코드에서 수행 하는 모든 참조 변경 내용을 검토할 수 있습니다. 이러한 리팩터링 작업의 경우 리팩터링 대화 상자에 **참조 변경 내용 미리 보기** 옵션이 표시 됩니다. 이 옵션을 선택 하 고 리팩터링 작업을 수락 하면 **변경 내용 미리 보기 대화 상자가** 표시 됩니다. **변경 내용 미리 보기** 대화 상자에는 두 가지 보기가 있습니다. 아래쪽 보기에는 리팩터링 작업으로 인해 모든 참조 업데이트와 함께 코드가 표시 됩니다. **변경 내용 미리 보기** 대화 상자에서 **취소** 를 누르면 리팩터링 작업이 중단 되 고 코드에 변경 내용이 적용 되지 않습니다.

## <a name="refactoring-warnings"></a>리팩터링 경고
 컴파일러에 프로그램에 대 한 완전 한 이해가 없는 경우 리팩터링 엔진이 적절 한 참조를 모두 업데이트 하지 못할 수 있는 경우 경고 대화 상자가 표시 됩니다. 또한이 경고 대화 상자는 변경 내용을 커밋하기 전에 **변경 내용 미리 보기** 대화 상자에서 코드를 미리 볼 수 있는 기회를 제공 합니다.

> [!NOTE]
> 메서드에 구문 오류 (IDE에서 빨간색 물결선 밑줄로 표시 됨)가 포함 된 경우 리팩터링 엔진은 해당 메서드 내의 요소에 대 한 참조를 업데이트 하지 않습니다. 아래 예제에서는이 동작을 보여 줍니다.

 기본적으로 참조 변경 내용 미리 보기 없이 리팩터링 작업을 실행 하 고 프로그램에서 컴파일 오류가 검색 되는 경우 개발 환경에서이 경고 대화 상자를 표시 합니다.

 **미리 보기 참조 변경 내용이** 설정 된 리팩터링 작업을 실행 하 고 프로그램에서 컴파일 오류가 검색 되는 경우 개발 환경에서는 **리팩터링 경고** 대화 상자를 표시 하는 대신 **변경 내용 미리 보기** 대화 상자 아래쪽에 다음과 같은 경고 메시지가 표시 됩니다.

 **프로젝트 또는 해당 종속성 중 하나가 현재 빌드되지 않습니다. 참조를 업데이트할 수 없습니다.**

 이 리팩터링 경고는 **미리 보기 참조 변경 내용** 옵션을 제공 하는 리팩터링 작업에만 사용할 수 있습니다.

## <a name="error-tolerant-refactoring-and-verification-results"></a>오류 허용 리팩터링 및 확인 결과
 리팩터링은 오류를 허용 합니다. 즉, 빌드할 수 없는 프로젝트에서 리팩터링을 수행할 수 있습니다. 그러나 이러한 경우에는 리팩터링 프로세스가 모호한 참조를 올바르게 업데이트 하지 못할 수 있습니다.

 **확인 결과** 대화 상자는 리팩터링 엔진이 컴파일 오류를 검색 하거나 리팩터링 작업으로 인해 코드 참조가 원래 바인딩된 것과 다른 항목 (리바인딩 문제)에 바인딩하려는 것을 발견 하는 경우 사용자에 게 알릴 수 있습니다.

 확인 결과 기능을 설정 하려면 **도구** 메뉴에서 **옵션**을 클릭 합니다. **옵션** 대화 상자에서 **텍스트 편집기**를 확장 한 다음 **c #** 을 확장 합니다. **고급** 을 클릭 하 고 **리팩터링 결과 확인** 확인란을 선택 합니다.

 **확인 결과** 대화 상자는 두 종류의 리바인딩 문제 간의 차이를 구분 합니다.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>정의가 더 이상 이름을 바꾼 기호가 아닌 참조입니다.
 이러한 종류의 리바인딩 문제는 참조가 더 이상 이름이 바뀐 기호를 참조 하지 않는 경우에 발생 합니다. 예를 들어, 다음 코드를 고려하세요.

```csharp
class Example
{
    private int a;
    public Example(int b)
    {
        a = b;
    }
}
```

 리팩터링을 사용 하 여의 이름을 `a` 로 바꾸면 `b` 이 대화 상자가 나타납니다. 이름을 바꾼 변수에 대 한 참조는 `a` 이제 필드에 바인딩하지 않고 생성자에 전달 되는 매개 변수에 바인딩됩니다.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>이제 정의가 이름이 변경 된 기호로 포함 된 참조가 됩니다.
 이러한 종류의 리바인딩 문제는 이전에 이름이 바뀐 기호를 참조 하지 않은 경우에는 이름이 바뀐 기호를 참조 하는 경우에 발생 합니다. 예를 들어, 다음 코드를 고려하세요.

```csharp
class Example
{
    private static void Method(object a) { }
    private static void OtherMethod(int a) { }
    static void Main(string[] args)
    {
        Method(5);
    }
}
```

 리팩터링을 사용 하 여의 이름을 `OtherMethod` 로 바꾸면 `Method` 이 대화 상자가 나타납니다. 이제의 참조는 `Main` `int` 매개 변수를 허용 하는 오버 로드 된 메서드 대신 매개 변수를 허용 하는 오버 로드 된 메서드를 참조 합니다 `object` .

## <a name="see-also"></a>관련 항목
 [C # 용 Visual Studio 개발 환경 사용](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [방법: c # 리팩터링 코드 조각 복원](../ide/how-to-restore-csharp-refactoring-snippets.md)
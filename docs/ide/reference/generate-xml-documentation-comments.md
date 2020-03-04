---
title: XML 문서 주석 삽입
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706398"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>방법: 문서 생성에 대한 XML 주석 삽입

Visual Studio는 표준 XML 문서 주석 구조를 자동으로 생성하여 클래스와 메서드 같은 코드 요소의 문서화에 도움이 될 수 있습니다. 컴파일 타임에 문서 주석이 포함된 XMl 파일을 생성할 수 있습니다.

> [!TIP]
> 생성된 XML 파일의 이름 및 위치 구성에 대한 자세한 내용은 [XML 주석을 사용하여 코드 문서화(C# 가이드)](/dotnet/csharp/codedoc)를 참조하세요.

Visual Studio 및 기타 IDE가 IntelliSense를 사용하여 형식 및 멤버에 대한 빠른 정보를 표시할 수 있도록 컴파일러에서 생성된 XML 파일은 .NET 어셈블리와 함께 배포될 수 있습니다. 또한 [DocFX](https://dotnet.github.io/docfx/) 및 [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) 같은 도구를 통해 XML 파일을 실행하여 API 참조 웹 사이트를 생성할 수 있습니다.

> [!NOTE]
> XML 문서 주석을 자동으로 삽입하는 **주석 삽입** 명령은 [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) 및 [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)에서 사용할 수 있습니다. 그러나 수동으로 [C++ 파일에 XML 문서 주석을 삽입](/cpp/build/reference/xml-documentation-visual-cpp)할 수 있으며 컴파일 타임에도 XML 문서 파일을 생성할 수 있습니다.

## <a name="to-insert-xml-comments-for-a-code-element"></a>코드 요소에 대한 XML 주석을 삽입하려면

1. 문서화할 요소(예: 메서드) 위에 텍스트 커서를 놓습니다.

2. 다음 작업 중 하나를 수행합니다.

   - C#에서 `///` 또는 Visual Basic에서 `'''`를 입력

   - **편집** 메뉴에서 **IntelliSense** > **주석 삽입**을 선택

   - 마우스 오른쪽 단추 클릭 또는 컨텍스트 메뉴 또는 단지 코드 요소 위에서 **코드 조각** > **주석 삽입**을 선택

   XML 템플릿은 코드 요소 위에 즉시 생성됩니다. 예를 들어 메서드를 주석화할 때 **\<summary\>** 요소, 각 매개 변수에 대한 **\<param\>** 요소 및 반환 값을 문서화하기 위한 **\<returns\>** 요소를 생성합니다.

   ![XML 주석 템플릿 - C#](media/doc-preview-cs.png)

   ![XML 주석 템플릿 - Visual Basic](media/doc-preview-vb.png)

3. 각 XML 요소에 대한 설명을 입력하여 코드 요소를 완전히 문서화합니다.

   ![완료된 주석](media/doc-result-cs.png)

요소를 마우스로 가리킬 때 요약 정보로 렌더링되는 XML 주석에 스타일을 사용할 수 있습니다. 이러한 스타일에는 기울임꼴, 굵게, 글머리 기호 및 클릭 가능한 링크 등이 있습니다.

   ![완료된 주석](media/doc-style-cs.png) 

> [!NOTE]
> C#에서 `///` 또는 Visual Basic에서 `'''`를 입력한 후 XML 문서 주석을 설정/해제하는 [옵션](../../ide/reference/options-text-editor-csharp-advanced.md)이 있습니다. 메뉴 모음에서 **도구** > **옵션**을 선택하여 **옵션** 대화 상자를 엽니다. 그런 다음, **텍스트 편집기** > **C#** 또는 **기본** > **고급**으로 이동합니다. **편집기 도움말** 섹션에서 **XML 문서 주석 생성** 옵션을 찾습니다.

## <a name="see-also"></a>참조

- [XML 문서 주석(C# 프로그래밍 가이드)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [XML 주석과 함께 코드 문서화(C# 가이드)](/dotnet/csharp/codedoc)
- [방법: XML 문서 만들기(Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ 주석](/cpp/cpp/comments-cpp)
- [XML 문서(C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [코드 생성](../code-generation-in-visual-studio.md)

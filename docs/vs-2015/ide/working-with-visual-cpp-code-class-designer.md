---
title: Visual C++ 코드 사용(클래스 디자이너) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 020535ac73c48be74e56100c7b6f9c49b69e50dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851308"
---
# <a name="working-with-visual-c-code-class-designer"></a>Visual C++ 코드 사용(클래스 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

클래스 디자이너에는 프로젝트의 코드 요소를 시각적으로 나타내 주는 *클래스 다이어그램*이라는 시각적 디자인 화면이 표시됩니다. 클래스 다이어그램을 사용하여 프로젝트의 클래스 및 기타 형식을 디자인하고 시각화할 수 있습니다.

 클래스 디자이너에서 지원되는 C++ 코드 요소는 다음과 같습니다.

- 클래스(상속 관계가 여러 개 있을 수 있다는 점을 제외하고는 관리되는 클래스의 모양과 비슷함)

- 익명 클래스(익명 형식에 대해 클래스 뷰에서 생성된 이름이 표시됨)

- 템플릿 클래스

- 구조체

- 열거형

- 매크로(후처리된 매크로 뷰가 표시됨)

- 형식 정의

> [!NOTE]
> 이 UML 클래스 다이어그램에서 모델링 프로젝트를 만들 수 있습니다 수 없습니다. 자세한 내용은 [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)를 참조하세요.

## <a name="troubleshooting-type-resolution-and-display-issues"></a>형식 확인 및 표시 문제 해결

### <a name="location-of-source-files"></a>소스 파일의 위치
 클래스 디자이너에서는 소스 파일의 위치를 추적하지 않습니다. 따라서 프로젝트 구조를 수정하거나 프로젝트의 소스 파일을 이동하면 특히 형식 정의, 기본 클래스 또는 형식 연결의 소스 형식에 대해 클래스 디자이너에서 해당 형식을 추적할 수 없게 됩니다. **클래스 디자이너에서 이 형식을 표시할 수 없습니다.** 와 같은 오류가 발생할 수 있습니다. 이러한 오류가 발생하면 수정되거나 위치가 변경된 소스 코드를 클래스 다이어그램으로 끌어서 다시 표시합니다.

### <a name="update-and-performance-issues"></a>업데이트 및 성능 문제
 Visual C++ 프로젝트의 경우 소스 파일의 변경 내용이 클래스 다이어그램에 나타나는 데는 30~60초가 소요될 수 있습니다. 이 시간 지연으로 인해 클래스 디자이너에서 **선택한 항목에서 형식을 찾을 수 없습니다**라는 오류를 throw할 수도 있습니다. 이와 같은 오류가 발생 하면 오류 메시지에서 **취소** 를 클릭 하 고 클래스 뷰에 코드 요소가 나타날 때까지 기다립니다. 그런 후에 클래스 디자이너에서 해당 형식이 표시될 수 있습니다.

 코드에서 변경한 내용으로 클래스 다이어그램이 업데이트되지 않으면 다이어그램을 닫았다가 다시 열어 보세요.

### <a name="type-resolution-issues"></a>형식 확인 문제
 클래스 디자이너에서는 다음과 같은 경우에 형식을 확인할 수 없습니다.

- 클래스 다이어그램이 속한 프로젝트에서 참조되지 않는 프로젝트나 어셈블리에 형식이 있습니다. 이 오류를 수정하려면 해당 형식을 포함하는 프로젝트나 어셈블리에 대한 참조를 추가합니다. 자세한 내용은 [NIB 방법: 참조 추가 대화 상자를 사용하여 참조 추가 또는 제거](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)를 참조하세요.

- 형식이 올바른 범위에 있지 않아 클래스 디자이너에서 해당 형식을 찾을 수 없습니다. 이 경우 코드에 `using`, `imports` 또는 `#include` 문이 누락되지 않았는지 확인합니다. 또한 해당 형식이나 관련 형식을 원래 있던 네임스페이스 밖으로 이동하지 않았는지 확인합니다.

- 형식이 존재하지 않거나 주석 처리되었습니다. 이 오류를 해결하려면 해당 형식을 주석으로 처리하거나 삭제하지 않았는지 확인합니다.

- 형식은 #import 지시문을 사용하여 참조되는 라이브러리에 있습니다. 가능한 해결 방법은 생성된 코드(.tlh 파일)를 헤더 파일에 대한 #include 지시문에 수동으로 추가하는 것입니다.

  형식 확인 문제에 대해 가장 많이 발생 하는 오류는 **클래스 다이어그램 ' \<element> '에서 하나 이상의 모양에 대 한 코드를 찾을**수 없는 경우입니다. 이 오류 메시지가 반드시 코드에 오류가 있음을 나타내지 않습니다. 클래스 디자이너는 코드를 표시할 수 없습니다 것을 나타냅니다. 다음과 같은 방법을 시도해 보세요.

- 해당 형식이 존재하는지 확인합니다. 실수로 주석으로 처리했거나 소스 코드를 삭제했는지 확인합니다.

- 입력한 형식이 클래스 디자이너에서 지원되는지 확인합니다. [C++ 코드 요소에 대한 제한 사항](#limitations)을 참조하세요.

- 형식을 확인해 보세요. 프로젝트 또는 클래스 다이어그램이 속한 프로젝트에서 참조되지 않는 어셈블리 형식이 있을 수 있습니다. 이 오류를 수정하려면 해당 형식을 포함하는 프로젝트나 어셈블리에 대한 참조를 추가합니다. 자세한 내용은 [NIB 방법: 참조 추가 대화 상자를 사용하여 참조 추가 또는 제거](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)를 참조하세요.

- 클래스 디자이너에서 찾을 수 있도록 형식이 올바른 범위에 있는지 확인하세요. 이 경우 코드에 `using`, `imports` 또는 `#include` 문이 누락되지 않았는지 확인합니다. 또한 해당 형식이나 관련 형식을 원래 있던 네임스페이스 밖으로 이동하지 않았는지 확인합니다.

### <a name="troubleshooting-other-error-messages"></a>기타 오류 메시지 문제 해결
 MSDN(Microsoft Developer Network) 공개 포럼에서 오류 및 경고 문제 해결 관련 지원 정보를 찾을 수 있습니다. [Visual Studio Class Designer Forum](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1)(Visual Studio 클래스 디자이너 포럼)을 참조하세요.

## <a name="limitations-for-c-code-elements"></a><a name="limitations"></a> C + + 코드 요소에 대 한 제한 사항

- Visual C++ 프로젝트가 로드되면 클래스 디자이너는 읽기 전용 방식으로 작동합니다. 즉, 클래스 다이어그램을 변경할 수 있지만 클래스 다이어그램에서 변경한 내용을 소스 코드에 저장할 수는 없습니다.

- 클래스 디자이너에서는 네이티브 C++ 의미 체계만 지원됩니다. 관리 코드로 컴파일된 Visual C++ 프로젝트의 경우 클래스 디자이너에는 네이티브 형식인 코드 요소만 시각화됩니다. 따라서 프로젝트에 클래스 다이어그램을 추가할 수는 있지만 `IsManaged` 속성이 `true`로 설정된 요소, 즉 값 형식과 참조 형식은 클래스 디자이너에 시각화되지 않습니다.

- Visual C++ 프로젝트의 경우 클래스 디자이너에서는 형식의 정의만 읽습니다. 예를 들어 헤더 파일(.h)에 형식을 정의하고 해당 멤버는 구현 파일(.cpp)에 정의할 경우, 구현 파일(.cpp)에서 "클래스 다이어그램 보기"를 호출하면 클래스 디자이너에 아무 것도 표시되지 않습니다. 또 다른 예로, `#include` 문을 사용하여 다른 파일을 포함하지만 실제 클래스 정의는 포함하지 않는 .cpp 파일에서 "클래스 다이어그램 보기"를 호출할 경우에도 클래스 디자이너에 아무 것도 표시되지 않습니다.

- COM 인터페이스와 형식 라이브러리를 정의하는 IDL 파일(.idl)은 네이티브 C++ 코드로 컴파일되기 전까지는 다이어그램에 표시되지 않습니다.

- 클래스 디자이너에서는 전역 함수 및 변수가 지원되지 않습니다.

- 클래스 디자이너에서는 공용 구조체가 지원되지 않습니다. 공용 구조체는 해당 데이터 멤버 중 가장 큰 데이터 멤버에 필요한 만큼만 메모리가 할당되는 특수한 클래스 형식입니다.

- 클래스 디자이너에서는 `int`, `char` 등의 기본 데이터 형식이 표시되지 않습니다.

- 클래스 디자이너에서는 현재 프로젝트에 프로젝트 외부에 정의된 형식에 대한 올바른 참조가 없을 경우 해당 형식이 표시되지 않습니다.

- 클래스 디자이너에서 중첩된 형식을 표시할 수는 있지만 중첩된 형식과 기타 형식 사이의 관계는 표시할 수 없습니다.

- 클래스 디자이너에서는 void 형식이거나 void 형식에서 파생된 형식을 표시할 수 없습니다.

## <a name="see-also"></a>관련 항목
 클래스 및 [형식 디자인 및 보기](../ide/designing-and-viewing-classes-and-types.md) 클래스 및 [기타 형식 작업 (클래스 디자이너) 클래스](../ide/working-with-classes-and-other-types-class-designer.md) [다이어그램 작업 (클래스 디자이너) 클래스 다이어그램 사용](../ide/working-with-class-diagrams-class-designer.md) (클래스 디자이너 [클래스 디자이너](../ide/additional-information-about-class-designer-errors.md) [) 클래스 및 형식 디자인](../ide/designing-classes-and-types-class-designer.md) Visual C++ 클래스 디자이너 Visual C++ [구조체](../ide/visual-cpp-structures-in-class-designer.md) 의 [클래스](../ide/visual-cpp-classes-in-class-designer.md) 클래스 디자이너 Visual C++ 클래스 디자이너 [의 Visual C++ 클래스 디자이너](../ide/visual-cpp-typedefs-in-class-designer.md) [열거형](../ide/visual-cpp-enumerations-in-class-designer.md)

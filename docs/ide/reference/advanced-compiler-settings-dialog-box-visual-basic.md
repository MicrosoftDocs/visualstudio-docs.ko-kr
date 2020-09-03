---
title: 고급 컴파일러 설정 대화 상자(Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: TerryGLee
ms.author: ghogen
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0c0e6e9d41bb1d4bd7446bb77306ca5a4551906f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419109"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>고급 컴파일러 설정 대화 상자(Visual Basic)

**프로젝트 디자이너**의 **고급 컴파일러 설정** 대화 상자를 사용하여 프로젝트의 고급 빌드 구성 속성을 지정합니다. 이 대화 상자는 Visual Basic 프로젝트에만 적용됩니다.

## <a name="to-access-this-dialog-box"></a>이 대화 상자에 액세스하려면

1. **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다.

2. **프로젝트** 메뉴에서 **속성**을 클릭합니다. **프로젝트 디자이너**가 나타나면 **컴파일** 탭을 클릭합니다.

3. [프로젝트 디자이너, 컴파일 페이지(Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)에서 **구성** 및 **플랫폼**을 선택합니다. 단순화된 빌드 구성에서 **구성** 및 **플랫폼** 목록이 표시되지 않습니다. 자세한 내용은 [방법: 디버그 및 릴리스 구성 설정](../../debugger/how-to-set-debug-and-release-configurations.md)을 참조하세요.

4. **고급 컴파일 옵션**을 클릭합니다.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>최적화

다음 옵션은 경우에 따라 프로그램 파일을 축소하고, 프로그램을 신속하게 실행하고, 빌드 프로세스를 가속화할 수 있도록 최적화를 지정합니다.

**정수 오버플로 검사 해제**

기본적으로 정수 오버플로 검사를 사용하도록 설정하려면 이 확인란의 선택을 취소합니다. 정수 오버플로 검사를 제거하려면 이 확인란을 선택합니다. 이 확인란을 선택하면 정수 연산을 가속화할 수 있습니다. 그러나 오버플로 검사 및 데이터 형식 용량 오버플로를 제거하면 오류가 발생하지 않고 잘못된 결과가 저장될 수 있습니다.

오버플로 조건을 확인하는 경우 정수 연산 오버플로는 <xref:System.OverflowException> 예외를 throw합니다. 오버플로 조건을 확인하지 않는 경우 정수 작업 오버플로는 예외를 throw하지 않습니다.

**최적화 사용**

기본적으로 컴파일러 최적화를 사용하지 않으려면 이 확인란의 선택을 취소합니다. 이 확인란을 선택하여 컴파일러 최적화를 사용합니다. 컴파일러 최적화를 통해 더 작지만 빠르고 효율적인 출력 파일을 만듭니다. 그러나 최적화를 통해 출력 파일에서 코드 재정렬이 발생하기 때문에 컴파일러 최적화로 인해 디버깅이 어려워질 수 있습니다.

 **DLL 기준 주소**

이 텍스트 상자는 16진수 형식인 기본 DLL 기준 주소를 표시합니다. 클래스 라이브러리 및 컨트롤 라이브러리 프로젝트에서 이 텍스트 상자를 사용하여 DLL을 만들 때 사용되는 기본 주소를 지정할 수 있습니다.

 **디버그 정보 생성**

목록에서 **없음**, **전체** 또는 **PDB 전용**을 선택합니다. **없음**은 디버깅 정보가 생성되지 않도록 지정합니다. **전체**는 전체 디버깅 정보가 생성되도록 지정하고, **PDB 전용**은 PDB 디버깅 정보가 생성되도록 지정합니다. 이 옵션의 기본값은 **전체**입니다.

## <a name="compilation-constants"></a>컴파일 상수

조건부 컴파일 상수를 사용하면 원본 파일에서 [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) 전처리기 지시문을 사용하는 것과 비슷합니다. 단, 정의되는 상수는 공용이며 프로젝트의 모든 파일에 적용된다는 차이점이 있습니다. [#If...Then...#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) 지시문과 함께 조건부 컴파일 상수를 사용하여 조건에 따라 원본 파일을 컴파일할 수 있습니다. [조건부 컴파일](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)을 참조하세요.

 **DEBUG 상수 정의**

기본적으로 이 확인란을 선택하면 DEBUG 상수가 설정되도록 지정합니다.

 **TRACE 상수 정의**

기본적으로 이 확인란을 선택하면 TRACE 상수가 설정되도록 지정합니다.

 **사용자 지정 상수**

이 텍스트 상자에 애플리케이션의 사용자 지정 상수를 입력합니다. 다음 양식을 사용하여 항목을 쉼표로 구분해야 합니다. **Name1="Value1",Name2="Value2",Name3="Value3"** .

## <a name="other-settings"></a>기타 설정

**Serialization 어셈블리 생성**

이 설정은 컴파일러가 XML serialization 어셈블리를 만드는지를 지정합니다. 코드에서 형식을 직렬화하는 데 <xref:System.Xml.Serialization.XmlSerializer> 클래스를 사용한 경우 serialization 어셈블리가 해당 클래스의 시작 성능을 향상할 수 있습니다. 이 옵션의 기본값은 **자동**입니다. **자동**은 코드에서 형식을 XML로 인코딩하는 데 <xref:System.Xml.Serialization.XmlSerializer>를 사용한 경우에만 serialization 어셈블리가 생성되도록 지정합니다. **끄기**는 코드에서 <xref:System.Xml.Serialization.XmlSerializer>를 사용하는지와 관계없이 serialization 어셈블리가 생성되지 않도록 지정합니다. **켜기**는 serialization 어셈블리가 항상 생성되도록 지정합니다. Serialization 어셈블리의 이름은 `TypeName`.XmlSerializers.dll로 지정됩니다.

## <a name="see-also"></a>참조

- [프로젝트 디자이너, 컴파일 페이지(Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)

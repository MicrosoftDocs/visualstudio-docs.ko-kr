---
title: 고급 컴파일러 설정 대화 상자(Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba666b0ff5544b185f82a66c78d6259e9f1268fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651762"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>고급 컴파일러 설정 대화 상자(Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**프로젝트 디자이너**의 **고급 컴파일러 설정** 대화 상자를 사용하여 프로젝트의 고급 빌드 구성 속성을 지정합니다. 이 대화 상자는 Visual Basic 프로젝트에만 적용됩니다.

### <a name="to-access-this-dialog-box"></a>이 대화 상자에 액세스하려면

1. **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다.

2. **프로젝트** 메뉴에서 **속성**을 클릭합니다. **프로젝트 디자이너**가 나타나면 **컴파일** 탭을 클릭합니다.

3. [프로젝트 디자이너, 컴파일 페이지(Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)에서 **구성** 및 **플랫폼**을 선택합니다. 단순화된 빌드 구성에서 **구성** 및 **플랫폼** 목록이 표시되지 않습니다. 자세한 내용은 [디버그 및 릴리스 프로젝트 구성](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)을 참조하세요.

4. **고급 컴파일 옵션**을 클릭합니다.

   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="optimizations"></a>최적화
 다음 옵션은 경우에 따라 프로그램 파일을 축소하고, 프로그램을 신속하게 실행하고, 빌드 프로세스를 가속화할 수 있도록 최적화를 지정합니다.

 **정수 오버플로 검사 제거** 기본적으로 정수 오버플로 검사를 사용 하려면이 확인란의 선택을 취소 합니다. 정수 오버플로 검사를 제거하려면 이 확인란을 선택합니다. 이 확인란을 선택하면 정수 연산을 가속화할 수 있습니다. 그러나 오버플로 검사 및 데이터 형식 용량 오버플로를 제거하면 오류가 발생하지 않고 잘못된 결과가 저장될 수 있습니다.

 오버플로 조건을 확인하는 경우 정수 연산 오버플로는 <xref:System.OverflowException> 예외를 throw합니다. 오버플로 조건을 확인하지 않는 경우 정수 작업 오버플로는 예외를 throw하지 않습니다.

 **최적화 사용** 기본적으로 컴파일러 최적화를 사용 하지 않도록 설정 하려면이 확인란의 선택을 취소 합니다. 이 확인란을 선택하여 컴파일러 최적화를 사용합니다. 컴파일러 최적화를 통해 더 작지만 빠르고 효율적인 출력 파일을 만듭니다. 그러나 최적화를 통해 출력 파일에서 코드 재정렬이 발생하기 때문에 컴파일러 최적화로 인해 디버깅이 어려워질 수 있습니다.

 **DLL 기준 주소** 이 텍스트 상자는 기본 DLL 기준 주소를 16 진수 형식으로 표시 합니다. 클래스 라이브러리 및 컨트롤 라이브러리 프로젝트에서 이 텍스트 상자를 사용하여 DLL을 만들 때 사용되는 기본 주소를 지정할 수 있습니다.

 **디버그 정보 생성** 목록에서 **없음**, **전체**또는 **pdb 전용** 을 선택 합니다. **없음**은 디버깅 정보가 생성되지 않도록 지정합니다. **전체**는 전체 디버깅 정보가 생성되도록 지정하고, **PDB 전용**은 PDB 디버깅 정보가 생성되도록 지정합니다. 기본적으로 이 옵션은 **전체**로 설정되어 있습니다.

## <a name="compilation-constants"></a>컴파일 상수
 조건부 컴파일 상수를 사용하면 원본 파일에서 [#Const](https://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) 전처리기 지시문을 사용하는 것과 비슷합니다. 단, 정의되는 상수는 공용이며 프로젝트의 모든 파일에 적용된다는 차이점이 있습니다. [#If...Then...#Else](https://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) 지시문과 함께 조건부 컴파일 상수를 사용하여 조건에 따라 원본 파일을 컴파일할 수 있습니다. [조건부 컴파일](https://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848)을 참조하세요.

 **DEBUG 상수 정의** 이 확인란은 기본적으로 선택 되어 있으며,이 확인란은 DEBUG 상수를 설정 하도록 지정 합니다.

 **TRACE 상수 정의** 이 확인란은 기본적으로 선택 되어 있으며,이 확인란은 추적 상수가 설정 되도록 지정 합니다.

 **사용자 지정 상수** 이 텍스트 상자에 응용 프로그램에 대 한 사용자 지정 상수를 입력 합니다. **Name1="Value1",Name2="Value2",Name3="Value3"** 양식을 사용하여 항목을 쉼표로 구분해야 합니다.

## <a name="other-settings"></a>기타 설정
 **Serialization 어셈블리 생성** 이 설정은 컴파일러가 XML serialization 어셈블리를 만들지 여부를 지정 합니다. 코드에서 형식을 직렬화하는 데 <xref:System.Xml.Serialization.XmlSerializer> 클래스를 사용한 경우 serialization 어셈블리가 해당 클래스의 시작 성능을 향상할 수 있습니다. 기본적으로 이 옵션은 **자동**으로 설정됩니다. 이 설정은 코드에서 형식을 XML로 인코딩하는 데 <xref:System.Xml.Serialization.XmlSerializer>를 사용한 경우에만 serialization 어셈블리가 생성되도록 지정합니다. **끄기**는 코드에서 <xref:System.Xml.Serialization.XmlSerializer>를 사용하는지와 관계없이 serialization 어셈블리가 생성되지 않도록 지정합니다. **켜기**는 serialization 어셈블리가 항상 생성되도록 지정합니다. Serialization 어셈블리의 이름은 `TypeName`.XmlSerializers.dll로 지정됩니다.

## <a name="see-also"></a>관련 항목
 [프로젝트 디자이너, 컴파일 페이지(Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)

---
title: '워크플로 디자이너-방법: 식 편집기 사용'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04c0fdaab87c88028b8c14ca59e93fa93e74be74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817439"
---
# <a name="how-to-use-the-expression-editor"></a>방법: 식 편집기 사용

식 편집기는 식을 입력 하 고 계산 하기 위해 많은 워크플로 활동에서 사용 되는 워크플로 디자이너 컨트롤입니다. 식 편집기는 IntelliSense, 색 지정, ParamInfo, 오류 물결선 등의 모든 기능을 갖춘 IDE 편집 환경을 제공 합니다. 컴파일러는 입력 된 식의 유효성을 검사 합니다. 식이 잘못된 경우 오류 아이콘이 표시됩니다. 편집기를 **식 편집기** 대화 상자로 열 수도 있습니다.

식이란 인수나 속성에 바인딩된 Visual Basic 코드 또는 리터럴 값입니다. 여기에는 새 값을 생성 하는 작업과 결합 된 값 요소 (예: 변수, 상수, 리터럴, 속성)가 포함 됩니다. 애플리케이션이 C#을 사용하는 프로그램에 있는 경우에도 식은 VB.NET 구문으로 작성됩니다. 즉, 대문자는 중요 하지 않습니다. 단일 등호 ("= =" 대신 "=")를 사용 하 여 비교를 수행 하 고, 부울 연산자는 "&&" 및 "| |" 기호 대신 "and" 및 "or" 단어를 사용 하 고 **null**대신 **아무 것도** 사용 하지 않습니다. Visual Basic의 식 및 연산자에 대 한 자세한 내용 및 일부 샘플은 [Visual Basic의 연산자 및 식](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100))을 참조 하세요.

**식 편집기** 는 다음과 같이 동작 합니다.

- 포커스가 식 편집기에 있지 않을 때는 일반 TextBlock 컨트롤과 비슷하게 보입니다.

- 포커스를 식 편집기에 맞추면 식 편집기 컨트롤처럼 보이고 동작하다가, 포커스를 잃은 후에는 식 편집기가 일반 TextBlock 처럼 보입니다.

- 다시 호스트된 Workflow Designer의 식 편집기에 포커스를 맞추면 TextBox처럼 동작하고, 다시 호스트된 워크플로 디자이너에서 포커스를 옮기면 식 편집기가 다시 일반 TextBlock처럼 보입니다.

> [!NOTE]
> 식 편집기에 대 한 IntelliSense는 Visual Studio 내부 에서만 사용할 수 있습니다. Visual Studio와 다시 호스팅된 시나리오에서 컴파일러는 입력 된 식의 유효성을 검사 하 고 식이 잘못 된 경우 식 편집기에서 오류 아이콘을 표시 합니다.

## <a name="use-the-expression-editor"></a>식 편집기 사용

1. Visual Studio에서 기존 또는 새 워크플로 프로젝트를 엽니다.

2. 예를 들어 <xref:System.Activities.Statements.Assign> 활동을 워크플로에 추가합니다.

    > [!NOTE]
    > 여러 가지 워크플로 활동에 식 편집기가 있습니다. 식 TextBlock은 변수 디자이너, 인수 디자이너 및 동적 인수 디자이너에도 나타납니다. 예제에서는 <xref:System.Activities.Statements.Assign> 활동을 사용합니다.

3. <xref:System.Activities.Statements.Assign> 활동의 활동 디자이너에서 왼쪽 식 편집기를 클릭합니다.

     회색 워터 마크 문자열 **\<To>** 및 **\<Enter a VB Expression>** 는 활동의 식 편집기에 대 한 기본 텍스트 문자열입니다 <xref:System.Activities.Statements.Assign> .

4. 식을 입력합니다. 문자열을 입력할 경우 문자열 앞뒤에 물음표를 붙여야 합니다. 식 인수를 변수에 바인딩하려면 물음표를 제거합니다.

     완료 되 면 식 편집기 외부에서 영역 또는 영역을 선택 하 여 디자이너의 다른 부분으로 포커스를 이동 합니다. 포커스를 이동 하면 컴파일러가 앞에서 설명한 대로 식의 유효성을 검사 합니다.

     식을 입력 하거나 편집 하는 다른 방법은 속성 표에서 속성 이름 옆에 있는 줄임표를 클릭 하는 것입니다. 줄임표를 선택 하면 **식 편집기** 가 대화 상자로 열립니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Activities.Presentation.View.ExpressionTextBox>

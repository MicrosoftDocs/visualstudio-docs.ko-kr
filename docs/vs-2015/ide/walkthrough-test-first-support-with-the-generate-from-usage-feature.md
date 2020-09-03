---
title: '연습: 관례에서 생성 기능을 통한 테스트 우선 지원 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Generate From Usage
- Test-First Development
ms.assetid: 764c17a4-cd95-4c23-bf63-d92d9c5adfb2
caps.latest.revision: 68
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f40ed5f3070f177d1c914495f78a223364d64ae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662670"
---
# <a name="walkthrough-test-first-support-with-the-generate-from-usage-feature"></a>연습: 관례에서 생성 기능을 통한 테스트 우선 지원
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 테스트 우선 개발을 지원하는 [관례에서 생성](../misc/generate-from-usage.md) 기능을 사용하는 방법을 보여 줍니다.

 *테스트 우선 개발* 은 먼저 제품 사양에 따라 단위 테스트를 작성한 다음 테스트에 성공하는 데 필요한 소스 코드를 작성하는 소프트웨어 디자인 방식입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 는 정의하기 전에 테스트 사례에서 처음 참조할 때 소스 코드에서 새 형식과 멤버를 생성하여 테스트 우선 개발을 지원합니다.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 는 워크플로를 중단을 최소화하면서 새 형식과 멤버를 생성합니다. 코드에서 현재 위치를 벗어나지 않고 형식, 메서드, 속성, 필드 또는 생성자에 대한 스텁을 만들 수 있습니다. 형식 생성 옵션을 지정할 수 있는 대화 상자를 여는 경우 대화 상자를 닫으면 포커스가 즉시 현재 열린 파일로 돌아갑니다.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]와 통합된 테스트 프레임워크와 함께 사용법에서 생성 기능을 사용할 수 있습니다. 이 항목에서는 Microsoft 단위 테스트 프레임워크를 보여 줍니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-create-a-windows-class-library-project-and-a-test-project"></a>Windows 클래스 라이브러리 프로젝트 및 테스트 프로젝트를 만들려면

1. [!INCLUDE[csprcs](../includes/csprcs-md.md)] 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]에서 새 Windows 클래스 라이브러리 프로젝트를 만듭니다. 사용하는 언어에 따라 이름을 `GFUDemo_VB` 또는 `GFUDemo_CS`로 지정합니다.

2. **솔루션 탐색기**에서 맨 위의 솔루션 아이콘을 마우스 오른쪽 단추로 클릭하고 **추가**를 가리킨 다음 **새 프로젝트**를 클릭합니다. **새 프로젝트** 대화 상자의 왼쪽 **프로젝트 형식** 창에서 **테스트**를 클릭합니다.

3. **템플릿** 창에서 **단위 테스트 프로젝트** 를 클릭하고 기본 이름인 UnitTestProject1을 적용합니다. 다음 그림에서는 [!INCLUDE[csprcs](../includes/csprcs-md.md)]에 표시되는 경우의 대화 상자를 보여 줍니다. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]에서도 대화 상자가 유사하게 표시됩니다.

     ![새 테스트 프로젝트 대화 상자](../ide/media/newproject-test.png "NewProject_Test") 새 프로젝트 대화 상자

4. **확인** 을 클릭하여 **새 프로젝트** 대화 상자를 닫습니다.

5. 클래스 프로젝트의 **솔루션 탐색기**에서 **참조** 항목을 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 클릭합니다.

6. **참조 관리자** 대화 상자에서 **프로젝트**를 선택한 다음 단위 테스트 프로젝트를 선택합니다.

7. **확인**을 클릭하여 **참조 관리자** 대화 상자를 닫습니다.

8. **Class1** 파일의 기존 **using** 문의 끝에 있는 테스트 프로젝트에 **using** 문을 추가합니다.

    * Visual Basic에서 `Using UnitTestProject1`을 추가합니다.

    * C#에서 `using UnitTestProject1;`을 추가합니다.

9. 솔루션을 저장합니다. 이제 테스트 작성을 시작할 준비가 되었습니다.

### <a name="to-generate-a-new-class-from-a-unit-test"></a>단위 테스트에서 새 클래스를 생성하려면

1. 테스트 프로젝트에는 UnitTest1이라는 파일이 포함되어 있습니다. **솔루션 탐색기** 에서이 파일을 두 번 클릭 하 여 코드 편집기에서 엽니다. 테스트 클래스 및 테스트 메서드가 생성되었습니다.

2. `UnitTest1` 클래스에 대한 선언을 찾아서 이름을 `AutomobileTest`로 바꿉니다. C#에서 `UnitTest1()` 생성자가 있는 경우 이름을 `AutomobileTest()`로 바꿉니다.

    > [!NOTE]
    > 이제 IntelliSense는 IntelliSense 문 완성을 위해 *완성 모드* 및 *제안 모드*라는 두 가지 대안을 제공합니다. 클래스 및 멤버를 정의하기 전에 사용하는 경우에는 제안 모드를 사용합니다. IntelliSense 창이 열려 있으면 Ctrl+Alt+스페이스바를 눌러 완성 모드와 제안 모드 간을 전환할 수 있습니다. 자세한 내용은 [Using IntelliSense](../ide/using-intellisense.md) 를 참조하세요. 제안 모드는 다음 단계에서 `Automobile` 을 입력할 때 도움이 됩니다.

3. `TestMethod1()` 메서드를 찾아서 이름을 `DefaultAutomobileIsInitializedCorrectly()`로 바꿉니다. 이 메서드 내에서 다음 그림과 같이 `Automobile`이라는 클래스의 새 인스턴스를 만듭니다. 컴파일 시간 오류를 나타내는 물결선이 표시되고 스마트 태그가 형식 이름 아래에 나타납니다. 스마트 태그의 정확한 위치는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 또는 [!INCLUDE[csprcs](../includes/csprcs-md.md)]를 사용하는지에 따라 달라집니다.

     ![Visual Basic의 스마트 태그 밑줄](../ide/media/genclass-underlinevb.png "GenClass_UnderlineVB") Visual Basic

     ![C&#35;의 스마트 태그 밑줄 ](../ide/media/genclass-underline.png "GenClass_Underline") Visual C #

4. 스마트 태그를 마우스 포인터로 가리켜 `Automobile` 이라는 형식이 아직 정의되지 않았다는 오류 메시지를 표시합니다. 스마트 태그를 클릭하거나 Ctrl+. (Ctrl+마침표)를 눌러 다음 그림과 같이 사용법에서 생성 바로 가기 메뉴를 엽니다.

     ![Visual Basic의 스마트 태그 상황에 맞는 메뉴](../ide/media/genclass-smartvb.png "GenClass_SmartVB") Visual Basic

     ![C&#35;의 스마트 태그 상황에 맞는 메뉴 ](../ide/media/genclass-smartcs.png "GenClass_SmartCS") Visual C #

5. 이제 두 가지 선택 옵션이 있습니다. **'Automobile 클래스' 생성** 을 클릭하여 테스트 프로젝트에서 새 파일을 만들고 `Automobile`이라는 빈 클래스로 채울 수 있습니다. 이렇게 하면 현재 프로젝트에 기본 액세스 한정자가 있는 새 파일에서 새 클래스를 빠르게 만들 수 있습니다. **새 형식 생성** 을 클릭하여 **새 형식 생성** 대화 상자를 열 수도 있습니다. 기존 파일에 클래스를 넣고 다른 프로젝트에 파일을 추가하는 옵션이 제공됩니다.

     **새 형식 생성** 을 클릭하여 다음 그림과 같이 **새 형식 생성** 대화 상자를 엽니다. **프로젝트** 목록에서 **GFUDemo_VB** 또는 **GFUDemo_CS** 를 클릭하여 테스트 프로젝트 대신 소스 코드 프로젝트에 파일을 추가하도록 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에 지시합니다.

     ![새 형식 생성 대화 상자](../ide/media/genotherdialog.png "GenOtherDialog") 새 형식 생성 대화 상자

6. **확인** 을 클릭하여 대화 상자를 닫고 새 파일을 만듭니다.

7. **솔루션 탐색기**의 GFUDemo_VB 또는 GFUDemo_CS 프로젝트 노드 아래에서 새 Automobile.vb 또는 Automobile.cs 파일이 있는지 확인합니다. 코드 편집기에서 포커스는 여전히 `AutomobileTest.DefaultAutomobileIsInitializedCorrectly`에 있습니다. 사용 중단을 최소화하여 테스트를 계속 작성할 수 있습니다.

### <a name="to-generate-a-property-stub"></a>속성 스텁을 생성하려면

1. 제품 사양에 따라 `Automobile` 클래스에 `Model` 및 `TopSpeed`라는 두 개의 공용 속성이 있다고 가정합니다. 이러한 속성은 기본값 `"Not specified"` 및 `-1` 을 사용하여 기본 생성자에서 초기화되어야 합니다. 다음 단위 테스트는 기본 생성자가 속성을 올바른 기본값으로 설정하는지 확인합니다.

     `DefaultAutomobileIsInitializedCorrectly`에 다음 코드 줄을 추가합니다.

     [!code-csharp[VbTDDWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#1)]
     [!code-vb[VbTDDWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#1)]

     코드에서 두 개의 정의되지 않은 `Automobile`속성을 참조하기 때문에 스마트 태그가 나타납니다. `Model` 에 대한 스마트 태그를 클릭한 다음 **속성 스텁 생성**을 클릭합니다. `TopSpeed` 속성에 대한 속성 스텁도 생성합니다.

     `Automobile` 클래스에서 새 속성의 형식이 컨텍스트에서 올바르게 유추됩니다.

     다음 그림에서는 스마트 태그 바로 가기 메뉴를 보여 줍니다.

     ![Visual Basic의 속성 생성 상황에 맞는 메뉴](../ide/media/genpropertysmarttagvb.png "GenPropertySmartTagVB") Visual Basic

     ![C&#35;의 속성 생성 상황에 맞는 메뉴 ](../ide/media/genpropertysmarttagcs.png "GenPropertySmartTagCS") Visual C #

### <a name="to-locate-the-source-code"></a>소스 코드를 찾으려면

1. 새 속성을 생성된 것을 확인할 수 있도록 **탐색** 기능을 사용하여 Automobile.cs 또는 Automobile.vb 소스 코드 파일을 탐색합니다.

     **탐색** 기능을 사용하면 형식 이름 또는 이름의 일부와 같은 텍스트 문자열을 빠르게 입력하고 결과 목록에서 요소를 클릭하여 원하는 위치로 이동할 수 있습니다.

     코드 편집기 내부를 클릭하고 Ctrl+,(Ctrl+쉼표)를 눌러 **탐색** 대화 상자를 엽니다. 텍스트 상자에 `automobile`을 입력합니다. 목록에서 **Automobile** 클래스를 클릭한 다음 **확인**을 클릭합니다.

     다음 그림에는 **탐색** 창이 나와 있습니다.

     ![탐색 대화 상자](../ide/media/navigate-2.png "Navigate_2") 창으로 이동

### <a name="to-generate-a-stub-for-a-new-constructor"></a>새로운 생성자에 대한 스텁을 생성하려면

1. 이 테스트 메서드에서는 지정한 값을 사용하도록 `Model` 및 `TopSpeed` 속성을 초기화하는 생성자 스텁을 생성합니다. 나중에 더 많은 코드를 추가하여 테스트를 완료합니다. 다음과 같은 추가 테스트 메서드를 `AutomobileTest` 클래스에 추가합니다.

     [!code-csharp[VbTDDWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#2)]
     [!code-vb[VbTDDWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#2)]

2. 새 클래스 생성자에서 스마트 태그를 클릭한 다음 **생성자 스텁 생성**을 클릭합니다. `Automobile` 클래스 파일에서 새로운 생성자가 생성자 호출에 사용되는 지역 변수의 이름을 검사하고 `Automobile` 클래스에서 동일한 이름을 가진 속성을 찾고 `Model` 및 `TopSpeed` 속성에 인수 값을 저장하는 코드를 생성자 본문에 제공한 것을 확인합니다. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]에서는 새로운 생성자의 `_model` 및 `_topSpeed` 필드가 `Model` 및 `TopSpeed` 속성에 대해 암시적으로 정의된 백업 필드입니다.

3. 새로운 생성자를 생성하면 `DefaultAutomobileIsInitializedCorrectly`의 기본 생성자 호출 아래에 물결선이 표시됩니다. `Automobile` 클래스에 인수를 사용하지 않는 생성자가 없다는 오류 메시지가 나타납니다. 매개 변수가 없는 명시적 기본 생성자를 생성하려면 스마트 태그를 클릭한 다음 **생성자 스텁 생성**을 클릭합니다.

### <a name="to-generate-a-stub-for-a-method"></a>메서드에 대한 스텁을 생성하려면

1. `Automobile` 및 `Model` 속성이 기본값이 아닌 다른 값으로 설정된 경우 사양에 따라 새 `TopSpeed` 을 실행 중 상태로 전환할 수 있다고 가정합니다. `AutomobileWithModelNameCanStart` 메서드에 다음 줄을 추가합니다.

     [!code-csharp[VbTDDWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/unittest1.cs#3)]
     [!code-vb[VbTDDWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/unittest1.vb#3)]

2. `myAuto.Start` 메서드 호출에 대한 스마트 태그를 클릭한 다음 **메서드 스텁 생성**을 클릭합니다.

3. `IsRunning` 속성에 대한 스마트 태그를 클릭한 다음 **속성 스텁 생성**을 클릭합니다. 이제 `Automobile` 클래스에 다음 코드가 포함됩니다.

     [!code-csharp[VbTDDWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/intermediate.cs#4)]
     [!code-vb[VbTDDWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/intermediate.vb#4)]

### <a name="to-run-the-tests"></a>테스트를 실행하려면

1. **단위 테스트** 메뉴에서 **단위 테스트 실행**을 가리킨 다음 **모든 테스트**를 클릭합니다. 이 명령은 현재 솔루션에 대해 작성된 모든 테스트 프레임워크의 모든 테스트를 실행합니다.

     이 경우 두 가지 테스트가 있으며 둘 다 예상대로 실패합니다. `DefaultAutomobileIsInitializedCorrectly` 테스트는 `Assert.IsTrue` 조건이 `False`를 반환하기 때문에 실패합니다. `AutomobileWithModelNameCanStart` 테스트는 `Start` 클래스의 `Automobile` 메서드에서 예외가 발생하기 때문에 실패합니다.

     다음 그림에는 **테스트 결과** 창이 나와 있습니다.

     ![실패 한 테스트 결과](../ide/media/testsfailed.png "TestsFailed") 테스트 결과 창

2. **테스트 결과** 창에서 각 테스트 결과 행을 두 번 클릭하면 각 테스트 실패 위치로 이동할 수 있습니다.

### <a name="to-implement-the-source-code"></a>소스 코드를 구현하려면

1. `Model`, `TopSpeed` 및 `IsRunning` 속성이 모두 올바른 기본값인 `"Not specified"`, `-1`및 `True` (`true`)로 초기화되도록 기본 생성자에 다음 코드를 추가합니다.

     [!code-csharp[VbTDDWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#5)]
     [!code-vb[VbTDDWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#5)]

2. `Start` 메서드를 호출할 경우 `IsRunning` 또는 `Model` 속성이 기본값 이외의 값으로 설정된 경우에만 `TopSpeed` 플래그를 true로 설정해야 합니다. 메서드 본문에서 `NotImplementedException` 을 제거하고 다음 코드를 추가합니다.

     [!code-csharp[VbTDDWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/vbtddwalkthrough/cs/automobile.cs#6)]
     [!code-vb[VbTDDWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbtddwalkthrough/vb/automobile.vb#6)]

### <a name="to-run-the-tests-again"></a>테스트를 다시 실행하려면

1. **테스트** 메뉴에서 **실행**을 가리킨 다음 **솔루션의 모든 테스트**를 클릭합니다. 이번에는 테스트가 성공합니다. 다음 그림에는 **테스트 결과** 창이 나와 있습니다.

     ![통과 한 테스트 결과](../ide/media/testspassed.png "TestsPassed") 테스트 결과 창

## <a name="see-also"></a>관련 항목
 IntelliSense [단위 테스트](../test/unit-test-your-code.md) 를 [사용 하 여](../ide/using-intellisense.md) [코드 작성 코드](../ide/writing-code-in-the-code-and-text-editor.md) [에서 생성](../misc/generate-from-usage.md)

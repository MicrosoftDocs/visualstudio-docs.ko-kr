---
title: UML 클래스 다이어그램에서 코드 생성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates
- vs.teamarch.logicalclassdiagram.shapes.properties.Templates.TextTransformationDataCollectionEditor
helpviewer_keywords:
- code generation, UML class diagrams
- class diagrams - UML, generating code
- UML diagrams, generating code
ms.assetid: 2790e64d-7728-4c2e-a4dd-4131e795f730
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75120b2f09c2eba3254a1b94e78875d8130c5225
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666138"
---
# <a name="generate-code-from-uml-class-diagrams"></a>UML 클래스 다이어그램에서 코드 생성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 UML 클래스 다이어그램에서 Visual c # .NET 코드를 생성 하려면 **코드 생성** 명령을 사용 합니다. 기본적으로 이 명령은 사용자가 선택한 각 UML 형식에 대해 C# 형식을 생성합니다. 코드를 생성하는 텍스트 템플릿을 수정하거나 복사하여 이 동작을 수정하고 확장할 수 있습니다. 모델의 여러 패키지에 포함된 형식에 대해 각기 다른 동작을 지정할 수 있습니다.

 **코드 생성** 명령은 사용자의 요소 선택에서 코드를 생성 하 고 각 UML 클래스 또는 다른 요소에 대해 하나의 파일을 생성 하는 데 특히 적합 합니다. 예를 들어 다음 스크린 샷에서는 두 가지 UML 클래스에서 생성된 두 개의 C# 파일을 보여줍니다.

 또는 생성 된 파일이 UML 요소와 1:1 관계가 없는 코드를 생성 하려면 **모든 템플릿 변환** 명령을 사용 하 여 호출 된 텍스트 템플릿을 작성 하는 것이 좋습니다. 해당 메서드에 대 한 자세한 내용은 [UML 모델에서 파일 생성](../modeling/generate-files-from-a-uml-model.md)을 참조 하세요.

 ![UML 클래스 다이어그램 및 생성 된 C&#35; 클래스 파일입니다.](../modeling/media/oob-gencode1.png "oob_GenCode1")

 Visual Studio의 UML 클래스 다이어그램에 대한 자세한 내용은 다음 항목을 참조하세요.

- [UML 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md)

- [UML 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md)

  UML 클래스 다이어그램을 지 원하는 Visual Studio 버전을 확인 하려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조 하세요.

## <a name="using-the-generate-code-command"></a>코드 생성 명령 사용
 다음 절차에서는 **코드 생성** 명령의 기본 동작에 대해 설명 합니다.

#### <a name="to-generate-a-separate-file-for-each-element"></a>각 요소에 대해 별도의 파일을 생성하려면

1. 클래스가 포함된 UML 모델을 만듭니다. 모델 요소에 스테레오타입을 적용할 수도 있습니다.

    자세한 내용은 [기본 코드 생성 변환](#default)을 참조 하세요.

2. 클래스 다이어그램 또는 **UML 모델 탐색기**에서 코드를 생성 하려는 요소를 선택 합니다. 다음 중 하나를 선택할 수 있습니다.

   - 특정 요소 집합

   - 코드를 생성할 내용이 포함된 패키지 또는 모델

   - 모든 요소를 선택할 다이어그램

3. 선택한 요소에 대 한 바로 가기 메뉴를 열고 **코드 생성**을 선택 합니다.

    특정 모델에서 **코드 생성** 을 처음으로 사용할 때 대화 상자가 나타납니다. 이 대화 상자에서 모델의 코드 생성 매개 변수를 편집할 수 있습니다.

    이러한 매개 변수를 변경 하려는 경우를 제외 하 고 **확인** 을 선택 합니다.

    나중에이 대화 상자로 돌아가려면 **UML 모델 탐색기**를 엽니다. 모델링 프로젝트 바로 가기 메뉴를 열고 **코드 생성 설정**을 선택 합니다. 자세한 내용은 [코드 생성 명령 사용자 지정](#custom)을 참조 하세요.

   C# 코드가 포함된 파일이 생성됩니다. 기본적인 경우에 형식마다 파일이 하나씩 생성되며 이러한 파일은 C# 클래스 라이브러리 프로젝트에서 생성됩니다. 그러나 이 동작을 사용자 지정할 수 있습니다. 자세한 내용은 [코드 생성 명령 사용자 지정](#custom)을 참조 하세요.

   모델이 C#으로 변환될 수 있는지 확인하기 위해 모델에 적용되는 유효성 검사 테스트가 있습니다. 이러한 테스트가 실패하면 오류 메시지가 표시되고 코드가 생성되지 않습니다. 유효성 검사 메뉴 명령을 만든 경우 유효성 검사 명령이 실패하는 모든 요소에 대해 코드가 생성되지 않습니다. 자세한 내용은 [UML 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)를 참조 하세요.

## <a name="default-code-generation-transforms"></a><a name="default"></a> 기본 코드 생성 변환
 이 섹션에서는 명령을 사용자 지정 하지 않는 한 **코드 생성** 명령으로 생성 되는 결과를 요약 합니다. 자세한 내용은 [코드 생성 명령 사용자 지정](#custom)을 참조 하세요.

- UML 모델에서 선택한 형식마다 C# 형식이 하나씩 생성됩니다. 각 형식은 **Generatedcode** 폴더에 있는 별도의 코드 파일에 배치 됩니다.

- UML 형식이 패키지에 포함된 경우 생성된 C# 형식은 네임스페이스 안에 배치되고 네임스페이스와 이름이 동일한 폴더에 파일이 생성됩니다.

- UML 클래스의 `Attribute`마다 C# 속성이 하나씩 생성됩니다.

- UML 형식의 `Operation`마다 C# 메서드가 하나씩 생성됩니다.

- 클래스가 참여하는 탐색 가능한 연결마다 C# 필드가 하나씩 생성됩니다.

  각 UML 형식에 스테레오타입을 추가하여 생성된 C# 형식의 보다 많은 속성을 제어할 수 있습니다.

|**만들 C# 형식**|**그릴 UML 형식**|**적용할 스테레오타입**|
|---------------------------------|----------------------------|-------------------------------|
|클래스|클래스|\<none> 또는<br /><br /> C# class|
|인터페이스|인터페이스|\<none> 또는<br /><br /> C# interface|
|열거형|열거형|\<none> 또는<br /><br /> C# enum|
|대리자|클래스|C# delegate|
|구조체|클래스|C# struct|

#### <a name="to-set-a-stereotype-on-a-type-or-other-element"></a>형식 또는 기타 요소에 대해 스테레오타입을 설정하려면

1. 다이어그램 또는 **UML 모델 탐색기**에서 요소에 대 한 바로 가기 메뉴를 연 다음 **속성**을 선택 합니다.

2. **속성** 창에서 **스테레오 타입** 속성의 드롭다운 화살표를 선택 하 고 적용할 스테레오 타입의 확인란을 선택 합니다.

   > [!TIP]
   > C# 스테레오타입이 나타나지 않으면 모델이나 관심이 있는 모델 요소를 포함하는 패키지에 대한 C# 프로필을 사용하도록 설정합니다. **UML 모델 탐색기**에서 패키지 또는 모델의 루트를 선택 합니다. 그런 다음 **속성** 창에서 **프로필**을 선택한 다음 c # 프로필을 사용 하도록 설정 합니다.

3. **스테레오 타입** 속성을 확장 하 여 설정할 수 있는 추가 속성을 볼 수 있습니다.

   형식, 특성, 작업 및 연결의 **설명** 속성은 `<summary>` 생성 된 코드의 주석에 기록 됩니다. 형식에 연결된 주석 요소는 `<remarks>` 주석에 기록됩니다.

## <a name="varying-the-generated-code"></a>생성된 코드 변경
 생성된 코드는 각 형식, 특성 또는 작업의 속성에 따라 달라집니다. 예를 들어 클래스의 **Is Abstract** 속성을 true로 설정 하면 `abstract` 생성 된 클래스에 키워드가 표시 됩니다. 특성의 **복합성** 을 **0. \* .** 로 설정 하면 생성 된 속성은 형식을 갖습니다 `IEnumerable<>` .

 또한 각 스테레오타입은 설정할 수 있는 몇 가지 추가 속성을 제공합니다. 이러한 값은 C# 코드에서 적절한 키워드로 변환됩니다. 예를 들어 클래스에서 `Is Static` 속성을 설정하면 C# 클래스가 `static`이 됩니다.

 이러한 추가 속성을 설정하려면 다이어그램에서 클래스나 다른 요소를 선택합니다. 속성 창에서 **스테레오 타입**을 확장 한 다음 c # **클래스**와 같은 c # 스테레오 타입을 확장 합니다.  클래스의 경우 다음과 같은 추가 속성이 포함됩니다.

- CLR Attributes

- Is Partial

- 정적

- Is Unsafe

- Package Visibility

  각 특성과 작업에는 설정할 수 있는 스테레오타입 속성도 있습니다. 새 특성에 대 한 속성이 표시 되지 않으면 **코드 생성**을 실행 합니다.

## <a name="customizing-the-generate-code-command"></a><a name="custom"></a> 코드 생성 명령 사용자 지정
 **코드 생성** 명령은 텍스트 템플릿 집합을 사용 하 여 모델 요소를 변환 하는 방식으로 작동 합니다. 텍스트 템플릿에 대 한 자세한 내용은 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)을 참조 하세요.

 템플릿은 *텍스트 템플릿 바인딩*집합에 지정 됩니다. 텍스트 템플릿 바인딩은 적용 해야 하는 템플릿, 생성 된 출력이 배치 되어야 하는 위치 및 **코드 생성** 명령의 기타 매개 변수를 지정 합니다.

 특정 모델에서 **코드 생성** 명령을 처음 실행 하면 템플릿 바인딩의 기본 집합이 모델의 루트에 연결 됩니다. 이러한 바인딩은 모델의 모든 요소에 적용됩니다.

 그러나 사용자 고유의 바인딩을 패키지, 클래스 또는 다른 요소에 연결하여 이러한 기본 바인딩을 재정의하거나 기본 바인딩에 추가할 수 있습니다. 바인딩은 바인딩이 연결된 요소에 포함된 모든 요소에 적용됩니다. 예를 들어 특정 패키지 내의 모든 형식이 다른 템플릿 집합에 의해 변형되거나 다른 폴더에 출력되도록 하려는 경우 템플릿 바인딩을 패키지에 연결할 수 있습니다.

 모델 요소에 연결 된 템플릿 바인딩을 검사 하려면 속성 창의 **텍스트 템플릿 바인딩** 속성에서 줄임표 **[...]** 를 선택 합니다.

 **코드 생성** 명령은 선택한 각 모델 요소에 템플릿을 적용 합니다. 각 요소의 경우 적용된 템플릿 집합은 모델의 루트를 포함하여 모델의 루트까지 존재하는 요소의 컨테이너에 연결된 템플릿의 결합된 집합입니다.

 이 집합에 있는 두 템플릿 바인딩의 이름이 동일한 경우 더 작은 컨테이너의 바인딩이 더 큰 컨테이너의 바인딩보다 우선합니다. 예를 들어 모델 루트에는 name **클래스 템플릿이**있는 바인딩이 있습니다. 사용자 고유의 템플릿을 특정 패키지의 내용에 적용 하려면 이름 **클래스 템플릿이**있는 고유한 템플릿 바인딩을 정의 합니다.

 둘 이상의 템플릿을 모델 요소에 적용할 수 있습니다. 각 모델 요소에서 둘 이상의 파일을 생성할 수 있습니다.

> [!NOTE]
> 모델의 루트에 연결된 바인딩은 모델의 모든 요소에 대한 기본값으로 작동합니다. 이러한 기본 바인딩을 보려면 **UML 모델 탐색기**를 엽니다. 모델링 프로젝트의 바로 가기 메뉴를 열고 **코드 생성 설정**을 선택 합니다. 또는 UML 모델 탐색기에서 모델의 루트를 선택할 수 있습니다. 속성 창에서 **텍스트 템플릿 바인딩** 속성의 **[...]** 를 선택 합니다. **코드 생성** 명령을 한 번 이상 사용할 때까지 바인딩이 나타나지 않습니다. 템플릿 바인딩은 다이어그램에 연결할 수 없습니다.

#### <a name="to-attach-text-template-bindings-to-a-package-or-other-model-element"></a>텍스트 템플릿 바인딩을 패키지 또는 다른 모델 요소에 연결하려면

1. **UML 모델 탐색기**에서 모델 요소에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다. 일반적으로 패키지나 모델의 루트에 텍스트 템플릿 바인딩을 연결합니다.

2. **속성** 창의 **텍스트 템플릿 바인딩** 속성에서 줄임표 단추 (**[...]**)를 선택 합니다.

    **텍스트 템플릿 바인딩** 대화 상자가 나타납니다.

3. **추가** 를 선택 하 여 새 텍스트 템플릿 바인딩을 만듭니다.

    \- 또는 -

    편집하려면 기존 바인딩을 선택합니다.

    각 템플릿 바인딩은 선택한 모델 요소에 지정된 템플릿을 적용해야 하는 방법과 포함된 다른 모델 요소를 정의합니다.

4. 대화 상자에서 텍스트 템플릿 바인딩의 속성을 설정합니다.

   |    **속성**    |                                                                                                                                                                                                                                                                                                                    **설명**                                                                                                                                                                                                                                                                                                                    |
   |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |        Name        |                                                                                                                                                                                                                                                  이 바인딩의 이름입니다. 포함하는 패키지 또는 모델에서 상속한 바인딩을 재정의하려면 재정의할 바인딩과 동일한 이름을 사용합니다.                                                                                                                                                                                                                                                  |
   |     Overwrite      |                                                                                                                                                                                                                                                                                                      true이면 모든 기존 코드를 덮어씁니다.                                                                                                                                                                                                                                                                                                       |
   |    대상 이름     | 생성된 파일의 이름입니다.<br /><br /> 또는와 같은이 문자열에 식을 삽입할 수 `{Name}` 있습니다 `{Owner.Name}` . 예를 들어를 작성할 수 있습니다 `{Owner.Name}_{Name}` . 식은 모델 요소에 대해 평가됩니다. 식에서는 요소의 속성을 사용할 수 있지만 메서드의 속성은 사용할 수 없습니다. 사용할 수 있는 속성을 찾으려면 **VisualStudio \* **에서 형식의 속성을 참조 하세요. \*\*중요: \* \* `{Name}` 또는 `{Owner.Name}` 는 **대상 이름** 속성에만 사용할 수 있습니다.   생성된 클래스의 이름을 변경하려면 템플릿을 수정해야 합니다. 자세한 내용은 [텍스트 템플릿 작성](#writing)을 참조 하세요. |
   |    프로젝트 경로    |                                                                      변환의 출력 파일을 포함할 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트의 경로를 지정합니다. 새 프로젝트를 만들려면 형식화된 값을 사용하고, 줄임표 단추 (**[...]**)를 선택 하 여 기존 프로젝트를 선택 합니다.<br /><br /> 새 프로젝트가 없는 경우 만들어지며, C# 클래스 라이브러리 프로젝트가 됩니다.<br /><br /> 이렇게 하려면 프로젝트를 직접 입력해야 합니다. %ProgramFiles% 또는 %LocalAppData%와 같은 환경 변수 매크로를 포함할 수 있습니다.                                                                       |
   |  대상 디렉터리  |                                                                                          대상 파일이 생성된 폴더입니다. 경로는 프로젝트 폴더에 상대적입니다.<br /><br /> `{PackageStructure}` 식을 사용하여, 포함하는 패키지의 이름에 해당하는 경로를 삽입할 수 있습니다. 기본값은 `\GeneratedCode\{PackageStructure}`입니다. %TEMP% 또는 %HomePath%와 같은 환경 변수도 포함할 수 있습니다. **중요:** `{PackageStructure}` **대상 디렉터리** 속성에만 사용할 수 있습니다.                                                                                            |
   | 템플릿 파일 경로 |                                                                                                                                                           변형을 수행할 템플릿입니다.<br /><br /> 제공된 템플릿을 사용하거나 사용자 고유의 템플릿을 만들 수 있습니다. 다음 위치에서 제공된 템플릿을 찾을 수 있습니다.<br /><br /> …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\                                                                                                                                                           |

5. 바인딩을 원하는 만큼 요소에 연결할 수 있습니다.

## <a name="writing-a-text-template"></a><a name="writing"></a> 텍스트 템플릿 작성
 사용자 고유의 텍스트 템플릿을 작성할 수 있습니다. 텍스트 템플릿은 프로그램 코드나 다른 모든 종류의 텍스트 파일을 생성할 수 있습니다.

 표준 템플릿의 복사본을 수정하여 시작하는 것이 좋습니다. 다음 위치에서 템플릿을 복사할 수 있습니다.

 …\Program Files\Microsoft Visual Studio 12.0\Common7\IDE\Extensions\Microsoft\Architecture Tools\Extensibility\Templates\Text\

 텍스트 템플릿을 이해하려면 다음 항목을 참조하십시오.

- 텍스트 템플릿은 결과 파일의 프로토타입이며 결과 텍스트와 모델을 읽는 프로그램 코드를 둘 다 포함합니다. 자세한 내용은 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)을 참조 하세요.

- 프로그램 코드에서 UML 모델을 탐색하려면 UML API를 사용해야 합니다. 자세한 내용은 uml [모델 탐색](../modeling/navigate-the-uml-model.md) 및 [uml 모델링 확장성에 대 한 API 참조](../modeling/api-reference-for-uml-modeling-extensibility.md)를 참조 하세요.

  **코드 생성** 명령을 사용 하 여 템플릿을 사용 하려면 모델링 지시문을 포함 해야 합니다. 예를 들면 다음과 같습니다.

  `<#@ Modeling ElementType="Microsoft.VisualStudio.Uml.Classes.IClass" Processor="ModelingProcessor" #>`

  `ElementType` 특성은 이 템플릿이 적용되는 UML 요소의 형식을 정의합니다.

  템플릿에서 `this`는 다음 속성이 있는 임시 클래스에 속합니다.

- `Element` = 템플릿이 적용 되는 UML [IElement](/previous-versions/dd516035(v=vs.140)) .

- `Errors`: <xref:System.CodeDom.Compiler.CompilerErrorCollection>

- `Host`: [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))

- `ModelBus`: [ModelBus](/previous-versions/ee904639(v=vs.140)). 자세한 내용은 [UML 모델을 다른 모델 및 도구와 통합](../modeling/integrate-uml-models-with-other-models-and-tools.md)을 참조 하세요.

- `ProfileName` = "C#Profile"

- `ServiceProvider`: <xref:System.IServiceProvider>

- `Session`: <xref:Microsoft.VisualStudio.TextTemplating.TextTemplatingSession>.

- `Store`: <xref:Microsoft.VisualStudio.Modeling.Store>. UML ModelStore가 구현되는 Visualization and Modeling SDK 저장소입니다. UML [Imodelstore](/previous-versions/ee789385(v=vs.140))를 가져오려면를 사용 `this.Element.GetModelStore()` 합니다.

  텍스트 템플릿을 작성하는 동안 다음 사항을 참고하면 도움이 될 수 있습니다. 이 정보는 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)에 자세히 설명 되어 있습니다.

- `Output` 지시문에서 결과의 파일 확장명을 설정할 수 있습니다. 각 텍스트 템플릿에는 `Output` 지시문이 하나씩 필요합니다.

- 일부 어셈블리는 템플릿에서 자동으로 참조됩니다. 이러한 어셈블리에는 System.dll, Microsoft.VisualStudio.Uml.Interfaces.dll 등이 있습니다.

   생성하는 프로그램 코드에서 다른 어셈블리를 사용하려면 `Assembly` 지시문을 사용해야 합니다. 예를 들면 다음과 같습니다.

   `<#@ Assembly Name="%ProgramFiles%\Microsoft Visual Studio 12.0\Common7\IDE\PublicAssemblies\Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll" #>`

- `System`과 같은 일부 네임스페이스를 프로그램 코드에 자동으로 가져올 수 있습니다. 다른 네임스페이스의 경우 `Import` 문을 사용할 때와 같은 방식으로 `using` 지시문을 사용할 수 있습니다. 예를 들면 다음과 같습니다.

   `<#@ Import Namespace="Microsoft.VisualStudio.Uml.Classes" #>`

   `<#@ Import Namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>`

- `Include` 지시문을 사용하여 다른 파일의 텍스트를 참조할 수 있습니다.

- 대괄호로 묶인 템플릿 부분은 `<# ... #>` **코드 생성** 명령에 의해 실행 됩니다. 이러한 꺾쇠 괄호 밖에 있는 템플릿의 부분은 결과 파일에 복사됩니다. 생성하는 코드와 생성된 텍스트를 구별할 수 있어야 합니다. 텍스트는 어떠한 언어로도 생성될 수 있습니다.

- `<#= Expressions #>` 평가 되 고 문자열로 변환 됩니다.

## <a name="see-also"></a>관련 항목
 [Uml 클래스 다이어그램: 참조](../modeling/uml-class-diagrams-reference.md) [uml 클래스 다이어그램: 지침](../modeling/uml-class-diagrams-guidelines.md) [uml 모델에서 파일 생성](../modeling/generate-files-from-a-uml-model.md)

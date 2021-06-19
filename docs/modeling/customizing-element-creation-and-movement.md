---
title: 요소 만들기 및 이동 사용자 지정
description: 도구 상자에서 또는 붙여넣기 또는 이동 작업에서 요소를 다른 요소로 끌 수 있도록 허용하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42339c532db3442d5fb5c5da3b51d94801a0907d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389399"
---
# <a name="customizing-element-creation-and-movement"></a>요소 만들기 및 이동 사용자 지정

도구 상자 또는 붙여넣기 또는 이동 작업에서 요소를 다른 요소로 끌도록 허용할 수 있습니다. 지정한 관계를 사용하여 이동된 요소를 대상 요소에 연결할 수 있습니다.

EMD(요소 병합 지시문)는 한 모델 요소를 다른 모델 요소에 *병합할* 때 발생하는 일을 지정합니다. 이런 상황은 다음과 같은 경우에 발생합니다.

- 사용자가 도구 상자에서 다이어그램 또는 도형으로 끌어 놓습니다.

- 사용자는 탐색기 또는 구획 모양에서 추가 메뉴를 사용하여 요소를 만듭니다.

- 사용자가 스윔 레인에서 다른 스윔 레인으로 항목을 이동합니다.

- 사용자가 요소를 붙여넣습니다.

- 프로그램 코드는 요소 병합 지시문을 호출합니다.

만들기 작업은 복사 작업과 다를 수 있지만 실제로는 동일한 방식으로 작동합니다. 예를 들어 도구 상자에서 요소를 추가하면 해당 요소의 프로토타입이 복제됩니다. 프로토타입은 모델의 다른 부분에서 복사된 요소와 동일한 방식으로 모델에 병합됩니다.

EMD의 책임은 개체 또는 개체 그룹을 모델의 특정 위치에 병합하는 방법을 결정하는 것입니다. 특히 병합된 그룹을 모델에 연결하기 위해 인스턴스화해야 하는 관계를 결정합니다. 속성을 설정하고 추가 개체를 만들도록 사용자 지정할 수도 있습니다.

![EM D에서 새 요소가 추가되는 방법을 결정할 때 요소의 트리와 해당 참조 관계를 살펴보기 전과 후에 를 보여 주는 다이어그램.](../modeling/media/dsl-emd_merge.png)

EMD는 포함 관계를 정의할 때 자동으로 생성됩니다. 이 기본 EMD는 사용자가 부모에 새 자식 인스턴스를 추가할 때 관계의 인스턴스를 만듭니다. 예를 들어 사용자 지정 코드를 추가하여 이러한 기본 EMD를 수정할 수 있습니다.

DSL 정의에 사용자 고유의 EMD를 추가하여 사용자가 병합된 클래스와 수신 클래스의 다양한 조합을 끌어서 붙여넣을 수도 있습니다.

## <a name="defining-an-element-merge-directive"></a>요소 병합 지시문 정의

도메인 클래스, 도메인 관계, 도형, 커넥터 및 다이어그램에 요소 병합 지시문을 추가할 수 있습니다. DSL 탐색기의 수신 도메인 클래스에서 추가하거나 찾을 수 있습니다. 받는 클래스는 모델에 이미 있고 새 요소나 복사된 요소를 병합할 요소의 도메인 클래스입니다.

![인덱싱 클래스로 ExampleElement가 선택되고 하위 클래스에 적용 옵션이 선택된 EM D가 추가되는 것을 보여주는 DSL 탐색기의 스크린샷.](../modeling/media/dsl-emd_details.png)

**인덱싱 클래스는** 받는 클래스의 멤버로 병합할 수 있는 요소의 도메인 클래스입니다. 서브클래스에 적용을 False로 설정하지 않으면 인덱싱 클래스의 **서브클래스** 인스턴스도 이 EMD에서 병합됩니다.

병합 지시문에는 두 가지 종류가 있습니다.

- **Process Merge** 지시문은 새 요소를 트리에 연결해야 하는 관계를 지정합니다.

- **Forward Merge** 지시문은 새 요소를 다른 수신 요소(일반적으로 부모)로 리디렉션합니다.

지시문을 병합하는 사용자 지정 코드를 추가할 수 있습니다.

- Set **사용자 지정 accept를 사용하여** 사용자 고유의 코드를 추가하여 인덱싱 요소의 특정 인스턴스를 대상 요소에 병합해야 하는지 여부를 결정합니다. 사용자가 도구 상자에서 끌어 올 때 코드에서 병합을 허용되지 않는 경우 "잘못된" 포인터가 표시됩니다.

   예를 들어 수신 요소가 특정 상태인 경우에만 병합을 허용할 수 있습니다.

- 집합 **사용자 지정 병합을 사용하여** 병합이 수행될 때 모델에 대한 변경 내용을 정의하는 고유한 코드를 추가합니다.

   예를 들어 모델의 새 위치에서 데이터를 사용하여 병합된 요소의 속성을 설정할 수 있습니다.

> [!NOTE]
> 사용자 지정 병합 코드를 작성하는 경우 이 EMD를 사용하여 수행되는 병합에만 영향을 미칩니다. 동일한 형식의 개체를 병합하는 다른 EMD가 있거나 EMD를 사용하지 않고 이러한 개체를 만드는 다른 사용자 지정 코드가 있는 경우 사용자 지정 병합 코드의 영향을 받지 않습니다.
>
> 새 요소 또는 새 관계가 항상 사용자 지정 코드에서 처리되도록 하려면 `AddRule` 포함 관계에서 를 정의하고 요소의 도메인 클래스에 를 정의하는 것이 `DeleteRule` 좋습니다. 자세한 내용은 규칙 모델 [내에서 변경 내용 전파를 참조하세요.](../modeling/rules-propagate-changes-within-the-model.md)

## <a name="example-defining-an-emd-without-custom-code"></a>예제: 사용자 지정 코드 없이 EMD 정의

다음 예제에서는 도구 상자에서 기존 셰이프로 끌어서 요소와 커넥터를 동시에 만들 수 있습니다. 이 예제는 DSL 정의에 EMD를 추가합니다. 이 수정 전에 사용자는 도구를 다이어그램으로 끌어다 놓을 수 있지만 기존 도형으로 끌어다 놓을 수는 없습니다.

사용자는 요소를 다른 요소에 붙여넣을 수도 있습니다.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>사용자가 요소와 커넥터를 동시에 만들 수 있도록 하려면

1. **최소 언어** 솔루션 템플릿을 사용하여 새 DSL을 만듭니다.

    이 DSL을 실행하면 도형 간에 셰이프와 커넥터를 만들 수 있습니다. 도구 상자에서 기존 셰이프로 새 **ExampleElement** 셰이프를 끌 수 없습니다.

2. 사용자가 도형에 요소를 병합할 수 있도록 `ExampleElement` 하려면 도메인 클래스에 새 EMD를 만듭니다. `ExampleElement`

   1. **DSL 탐색기에서** **도메인 클래스 를 확장합니다.** 마우스 오른쪽 단추를 `ExampleElement` 클릭한 다음 새 요소 병합 **지시문 추가** 를 클릭합니다.

   2. 새 EMD의 세부 정보를 볼 수 있도록 **DSL 세부 정보** 창이 열려 있는지 확인합니다. (메뉴: **보기**, **다른 창**, **DSL 세부 정보.)**

3. DSL 세부 내용 창에서 **인덱싱 클래스를** 설정하여 개체에 병합할 수 있는 요소 클래스를 `ExampleElement` 정의합니다.

    이 예제에서는 `ExampleElements` 사용자가 새 요소를 기존 요소로 끌 수 있도록 를 선택합니다.

    인덱싱 클래스는 DSL 탐색기에서 EMD의 이름이 됩니다.

4. **링크를 만들어 병합 처리** 아래에 다음 두 개의 경로를 추가합니다.

   - 한 경로는 새 요소를 부모 모델에 연결합니다. 입력해야 하는 경로 식은 기존 요소에서 부모 모델에 대한 포함 관계까지 이동합니다. 마지막으로 새 요소를 할당할 새 링크의 역할을 지정합니다. 경로는 다음과 같습니다.

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - 다른 경로는 새 요소를 기존 요소에 연결합니다. path 식은 참조 관계와 새 요소가 할당될 역할을 지정합니다. 이 경로는 다음과 같습니다.

      `ExampleElementReferencesTargets.Sources`

      경로 탐색 도구를 사용하여 각 경로를 만들 수 있습니다.

      1. **경로에 링크를 만들어 병합 처리 아래에서** 를 **\<add path>** 클릭합니다.

      2. 목록 항목의 오른쪽에 있는 드롭다운 화살표를 클릭합니다. 트리 뷰가 나타납니다.

      3. 트리의 노드를 확장하여 지정하려는 경로를 구성합니다.

5. DSL 테스트:

   1. **F5** 키를 눌러 솔루션을 다시 빌드하고 실행합니다.

        생성된 코드가 새 DSL 정의를 준수하도록 텍스트 템플릿에서 업데이트되기 때문에 다시 빌드하는 데는 평소보다 오래 걸릴 수 있습니다.

   2. Visual Studio 실험적 인스턴스가 시작되면 DSL의 모델 파일을 엽니다. 몇 가지 예제 요소를 만듭니다.

   3. **Example 요소** 도구에서 기존 도형으로 끌어서 놓습니다.

        새 셰이프가 나타나고 커넥터를 사용하여 기존 셰이프에 연결됩니다.

   4. 기존 셰이프를 복사합니다. 다른 셰이프를 선택하고 붙여넣습니다.

        첫 번째 도형의 복사본이 만들어집니다.  새 이름이 있으며 커넥터를 사용하여 두 번째 셰이프에 연결됩니다.

이 절차에서 다음 사항을 알아차리세요.

- 요소 병합 지시문을 만들면 요소의 모든 클래스가 다른 클래스를 허용하도록 허용할 수 있습니다. EMD는 수신 도메인 클래스에서 만들어지고 허용되는 도메인 클래스는 **인덱스 클래스** 필드에 지정됩니다.

- 경로를 정의하여 새 요소를 기존 모델에 연결하는 데 사용해야 하는 링크를 지정할 수 있습니다.

     지정한 링크에는 하나의 포함 관계가 포함되어야 합니다.

- EMD는 도구 상자에서 만드는 작업과 붙여넣기 작업에 모두 영향을 미칩니다.

     새 요소를 만드는 사용자 지정 코드를 작성하는 경우 메서드를 사용하여 EMD를 명시적으로 호출할 수 `ElementOperations.Merge` 있습니다. 이렇게 하면 코드가 다른 작업과 동일한 방식으로 새 요소를 모델에 연결합니다. 자세한 내용은 [복사 동작 사용자 지정을 참조하세요.](../modeling/customizing-copy-behavior.md)

## <a name="example-adding-custom-accept-code-to-an-emd"></a>예제: EMD에 사용자 지정 수락 코드 추가

EMD에 사용자 지정 코드를 추가하여 더 복잡한 병합 동작을 정의할 수 있습니다. 이 간단한 예제에서는 사용자가 고정된 개수 이상의 요소를 다이어그램에 추가할 수 없습니다. 이 예제는 포함 관계와 함께 기본 EMD를 수정합니다.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>사용자가 추가할 수 있는 내용을 제한하는 사용자 지정 수락 코드를 작성하려면

1. **최소 언어** 솔루션 템플릿을 사용하여 DSL을 만듭니다. DSL 정의 다이어그램을 엽니다.

2. DSL 탐색기에서 **도메인 클래스**, , 요소 병합 `ExampleModel` **지시문을 확장합니다.** 라는 요소 병합 지시문을 `ExampleElement` 선택합니다.

     이 EMD는 사용자가 모델에서 새 개체를 만드는 방법을 `ExampleElement` 제어합니다(예: 도구 상자에서 끌어서).

3. **DSL 세부 정보** 창에서 **사용자 지정 허용 사용을** 선택합니다.

4. 솔루션을 다시 빌드합니다. 생성된 코드가 모델에서 업데이트되기 때문에 이 시간이 평소보다 오래 걸릴 수 있습니다.

     "Company.ElementMergeSample.ExampleElement에 CanMergeExampleElement에 대한 정의가 포함되어 있지 않습니다..."와 유사한 빌드 오류가 보고됩니다.

     메서드를 구현해야 `CanMergeExampleElement` 합니다.

5. Dsl 프로젝트에 새 코드 파일을 **만듭니다.** 콘텐츠를 다음 코드로 바꾸고 네임스페이스를 프로젝트의 네임스페이스로 변경합니다.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }
    ```

    이 간단한 예제에서는 부모 모델에 병합할 수 있는 요소 수를 제한합니다. 더 흥미로운 조건을 위해 메서드는 수신 개체의 속성 및 링크를 검사할 수 있습니다. 또한 에 포함된 병합 요소의 속성을 검사할 수도 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> 있습니다. 에 대한 자세한 내용은 `ElementGroupPrototypes` [복사 동작 사용자 지정을 참조하세요.](../modeling/customizing-copy-behavior.md) 모델을 읽는 코드를 작성하는 방법에 대한 자세한 내용은 [프로그램 코드에서 모델 탐색 및 업데이트를](../modeling/navigating-and-updating-a-model-in-program-code.md)참조하세요.

6. DSL 테스트:

    1. **F5** 키를 눌러 솔루션을 다시 빌드합니다. Visual Studio 실험적 인스턴스가 열리면 DSL의 인스턴스를 엽니다.

    2. 여러 가지 방법으로 새 요소를 만듭니다.

        - **Example 요소** 도구에서 다이어그램으로 끌어서 놓습니다.

        - 예제 **모델 탐색기에서** 루트 노드를 마우스 오른쪽 단추로 클릭한 다음 **새 예제 요소 추가를** 클릭합니다.

        - 다이어그램에서 요소를 복사하여 붙여넣습니다.

    3. 이러한 방법 중 어떤 방법도 사용하여 모델에 4개 이상의 요소를 추가할 수 없는지 확인합니다. 이는 모두 요소 병합 지시문을 사용하기 때문입니다.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>예제: EMD에 사용자 지정 병합 코드 추가

사용자 지정 병합 코드에서 사용자가 도구를 끌거나 요소에 붙여넣을 때 발생하는 일을 정의할 수 있습니다. 사용자 지정 병합을 정의하는 방법에는 두 가지가 있습니다.

1. **사용자 지정 병합 사용을** 설정하고 필요한 코드를 지정합니다. 코드는 생성된 병합 코드를 대체합니다. 병합이 수행하는 작업을 완전히 다시 정의하려면 이 옵션을 사용합니다.

2. `MergeRelate`메서드를 재정의하고 필요에 따라 `MergeDisconnect` 메서드를 재정의합니다. 이렇게 하려면 도메인 클래스의 **Generates Double Derived** 속성을 설정해야 합니다. 코드는 기본 클래스에서 생성된 병합 코드를 호출할 수 있습니다. 병합이 수행된 후 추가 작업을 수행하려면 이 옵션을 사용합니다.

   이러한 방법은 이 EMD를 사용하여 수행되는 병합에만 영향을 미칩니다. 병합된 요소를 만들 수 있는 모든 방법에 영향을 주려면 포함 `AddRule` 관계에 를 정의하고 병합된 도메인 클래스에 를 정의하는 것이 `DeleteRule` 좋습니다. 자세한 내용은 규칙 모델 [내에서 변경 내용 전파를 참조하세요.](../modeling/rules-propagate-changes-within-the-model.md)

### <a name="to-override-mergerelate"></a>MergeRelate를 재정의하려면

1. DSL 정의에서 코드를 추가할 EMD를 정의했는지 확인합니다. 원하는 경우 이전 섹션에서 설명한 대로 경로를 추가하고 사용자 지정 수락 코드를 정의할 수 있습니다.

2. DslDefinition 다이어그램에서 병합의 수신 클래스를 선택합니다. 일반적으로 포함 관계의 소스 끝에 있는 클래스입니다.

     예를 들어 최소 언어 솔루션에서 생성된 DSL에서 를 `ExampleModel` 선택합니다.

3. **속성** 창에서 **Double Derived 생성을** **true** 로 설정합니다.

4. 솔루션을 다시 빌드합니다.

5. **Dsl\Generated Files\DomainClasses.cs의 콘텐츠를 검사합니다.** 라는 메서드를 `MergeRelate` 검색하고 해당 내용을 검사합니다. 이렇게 하면 고유한 버전을 작성하는 데 도움이 됩니다.

6. 새 코드 파일에서 수신 클래스에 대한 partial 클래스를 작성하고 `MergeRelate` 메서드를 재정의합니다. 기본 메서드를 호출해야 합니다. 예를 들면 다음과 같습니다.

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }
    ```

### <a name="to-write-custom-merge-code"></a>사용자 지정 병합 코드를 작성하려면

1. **Dsl\Generated Code\DomainClasses.cs에서** 라는 메서드를 `MergeRelate` 검사합니다. 이러한 메서드는 새 요소와 기존 모델 간에 링크를 만듭니다.

    또한 라는 메서드를 `MergeDisconnect` 검사합니다. 이러한 메서드는 삭제될 때 모델에서 요소의 연결을 해제합니다.

2. **DSL 탐색기에서** 사용자 지정하려는 요소 병합 지시문을 선택하거나 만듭니다. **DSL 세부 정보** 창에서 **사용자 지정 병합 사용을** 설정합니다.

    이 옵션을 설정하면 **병합 처리** 및 **병합 전달** 옵션이 무시됩니다. 코드가 대신 사용됩니다.

3. 솔루션을 다시 빌드합니다. 생성된 코드 파일이 모델에서 업데이트되기 때문에 평소보다 오래 걸릴 수 있습니다.

    오류 메시지가 표시됩니다. 생성된 코드의 지침을 보려면 오류 메시지를 두 번 클릭합니다. 다음 지침에서는 `MergeRelate` *YourDomainClass 및* `MergeDisconnect` *YourDomainClass라는* 두 가지 메서드를 제공하라는 메시지가 표시됩니다.

4. 부분 클래스 정의의 메서드를 별도의 코드 파일에 씁니다. 이전에 검사한 예제는 필요한 것을 제안해야 합니다.

   사용자 지정 병합 코드는 개체와 관계를 직접 만드는 코드에 영향을 미치지 않으며 다른 EMD에는 영향을 미치지 않습니다. 요소를 만드는 방법에 관계없이 추가 변경 내용이 구현되도록 하려면 대신 및 을 작성하는 것이 `AddRule` `DeleteRule` 좋습니다. 자세한 내용은 규칙 모델 [내에서 변경 내용 전파를 참조하세요.](../modeling/rules-propagate-changes-within-the-model.md)

## <a name="redirecting-a-merge-operation"></a>병합 작업 리디렉션

병합 지시문은 병합 작업의 대상을 리디렉션합니다. 일반적으로 새 대상은 초기 대상의 포함 부모입니다.

예를 들어 구성 요소 다이어그램 템플릿을 통해 만든 DSL에서 포트는 구성 요소에 포함됩니다. 포트는 구성 요소 셰이프의 가장자리에 작은 모양으로 표시됩니다. 사용자는 포트 도구를 구성 요소 모양으로 끌어서 포트를 만듭니다. 그러나 경우에 따라 사용자가 실수로 포트 도구를 구성 요소 대신 기존 포트로 끌어다 놓으면 작업이 실패합니다. 기존 포트가 여러 대 있는 경우 이는 쉬운 실수입니다. 사용자가 이러한 문제가 발생하지 않도록 하려면 포트를 기존 포트로 끌 수 있지만 작업이 부모 구성 요소로 리디렉션되도록 할 수 있습니다. 작업은 대상 요소가 구성 요소인 것처럼 작동합니다.

구성 요소 모델 솔루션에서 forward merge 지시문을 만들 수 있습니다. 원래 솔루션을 컴파일하고 실행하는 경우 사용자가 **도구 상자에서** **Component** 요소로 원하는 수의 **입력 포트** 또는 출력 **포트** 요소를 끌 수 있음을 알 수 있습니다. 그러나 포트를 기존 포트로 끌 수는 없습니다. 사용할 수 없음 포인터는 이 이동을 사용할 수 없음을 경고합니다. 그러나 기존 **입력** 포트에서 의도치 않게 삭제된 포트가 **Component** 요소로 전달되도록 정방향 병합 지시문을 만들 수 있습니다.

### <a name="to-create-a-forward-merge-directive"></a>병합 지시문을 만들려면

1. 구성 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 요소 모델 템플릿을 사용하여 솔루션을 만듭니다.

2. DslDefinition.dsl을 열어 **DSL 탐색기를** 표시합니다.

3. **DSL 탐색기에서** **도메인 클래스 를 확장합니다.**

4. **ComponentPort** 추상 도메인 클래스는 **InPort** 및 **OutPort** 의 기본 클래스입니다. **ComponentPort를** 마우스 오른쪽 단추로 클릭한 다음 **새 요소 병합 지시문 추가를** 클릭합니다.

    새 **요소 병합 지시문** 노드가 **요소 병합 지시문** 노드 아래에 나타납니다.

5. 요소 **병합 지시문** 노드를 선택하고 **DSL 세부 정보** 창을 엽니다.

6. 인덱싱 클래스 목록에서 **ComponentPort를** 선택합니다.

7. **다른 도메인 클래스 에 병합 전달을** 선택합니다.

8. 경로 선택 목록에서 **ComponentPort를** 확장하고 **ComponentHasPorts 를** 확장한 다음 **구성 요소** 를 선택합니다.

    새 경로는 다음과 유사합니다.

    **ComponentHasPorts.Component/!Component**

9. 솔루션을 저장한 다음, **솔루션 탐색기** 도구 모음에서 가장 오른쪽 단추를 클릭하여 템플릿을 변환합니다.

10. 솔루션을 빌드하고 실행합니다. Visual Studio의 새 인스턴스가 나타납니다.

11. **솔루션 탐색기** 에서 샘플. mydsl을 엽니다. 다이어그램 및 **Componentlanguage 도구 상자가** 나타납니다.

12. **입력 포트** 를 **도구 상자** 에서 다른 **입력 포트로** 끌어 옵니다. 그런 다음 **outputport** 를 **inputport** 로 끈 다음 다른 **outputport** 로 끕니다.

     사용할 수 없는 포인터는 표시 되지 않으며 기존 **입력 포트에 새 입력 포트** 를 삭제할 수 있어야 합니다. 새 **입력 포트** 를 선택 하 고 **구성 요소의** 다른 위치로 끕니다.

## <a name="see-also"></a>참조

- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [도구 및 도구 상자 사용자 지정](../modeling/customizing-tools-and-the-toolbox.md)
- [회로 다이어그램 샘플 DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

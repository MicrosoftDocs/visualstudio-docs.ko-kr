---
title: 요소 만들기 및 이동 사용자 지정
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a94f1e3321d846578ea42c69e50d48713ff618fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547266"
---
# <a name="customizing-element-creation-and-movement"></a>요소 만들기 및 이동 사용자 지정

도구 상자 또는 붙여넣기 또는 이동 작업에서 요소를 다른 페이지로 끌 수 있습니다. 지정한 관계를 사용 하 여 이동 된 요소를 대상 요소에 연결할 수 있습니다.

요소 병합 지시문 (EMD)은 하나의 모델 요소가 다른 모델 요소에 *병합* 될 때 발생 하는 결과를 지정 합니다. 이런 상황은 다음과 같은 경우에 발생합니다.

- 사용자가 도구 상자에서 다이어그램 또는 모양으로 끌어 옵니다.

- 사용자가 탐색기 또는 구획 도형에서 추가 메뉴를 사용 하 여 요소를 만듭니다.

- 사용자가 한 스윔 레인에서 다른 스윔 레인로 항목을 이동 합니다.

- 사용자가 요소를 붙여넣습니다.

- 프로그램 코드는 요소 병합 지시문을 호출 합니다.

만들기 작업은 복사 작업과 다른 것 처럼 보일 수 있지만 실제로는 동일한 방식으로 작동 합니다. 예를 들어 도구 상자에서 요소를 추가 하면 그 프로토타입이 복제 됩니다. 프로토타입은 모델의 다른 부분에서 복사 된 요소와 동일한 방식으로 모델에 병합 됩니다.

EMD의 책임은 개체 또는 개체 그룹을 모델의 특정 위치에 병합 하는 방법을 결정 하는 것입니다. 특히 병합 된 그룹을 모델에 연결 하기 위해 인스턴스화할 관계를 결정 합니다. 또한 속성을 설정 하 고 추가 개체를 만들기 위해 사용자 지정할 수 있습니다.

![DSL&#45;EMD&#95;병합](../modeling/media/dsl-emd_merge.png)

EMD는 포함 관계를 정의할 때 자동으로 생성 됩니다. 사용자가 새 자식 인스턴스를 부모에 추가할 때이 기본 EMD는 관계의 인스턴스를 만듭니다. 예를 들어 사용자 지정 코드를 추가 하 여 이러한 기본 EMDs를 수정할 수 있습니다.

DSL 정의에서 사용자 고유의 EMDs를 추가 하 여 사용자가 병합 된 클래스와 수신 하는 클래스의 다른 조합을 끌거나 붙여 넣을 수도 있습니다.

## <a name="defining-an-element-merge-directive"></a>요소 병합 지시문 정의

도메인 클래스, 도메인 관계, 모양, 연결선 및 다이어그램에 요소 병합 지시문을 추가할 수 있습니다. DSL 탐색기에서 수신 도메인 클래스 아래에 해당 항목을 추가 하거나 찾을 수 있습니다. 수신 클래스는 이미 모델에 있는 요소의 도메인 클래스 이며, 새 요소 또는 복사 된 요소가 병합 됩니다.

![DSL&#45;EMD&#95;세부 정보](../modeling/media/dsl-emd_details.png)

**인덱싱 클래스** 는 수신 하는 클래스의 멤버로 병합 될 수 있는 요소의 도메인 클래스입니다. **서브 클래스에 적용** 을 False로 설정 하지 않으면 인덱싱 클래스의 하위 클래스 인스턴스도이 emd에 의해 병합 됩니다.

Merge 지시문에는 다음과 같은 두 가지 종류가 있습니다.

- **프로세스 병합** 지시문은 새 요소가 트리에 연결 되어야 하는 관계를 지정 합니다.

- **전방 병합** 지시문은 새 요소를 일반적으로 부모 인 다른 수신 요소로 리디렉션합니다.

Merge 지시문에 사용자 지정 코드를 추가할 수 있습니다.

- Set **사용자 지정 허용을 사용** 하 여 사용자 고유의 코드를 추가 하 여 인덱싱 요소의 특정 인스턴스를 대상 요소로 병합할지 여부를 결정 합니다. 사용자가 도구 상자에서 끌면 "유효 하지 않은" 포인터가 코드에서 병합을 허용 하지 않는 경우를 표시 합니다.

   예를 들어 수신 요소가 특정 상태에 있는 경우에만 병합을 허용할 수 있습니다.

- Set **사용자 지정 병합을 사용** 하 여 병합 수행 시 모델에 대 한 변경 내용을 정의 하는 고유한 코드를 추가 합니다.

   예를 들어 모델의 새 위치에 있는 데이터를 사용 하 여 병합 된 요소에 속성을 설정할 수 있습니다.

> [!NOTE]
> 사용자 지정 병합 코드를 작성 하는 경우이 EMD를 사용 하 여 수행 된 병합에만 영향을 줍니다. 동일한 형식의 개체를 병합 하는 다른 EMDs가 있거나 EMDS를 사용 하지 않고 이러한 개체를 만드는 다른 사용자 지정 코드가 있는 경우 사용자 지정 병합 코드의 영향을 받지 않습니다.
>
> 사용자 지정 코드에서 새 요소나 새 관계를 항상 처리 하는지 확인 하려는 경우 `AddRule` 포함 관계 및 `DeleteRule` 요소의 도메인 클래스에 대 한을 정의 하는 것이 좋습니다. 자세한 내용은 [모델 내에서 변경 내용 전파 규칙](../modeling/rules-propagate-changes-within-the-model.md)을 참조 하세요.

## <a name="example-defining-an-emd-without-custom-code"></a>예: 사용자 지정 코드 없이 EMD 정의

다음 예제에서는 사용자가 도구 상자에서 기존 모양으로 끌어 요소와 연결선을 동시에 만들 수 있습니다. 이 예에서는 EMD를 DSL 정의에 추가 합니다. 이 수정 작업을 수행 하기 전에 사용자가 도구를 다이어그램으로 끌 수 있지만 기존 셰이프에는 끌어 오지 않습니다.

사용자가 요소를 다른 요소에 붙여넣을 수도 있습니다.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>사용자가 요소와 연결선을 동시에 만들 수 있도록 하려면

1. **최소 언어** 솔루션 템플릿을 사용 하 여 새 DSL을 만듭니다.

    이 DSL을 실행 하면 셰이프 사이에 모양과 연결선을 만들 수 있습니다. 도구 상자에서 기존 모양으로 새 **ExampleElement** 셰이프를 끌어올 수 없습니다.

2. 사용자가 요소를 셰이프에 병합 하도록 하려면 `ExampleElement` 도메인 클래스에 새 EMD를 만듭니다 `ExampleElement` .

   1. **DSL 탐색기**에서 **도메인 클래스**를 확장 합니다. 마우스 오른쪽 단추로 클릭 한 `ExampleElement` 다음 **새 요소 병합 지시문 추가**를 클릭 합니다.

   2. 새 EMD의 세부 정보를 볼 수 있도록 **DSL 세부 정보** 창이 열려 있는지 확인 합니다. (메뉴: **보기**, **다른 창**, **DSL 세부 정보**)

3. DSL 정보 창에서 **인덱싱 클래스** 를 설정 하 여 개체에 병합할 수 있는 요소 클래스를 정의 `ExampleElement` 합니다.

    이 예에서는 `ExampleElements` 사용자가 새 요소를 기존 요소로 끌어올 수 있도록를 선택 합니다.

    인덱싱 클래스는 DSL 탐색기에서 EMD의 이름이 됩니다.

4. **링크를 만들어 병합 처리**에서 두 개의 경로를 추가 합니다.

   - 한 경로는 새 요소를 부모 모델에 연결 합니다. 입력 해야 하는 경로 식은 기존 요소에서 부모 모델과의 포함 관계를 통해 탐색 합니다. 마지막으로 새 요소가 할당 될 새 링크의 역할을 지정 합니다. 경로는 다음과 같습니다.

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - 다른 경로는 새 요소를 기존 요소에 연결 합니다. 경로 식은 참조 관계와 새 요소가 할당 될 역할을 지정 합니다. 이 경로는 다음과 같습니다.

      `ExampleElementReferencesTargets.Sources`

      경로 탐색 도구를 사용 하 여 각 경로를 만들 수 있습니다.

      1. **경로에 링크를 만들어 병합 처리**에서를 클릭 **\<add path>** 합니다.

      2. 목록 항목의 오른쪽에 있는 드롭다운 화살표를 클릭 합니다. 트리 뷰가 나타납니다.

      3. 트리의 노드를 확장 하 여 지정 하려는 경로를 구성 합니다.

5. DSL 테스트:

   1. **F5** 키를 눌러 솔루션을 다시 빌드하고 실행 합니다.

        생성 된 코드는 새 DSL 정의를 준수 하도록 텍스트 템플릿에서 업데이트 되기 때문에 다시 작성 하는 것이 평소 보다 더 오래 걸립니다.

   2. Visual Studio의 실험적 인스턴스가 시작 되 면 DSL의 모델 파일을 엽니다. 몇 가지 예제 요소를 만듭니다.

   3. **예제 요소** 도구에서 기존 모양으로 끌어 옵니다.

        새 셰이프가 나타나고 연결선을 사용 하 여 기존 셰이프에 연결 됩니다.

   4. 기존 셰이프를 복사 합니다. 다른 셰이프를 선택 하 고 붙여 넣습니다.

        첫 번째 셰이프의 복사본이 생성 됩니다.  새 이름을 가지 며 커넥터를 사용 하 여 두 번째 셰이프에 연결 됩니다.

이 절차에서 다음 사항을 확인 합니다.

- 요소 병합 지시문을 만들어 요소 클래스에서 다른 모든 요소를 허용 하도록 허용할 수 있습니다. EMD는 수신 도메인 클래스에서 만들어지며, 허용 된 도메인 클래스는 **인덱스 클래스** 필드에 지정 됩니다.

- 경로를 정의 하 여 새 요소를 기존 모델에 연결 하는 데 사용할 링크를 지정할 수 있습니다.

     지정 하는 링크에는 포함 관계 하나가 포함 되어야 합니다.

- EMD는 도구 상자에서 만드는 작업과 붙여넣기 작업에 모두 영향을 줍니다.

     새 요소를 만드는 사용자 지정 코드를 작성 하는 경우 메서드를 사용 하 여 EMD를 명시적으로 호출할 수 있습니다 `ElementOperations.Merge` . 이렇게 하면 코드에서 다른 작업과 동일한 방식으로 새 요소를 모델에 연결 합니다. 자세한 내용은 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)을 참조 하세요.

## <a name="example-adding-custom-accept-code-to-an-emd"></a>예: EMD에 사용자 지정 수락 코드 추가

EMD에 사용자 지정 코드를 추가 하 여 더 복잡 한 병합 동작을 정의할 수 있습니다. 이 간단한 예제에서는 사용자가 보다 고정 된 수의 요소를 다이어그램에 추가할 수 없습니다. 이 예제에서는 포함 관계와 함께 제공 되는 기본 EMD를 수정 합니다.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>사용자 지정 수락 코드를 작성 하 여 사용자가 추가할 수 있는 항목을 제한 하려면

1. **최소 언어** 솔루션 템플릿을 사용 하 여 DSL을 만듭니다. DSL 정의 다이어그램을 엽니다.

2. DSL 탐색기에서 **도메인 클래스**, `ExampleModel` , **요소 병합 지시문**을 차례로 확장 합니다. 이라는 요소 병합 지시문을 선택 `ExampleElement` 합니다.

     이 EMD는 사용자가 `ExampleElement` 도구 상자에서 끌어와 같이 모델에 새 개체를 만들 수 있는 방법을 제어 합니다.

3. **DSL 정보** 창에서 **사용자 지정 허용 사용**을 선택 합니다.

4. 솔루션을 다시 빌드합니다. 생성 된 코드가 모델에서 업데이트 되기 때문에이는 평소 보다 시간이 오래 걸립니다.

     "ElementMergeSample. ExampleElement에 CanMergeExampleElement에 대 한 정의가 포함 되어 있지 않습니다."와 비슷한 빌드 오류가 보고 됩니다.

     메서드를 구현 해야 합니다 `CanMergeExampleElement` .

5. **Dsl** 프로젝트에서 새 코드 파일을 만듭니다. 해당 콘텐츠를 다음 코드로 바꾸고 네임 스페이스를 프로젝트의 네임 스페이스로 변경 합니다.

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

    이 간단한 예제에서는 부모 모델에 병합할 수 있는 요소의 수를 제한 합니다. 더 흥미로운 조건을 위해 메서드에서는 수신 개체의 속성 및 링크를 검사할 수 있습니다. 에서 전달 되는 병합 요소의 속성을 검사할 수도 있습니다 <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . 에 대 한 자세한 내용은 `ElementGroupPrototypes` [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md)을 참조 하세요. 모델을 읽는 코드를 작성 하는 방법에 대 한 자세한 내용은 [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)를 참조 하세요.

6. DSL 테스트:

    1. **F5** 키를 눌러 솔루션을 다시 빌드합니다. Visual Studio의 실험적 인스턴스가 열리면 DSL의 인스턴스를 엽니다.

    2. 여러 가지 방법으로 새 요소를 만듭니다.

        - **예제 요소** 도구에서 다이어그램으로 끌어 옵니다.

        - **예제 모델 탐색기**에서 루트 노드를 마우스 오른쪽 단추로 클릭 한 다음 **새 예제 요소 추가**를 클릭 합니다.

        - 다이어그램에서 요소를 복사 하 여 붙여넣습니다.

    3. 이러한 방법 중 하나를 사용 하 여 모델에 4 개 이상의 요소를 추가할 수 있는지 확인 합니다. 이는 모두 요소 병합 지시문을 사용 하기 때문입니다.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>예: EMD에 사용자 지정 병합 코드 추가

사용자 지정 병합 코드에서 사용자가 도구를 끌거나 요소에 붙여넣을 때 발생 하는 작업을 정의할 수 있습니다. 사용자 지정 병합을 정의 하는 방법에는 다음 두 가지가 있습니다.

1. Set **사용자 지정 병합을 사용 하** 고 필요한 코드를 제공 합니다. 코드는 생성 된 병합 코드를 대체 합니다. 병합이 수행 하는 작업을 완전히 다시 정의 하려면이 옵션을 사용 합니다.

2. `MergeRelate`메서드를 재정의 하 고 필요에 따라 메서드를 재정의 합니다 `MergeDisconnect` . 이렇게 하려면 도메인 클래스의 **이중 파생 클래스 생성** 속성을 설정 해야 합니다. 코드는 기본 클래스에서 생성 된 병합 코드를 호출할 수 있습니다. 병합을 수행한 후 추가 작업을 수행 하려는 경우이 옵션을 사용 합니다.

   이러한 방법은이 EMD를 사용 하 여 수행 되는 병합에만 영향을 줍니다. 병합 된 요소를 만들 수 있는 모든 방법에 영향을 주려면 `AddRule` 포함 관계와 병합 된 도메인 클래스에 대 한을 정의 하는 방법을 사용할 수 있습니다 `DeleteRule` . 자세한 내용은 [모델 내에서 변경 내용 전파 규칙](../modeling/rules-propagate-changes-within-the-model.md)을 참조 하세요.

### <a name="to-override-mergerelate"></a>MergeRelate를 재정의 하려면

1. DSL 정의에서 코드를 추가할 EMD를 정의 했는지 확인 합니다. 원하는 경우 이전 섹션에 설명 된 대로 경로를 추가 하 고 사용자 지정 수락 코드를 정의할 수 있습니다.

2. DslDefinition 다이어그램에서 병합의 수신 클래스를 선택 합니다. 일반적으로 포함 관계의 소스 끝에 있는 클래스입니다.

     예를 들어 최소 언어 솔루션에서 생성 된 DSL에서을 선택 `ExampleModel` 합니다.

3. **속성** 창에서 **Double 파생** 을 **true**로 설정 합니다.

4. 솔루션을 다시 빌드합니다.

5. **Dsl\generated Files\DomainClasses.cs**의 콘텐츠를 검사 합니다. 이라는 메서드를 검색 `MergeRelate` 하 고 해당 내용을 검사 합니다. 이렇게 하면 고유한 버전을 작성 하는 데 도움이 됩니다.

6. 새 코드 파일에서 수신 하는 클래스에 대 한 partial 클래스를 작성 하 고 메서드를 재정의 `MergeRelate` 합니다. 기본 메서드를 호출 해야 합니다. 예:

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

### <a name="to-write-custom-merge-code"></a>사용자 지정 병합 코드를 작성 하려면

1. **Dsl\generated Code\DomainClasses.cs**에서 라는 메서드를 검사 `MergeRelate` 합니다. 이러한 메서드는 새 요소와 기존 모델 간에 링크를 만듭니다.

    또한 라는 메서드를 검사 `MergeDisconnect` 합니다. 이러한 메서드는 모델을 삭제할 때 모델에서 요소의 연결을 해제 합니다.

2. **DSL 탐색기**에서 사용자 지정 하려는 요소 병합 지시문을 선택 하거나 만듭니다. **DSL 정보** 창에서 설정 **사용자 지정 병합을 사용**합니다.

    이 옵션을 설정 하면 **병합** 및 **전달 병합** 옵션이 무시 됩니다. 코드가 대신 사용 됩니다.

3. 솔루션을 다시 빌드합니다. 생성 된 코드 파일이 모델에서 업데이트 되기 때문에이는 평소 보다 시간이 더 오래 걸립니다.

    오류 메시지가 표시 됩니다. 오류 메시지를 두 번 클릭 하면 생성 된 코드의 지침이 표시 됩니다. 이 지침에서는 `MergeRelate` *YourDomainClass* 및 `MergeDisconnect` *YourDomainClass* 의 두 가지 메서드를 제공 하도록 요청 합니다.

4. 별도의 코드 파일에서 partial 클래스 정의에 메서드를 작성 합니다. 앞서 검사 한 예제에서는 필요한 항목을 제안 해야 합니다.

   사용자 지정 병합 코드는 개체 및 관계를 직접 만드는 코드에는 영향을 주지 않으며 다른 EMDs에는 영향을 주지 않습니다. 요소가 생성 되는 방법에 관계 없이 추가 변경 내용이 구현 되도록 하려면 및를 대신 작성 하는 것이 좋습니다 `AddRule` `DeleteRule` . 자세한 내용은 [모델 내에서 변경 내용 전파 규칙](../modeling/rules-propagate-changes-within-the-model.md)을 참조 하세요.

## <a name="redirecting-a-merge-operation"></a>병합 작업 리디렉션

전방 병합 지시문은 병합 작업의 대상을 리디렉션합니다. 일반적으로 새 대상은 초기 대상의 포함 부모입니다.

예를 들어 구성 요소 다이어그램 템플릿을 사용 하 여 만든 DSL에서 포트는 구성 요소에 포함 됩니다. 포트는 구성 요소 셰이프의 가장자리에 작은 모양으로 표시 됩니다. 사용자는 포트 도구를 구성 요소 셰이프로 끌어 포트를 만듭니다. 그러나 경우에 따라 사용자가 실수로 포트 도구를 구성 요소 대신 기존 포트로 끌어 오면 작업이 실패 합니다. 이는 기존 포트가 여러 개 있는 경우에 쉬운 실수입니다. 사용자가이 걸림돌를 방지 하는 데 도움이 되도록 기존 포트로 포트를 끌 수 있지만 작업을 부모 구성 요소로 리디렉션할 수 있습니다. 작업은 대상 요소가 구성 요소인 것 처럼 작동 합니다.

구성 요소 모델 솔루션에서 전방 병합 지시문을 만들 수 있습니다. 원본 솔루션을 컴파일 및 실행 하는 경우 사용자가 **도구 상자** 에서 원하는 수의 **입력 포트** 또는 **출력 포트** 요소를 **구성** 요소 요소에 끌어 놓을 수 있습니다. 그러나 포트를 기존 포트로 끌어올 수 없습니다. 사용할 수 없는 포인터는이 이동이 사용 되지 않도록 경고 합니다. 그러나 기존 **입력 포트** 에서 실수로 삭제 된 포트가 **Component** 요소로 전달 되도록 전방 병합 지시문을 만들 수 있습니다.

### <a name="to-create-a-forward-merge-directive"></a>전방 병합 지시문을 만들려면

1. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]구성 요소 모델 템플릿을 사용 하 여 솔루션을 만듭니다.

2. DslDefinition. dsl을 열어 **Dsl 탐색기** 를 표시 합니다.

3. **DSL 탐색기**에서 **도메인 클래스**를 확장 합니다.

4. **Componentport** abstract 도메인 클래스는 **InPort** 및 **outport**의 기본 클래스입니다. **Componentport** 를 마우스 오른쪽 단추로 클릭 한 다음 **새 요소 병합 지시문 추가**를 클릭 합니다.

    새 **요소 병합 지시문** 노드가 **요소 병합** 지시문 노드 아래에 나타납니다.

5. **요소 병합 지시문** 노드를 선택 하 고 **DSL 세부 정보** 창을 엽니다.

6. 인덱싱 클래스 목록에서 **Componentport**를 선택 합니다.

7. **다른 도메인 클래스로 병합 전달을**선택 합니다.

8. 경로 선택 목록에서 **Componentport**를 확장 하 고 **ComponentHasPorts**를 확장 한 다음 **구성 요소**를 선택 합니다.

    새 경로는 다음과 유사 합니다.

    **ComponentHasPorts/! 구성 요소**

9. 솔루션을 저장 한 다음 **솔루션 탐색기** 도구 모음에서 맨 오른쪽 단추를 클릭 하 여 템플릿을 변환 합니다.

10. 솔루션을 빌드하고 실행합니다. Visual Studio의 새 인스턴스가 나타납니다.

11. **솔루션 탐색기**에서 샘플. mydsl을 엽니다. 다이어그램 및 **Componentlanguage 도구 상자가** 나타납니다.

12. **입력 포트** 를 **도구 상자** 에서 다른 **입력 포트로** 끌어 옵니다. 그런 다음 **outputport** 를 **inputport** 로 끈 다음 다른 **outputport**로 끕니다.

     사용할 수 없는 포인터는 표시 되지 않으며 기존 **입력 포트에 새 입력 포트** 를 삭제할 수 있어야 합니다. 새 **입력 포트** 를 선택 하 고 **구성 요소의**다른 위치로 끕니다.

## <a name="see-also"></a>참조

- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [도구 및 도구 상자 사용자 지정](../modeling/customizing-tools-and-the-toolbox.md)
- [회로 다이어그램 샘플 DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

---
title: 도메인 속성 값 변경 처리기
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2f23984d6c4723b020b361e1da30363442966ea7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594710"
---
# <a name="domain-property-value-change-handlers"></a>도메인 속성 값 변경 처리기

Visual Studio 도메인별 언어에서 도메인 속성 값이 변경 되 면 `OnValueChanging()` 및 `OnValueChanged()` 메서드가 도메인 속성 처리기에서 호출 됩니다. 변경에 응답하려면 이러한 메서드를 재정의하면 됩니다.

## <a name="override-the-property-handler-methods"></a>속성 처리기 메서드 재정의

DSL의 각 도메인 속성은 부모 도메인 클래스 내에 중첩된 클래스를 통해 처리됩니다. 해당 이름은 *PropertyName*propertyhandler 형식 뒤에 나옵니다. **Dsl\generated Code\DomainClasses.cs**파일에서이 속성 처리기 클래스를 검사할 수 있습니다. 해당 클래스에서는 값이 변경되기 직전에 `OnValueChanging()`이 호출되고 값이 변경된 직후에 `OnValueChanged()`가 호출됩니다.

예를 들어 라는 `Comment` 문자열 도메인 속성 및 라는 정수 속성이 있는 라는 도메인 클래스가 있다고 가정 합니다 `Text` `TextLengthCount` . `TextLengthCount`항상 문자열의 길이를 포함 하도록 하려면 `Text` Dsl 프로젝트에서 별도의 파일에 다음 코드를 작성 하면 됩니다.

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

속성 처리기와 관련하여 유의할 사항은 다음과 같습니다.

- 속성 처리기 메서드는 사용자가 도메인 속성을 변경할 때와 프로그램 코드가 속성에 다른 값을 할당할 때 모두 호출됩니다.

- 메서드는 값이 실제로 변경될 때만 호출됩니다. 프로그램 코드가 현재 값과 같은 값을 할당하는 경우에는 처리기가 호출되지 않습니다.

- 계산된 속성 및 사용자 지정 스토리지 도메인 속성에는 OnValueChanged 및 OnValueChanging 메서드가 없습니다.

- 변경 처리기를 사용하여 새 값을 수정할 수는 없습니다. 값을 특정 범위로 제한하는 등의 작업을 수행하려면 `ChangeRule`을 정의합니다.

- 관계의 역할을 나타내는 속성에는 변경 처리기를 추가할 수 없습니다. 대신 관계 클래스에 대해 `AddRule` 및 `DeleteRule`을 정의합니다. 이러한 규칙은 링크를 만들거나 변경할 때 트리거됩니다. 자세한 내용은 [모델 내에서 변경 내용 전파 규칙](../modeling/rules-propagate-changes-within-the-model.md)을 참조 하세요.

### <a name="changes-in-and-out-of-the-store"></a>Store 내부 및 외부의 변경 사항

속성 처리기 메서드는 변경을 시작한 트랜잭션 내에서 호출됩니다. 그러므로 새 트랜잭션을 열지 않고 Store에서 추가로 변경할 수 있습니다. 변경하면 처리기가 추가로 호출될 수 있습니다.

트랜잭션 실행을 취소하거나 다시 실행하거나 롤백할 때는 Store에서 변경하면 안 됩니다. 즉, 모델 요소/관계/모양/연결선/다이어그램 또는 해당 속성을 변경해서는 안 됩니다.

또한 파일에서 모델을 로드할 때는 보통 값을 업데이트하지 않습니다.

따라서 모델 변경 시에는 다음과 같은 테스트를 수행해야 합니다.

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

반면에 속성 처리기가 파일, 데이터베이스 또는 Store에 포함되지 않은 변수 등의 Store 외부 항목으로 변경 내용을 전파하는 경우에는 항상 사용자가 실행 취소 또는 다시 실행을 호출할 때 외부 값이 업데이트되도록 변경해야 합니다.

### <a name="cancel-a-change"></a>변경 취소

변경을 방지하려는 경우 현재 트랜잭션을 롤백하면 됩니다. 예를 들어 속성이 특정 범위 내에 유지되도록 하려면 다음 코드를 사용합니다.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>대체 기술: 계산된 속성

위의 예에서는 OnValueChanged()를 사용하여 도메인 속성 간에 값을 전파하는 방법을 보여줍니다. 이 속성에는 자체 저장 값이 있습니다.

대신 파생 속성을 계산된 속성으로 정의할 수 있습니다. 이 경우 속성은 자체 스토리지를 포함하지 않으며 속성의 값이 필요할 때마다 정의 기능을 평가합니다. 자세한 내용은 [계산 된 저장소 속성 및 사용자 지정 저장소 속성](../modeling/calculated-and-custom-storage-properties.md)을 참조 하세요.

이전 예제 대신 **Kind** `TextLengthCount` DSL 정의에서 **계산** 되는의 Kind 필드를 설정할 수 있습니다. 이 도메인 속성에 대해 고유한 **Get** 메서드를 제공 합니다. **Get** 메서드는 문자열의 현재 길이를 반환 합니다 `Text` .

그러나 계산된 속성을 사용하는 경우 값을 사용할 때마다 식을 평가하므로 성능상의 문제가 발생할 수 있다는 단점이 있습니다. 또한 계산된 속성에는 OnValueChanging() 및 OnValueChanged()가 없습니다.

### <a name="alternative-technique-change-rules"></a>대체 기술: 변경 규칙

ChangeRule를 정의 하는 경우 속성 값이 변경 되는 트랜잭션의 끝에서 실행 됩니다.  자세한 내용은 [모델 내에서 변경 내용 전파 규칙](../modeling/rules-propagate-changes-within-the-model.md)을 참조 하세요.

트랜잭션 하나에서 여러 항목을 변경하는 경우 모든 변경이 완료되면 ChangeRule이 실행됩니다. 반대로 OnValue ... 메서드는 일부 변경 내용이 수행 되지 않았을 때 실행 됩니다. 그러므로 수행하려는 작업에 따라서 ChangeRule을 사용하는 것이 보다 적절할 수 있습니다.

ChangeRule를 사용 하 여 속성의 새 값을 조정 하 여 특정 범위 내에 유지할 수도 있습니다.

> [!WARNING]
> 규칙이 Store 콘텐츠를 변경하면 다른 규칙과 속성 처리기가 트리거될 수 있습니다. 규칙을 트리거한 속성이 규칙에 의해 변경되면 해당 규칙이 다시 호출됩니다. 규칙 정의로 인해 무한 트리거가 발생하지 않는지 확인해야 합니다.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>예제

### <a name="description"></a>설명

다음 예에서는 도메인 속성의 속성 처리기를 재정의하고 `ExampleElement` 도메인 클래스의 속성이 변경된 경우 사용자에게 알림을 표시합니다.

### <a name="code"></a>코드

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```

---
title: '방법: 트랜잭션을 사용하여 모델 업데이트'
description: 트랜잭션에서 저장소에 대한 변경 내용이 그룹으로 처리되는지 확인하고 트랜잭션을 사용하여 모델을 업데이트하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e91e569573076d1614a9fa946b67f3bda01e6fba
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390544"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>방법: 트랜잭션을 사용하여 모델 업데이트
트랜잭션은 저장소에 대한 변경 내용이 그룹으로 처리되도록 합니다. 그룹화되는 변경 내용은 단일 단위로 커밋하거나 롤백할 수 있습니다.

 프로그램 코드가 Visual Studio 시각화 및 모델링 SDK의 Store에서 요소를 수정, 추가 또는 삭제할 때마다 트랜잭션 내에서 수정, 추가 또는 삭제해야 합니다. 변경이 발생할 때 Store와 연결된 의 활성 인스턴스가 있어야 <xref:Microsoft.VisualStudio.Modeling.Transaction> 합니다. 이는 모든 모델 요소, 관계, 도형, 다이어그램 및 해당 속성에 적용됩니다.

 트랜잭션 메커니즘을 사용하면 일관성 없는 상태를 방지할 수 있습니다. 트랜잭션 중에 오류가 발생하면 모든 변경 내용이 롤백됩니다. 사용자가 실행 취소 명령을 수행하는 경우 각 최근 트랜잭션은 단일 단계로 처리됩니다. 사용자가 명시적으로 별도의 트랜잭션에 배치하지 않는 한 최근 변경의 일부를 실행 취소할 수 없습니다.

## <a name="opening-a-transaction"></a>트랜잭션 열기
 트랜잭션을 관리하는 가장 편리한 방법은 `using` 문으로 묶인 문을 사용하는 것입니다. `try...catch`

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 변경 중에 최종을 방지하는 예외가 `Commit()` 발생하면 Store가 이전 상태로 다시 설정됩니다. 이렇게 하면 오류가 모델을 일관되지 않은 상태로 두지 않도록 할 수 있습니다.

 한 트랜잭션 내에서 원하는 수의 변경 내용을 만들 수 있습니다. 활성 트랜잭션 내에서 새 트랜잭션을 열 수 있습니다. 중첩된 트랜잭션은 포함하는 트랜잭션이 종료되기 전에 커밋하거나 롤백해야 합니다. 자세한 내용은 속성에 대한 예제를 <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> 참조하세요.

 변경 내용을 영구적으로 만들려면 `Commit` 트랜잭션이 삭제되기 전에 트랜잭션을 삭제해야 합니다. 트랜잭션 내에서 포착되지 않은 예외가 발생하면 저장소가 변경되기 전에 해당 상태로 다시 설정됩니다.

## <a name="rolling-back-a-transaction"></a>트랜잭션 롤백
 저장소가 트랜잭션 전 상태로 유지되거나 해당 상태로 되돌아가도록 하려면 다음 전술 중 하나를 사용할 수 있습니다.

1. 트랜잭션 범위 내에서 포착되지 않는 예외를 발생합니다.

2. 트랜잭션을 명시적으로 롤백합니다.

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>트랜잭션이 저장소가 아닌 개체에 영향을 미치지 않음
 트랜잭션은 Store의 상태만 제어합니다. DSL 정의 외부의 일반 형식으로 선언한 파일, 데이터베이스 또는 개체와 같은 외부 항목에 대한 부분 변경 내용을 실행 취소할 수 없습니다.

 예외로 이러한 변경이 Store와 일치하지 않을 수 있는 경우 예외 처리기에서 해당 가능성을 처리해야 합니다. 외부 리소스가 Store 개체와 동기화된 상태로 유지되도록 하는 한 가지 방법은 이벤트 처리기를 사용하여 각 외부 개체를 저장소 내 요소에 결합하는 것입니다. 자세한 내용은 [이벤트 처리기 모델 외부에서 변경 내용 전파를 참조하세요.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

## <a name="rules-fire-at-the-end-of-a-transaction"></a>트랜잭션이 끝날 때 규칙이 발생합니다.
 트랜잭션이 종료되면 트랜잭션이 삭제되기 전에 저장소의 요소에 연결된 규칙이 발생합니다. 각 규칙은 변경된 모델 요소에 적용되는 메서드입니다. 예를 들어 모델 요소가 변경된 경우 Shape의 상태를 업데이트하고 모델 요소를 만들 때 Shape를 만드는 "수정" 규칙이 있습니다. 지정된 발생 순서가 없습니다. 규칙을 변경하면 다른 규칙이 발생합니다.

 사용자 고유의 규칙을 정의할 수 있습니다. 규칙에 대한 자세한 내용은 [변경 내용에 응답 및 전파를 참조하세요.](../modeling/responding-to-and-propagating-changes.md)

 실행 취소, 다시 실행 또는 롤백 명령 후에는 규칙이 실행되지 않습니다.

## <a name="transaction-context"></a>트랜잭션 컨텍스트
 각 트랜잭션에는 원하는 정보를 저장할 수 있는 사전이 있습니다.

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 이 방법은 규칙 간에 정보를 전송하는 데 특히 유용합니다.

## <a name="transaction-state"></a>트랜잭션 상태
 경우에 따라 트랜잭션을 실행 취소하거나 다시 실행하여 변경이 발생하는 경우 변경 전파를 피해야 합니다. 예를 들어 Store에서 다른 값을 업데이트할 수 있는 속성 값 처리기를 작성하는 경우 이런 일이 발생할 수 있습니다. 실행 취소 작업은 Store의 모든 값을 이전 상태로 다시 설정하므로 업데이트된 값을 계산할 필요가 없습니다. 다음 코드를 사용합니다.

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 저장소가 처음에 파일에서 로드될 때 규칙이 발생합니다. 이러한 변경 내용에 응답하지 않으려면 다음을 사용합니다.

```csharp
if (!this.Store.InSerializationTransaction) {...}
```

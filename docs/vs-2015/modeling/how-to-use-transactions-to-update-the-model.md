---
title: '방법: 트랜잭션을 사용 하 여 모델 업데이트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cd66c62d74bfe63d8376b5520b42cb20c8c0a3a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651615"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>방법: 트랜잭션을 사용하여 모델 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

트랜잭션은 저장소에 대 한 변경 내용이 하나의 그룹으로 처리 되는지 확인 합니다. 그룹화 된 변경 내용은 단일 단위로 커밋되거나 롤백될 수 있습니다.

 프로그램 코드에서 시각화 및 모델링 SDK의 저장소에 있는 모든 요소를 수정, 추가 또는 삭제할 때마다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 트랜잭션 내에서이 작업을 수행 해야 합니다. <xref:Microsoft.VisualStudio.Modeling.Transaction>변경이 발생 하는 경우 저장소와 연결 된의 활성 인스턴스가 있어야 합니다. 이는 모든 모델 요소, 관계, 모양, 다이어그램 및 해당 속성에 적용 됩니다.

 트랜잭션 메커니즘은 일관 되지 않은 상태를 방지 하는 데 도움이 됩니다. 트랜잭션 중에 오류가 발생 하면 모든 변경 내용이 롤백됩니다. 사용자가 실행 취소 명령을 수행 하면 각 최근 트랜잭션이 단일 단계로 처리 됩니다. 사용자가 별도의 트랜잭션에 명시적으로 배치 하지 않는 한 사용자는 최근 변경 내용의 일부를 실행 취소할 수 없습니다.

## <a name="opening-a-transaction"></a>트랜잭션 열기
 트랜잭션을 관리 하는 가장 편리한 방법은 문에 포함 된 문을 사용 하는 것입니다 `using` `try...catch` .

```
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

 변경 하는 동안 최종을 방지 하는 예외가 `Commit()` 발생 하면 저장소는 이전 상태로 다시 설정 됩니다. 이렇게 하면 오류가 모델을 일관 되지 않은 상태로 유지 하지 않도록 할 수 있습니다.

 한 트랜잭션 내에서 원하는 수의 변경 작업을 수행할 수 있습니다. 활성 트랜잭션 내에서 새 트랜잭션을 열 수 있습니다. 중첩 된 트랜잭션은 포함 하는 트랜잭션이 끝나기 전에 커밋되거나 롤백해야 합니다. 자세한 내용은 속성의 예제를 참조 하세요 <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> .

 변경 내용을 영구적으로 적용 하려면 `Commit` 트랜잭션이 삭제 되기 전에 수행 해야 합니다. 트랜잭션 내에서 catch 되지 않는 예외가 발생 하면 저장소는 변경 전 상태로 다시 설정 됩니다.

## <a name="rolling-back-a-transaction"></a>트랜잭션 롤백
 저장소를 트랜잭션 전 상태로 유지 하거나 해당 상태로 되돌리기 위해 다음 방법 중 하나를 사용할 수 있습니다.

1. 트랜잭션의 범위 내에서 catch 되지 않은 예외를 발생 시킵니다.

2. 트랜잭션을 명시적으로 롤백합니다.

    ```
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>트랜잭션은 저장소 개체가 아닌 개체에 영향을 주지 않습니다.
 트랜잭션은 저장소의 상태만 제어 합니다. DSL 정의 외부에서 일반 형식을 사용 하 여 선언 된 파일, 데이터베이스 또는 개체와 같은 외부 항목에 대 한 일부 변경 내용을 실행 취소할 수 없습니다.

 예외로 인해 이러한 변경 내용이 저장소와 일치 하지 않을 수 있는 경우 예외 처리기에서 해당 가능성을 처리 해야 합니다. 외부 리소스가 저장소 개체와 동기화 상태를 유지 하도록 하는 한 가지 방법은 이벤트 처리기를 사용 하 여 각 외부 개체를 저장소 요소에 두는 것입니다. 자세한 내용은 [이벤트 처리기가 모델 외부에서 변경 내용을 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)하는 방법을 참조 하세요.

## <a name="rules-fire-at-the-end-of-a-transaction"></a>트랜잭션이 끝날 때 규칙이 발생 합니다.
 트랜잭션이 종료 될 때까지 트랜잭션이 삭제 되기 전에 저장소의 요소에 연결 된 규칙이 발생 합니다. 각 규칙은 변경 된 모델 요소에 적용 되는 메서드입니다. 예를 들어 모델 요소가 변경 된 경우 셰이프의 상태를 업데이트 하는 "수정" 규칙이 있으며 모델 요소가 만들어질 때 셰이프를 만듭니다. 지정 된 실행 순서가 없습니다. 규칙에서 변경한 내용은 다른 규칙을 발생 시킬 수 있습니다.

 사용자 고유의 규칙을 정의할 수 있습니다. 규칙에 대 한 자세한 내용은 [변경 내용에 대 한 응답 및 전파](../modeling/responding-to-and-propagating-changes.md)를 참조 하세요.

 실행 취소, 다시 실행 또는 롤백 명령 후에는 규칙이 실행 되지 않습니다.

## <a name="transaction-context"></a>트랜잭션 컨텍스트
 각 트랜잭션에는 원하는 모든 정보를 저장할 수 있는 사전이 있습니다.

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 규칙 간에 정보를 전송 하는 데 특히 유용 합니다.

## <a name="transaction-state"></a>트랜잭션 상태
 경우에 따라 트랜잭션을 실행 취소 하거나 다시 실행 하 여 변경이 발생 하는 경우 변경 내용 전파를 방지 해야 합니다. 예를 들어 저장소의 다른 값을 업데이트할 수 있는 속성 값 처리기를 작성 하는 경우이 문제가 발생할 수 있습니다. 실행 취소 작업은 저장소의 모든 값을 이전 상태로 다시 설정 하므로 업데이트 된 값을 계산할 필요가 없습니다. 이 코드를 사용 합니다.

```
if (!this.Store.InUndoRedoOrRollback) {...}
```

 저장소를 처음 파일에서 로드 하는 경우 규칙을 실행할 수 있습니다. 이러한 변경 내용에 대 한 응답을 방지 하려면 다음을 사용 합니다.

```
if (!this.Store.InSerializationTransaction) {...}

```

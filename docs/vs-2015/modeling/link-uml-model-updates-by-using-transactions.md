---
title: 트랜잭션을 사용 하 여 UML 모델 업데이트 연결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8930bba76830a6116c3182f3fb2936cd4f1a3e47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657603"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>트랜잭션을 사용하여 UML 모델 업데이트 연결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 UML 디자이너에 대 한 확장을 정의 하는 경우 여러 변경 내용을 *연결 된 실행 취소 컨텍스트*라는 단일 트랜잭션으로 그룹화 할 수 있습니다. UML 모델을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 기본적으로 코드에서 모델에 수행하는 각 수정 작업은 사용자가 개별적으로 취소할 수 있습니다. 예를 들어 두 UML 클래스의 이름을 교환하는 메뉴 명령을 정의하는 경우 사용자가 명령을 호출한 다음 하나의 실행 취소를 수행할 수 있습니다. 이렇게 하면 하나의 이름 변경만 취소되고 다른 이름 변경은 취소되지 않으므로 모델이 의도하지 않은 상태가 됩니다.

 이를 방지하기 위해 코드에서 트랜잭션을 통해 일련의 변경 작업을 수행할 수 있습니다. 이렇게 하면 변경 내용이 사용자에게 단일 변경으로 표시됩니다. 이후 실행 취소 명령을 실행하면 일련의 전체 작업이 취소됩니다.

 코드에서 예외를 발생시키거나 트랜잭션을 중단하여 부분적으로 완료된 변경 집합을 취소할 수 있다는 이점도 있습니다.

## <a name="to-group-changes-into-a-single-transaction"></a>변경 내용을 단일 트랜잭션으로 그룹화하려면
 프로젝트 참조에 이 .NET 어셈블리가 포함되어 있는지 확인합니다.

 **VisualStudio입니다. [version] .dll**

 클래스 내에서 <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext> 형식의 가져온 속성을 선언합니다.

 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`

 `...`

 `class … {`

 `[Import]`

 `public ILinkedUndoContext LinkedUndoContext { get; set; }`

 모델을 수정하는 메서드에서 변경 내용을 트랜잭션으로 묶습니다.

 `using (ILinkedUndoTransaction transaction =`

 `LinkedUndoContext.BeginTransaction("my updates"))`

 `{`

 `// code to update model elements or shapes goes here`

 `transaction.Commit();`

 `}`

 다음을 확인합니다.

- 트랜잭션의 끝에 항상 `Commit()`을 포함해야 합니다. 트랜잭션을 커밋하지 않고 삭제하면 트랜잭션이 롤백됩니다. 즉, 모델이 트랜잭션을 시작할 때의 상태로 복원됩니다.

- 트랜잭션 내에 catch되지 않는 예외가 발생하면 트랜잭션이 롤백됩니다. 트랜잭션의 `using` 블록을 `try…catch` 블록 안에 묶는 것이 자주 사용되는 패턴입니다.

- 트랜잭션을 중첩할 수 있습니다.

- `BeginTransaction()`에 공백이 아닌 임의 이름을 지정할 수 있습니다.

- UML 모델 저장소만 이러한 트랜잭션의 영향을 받습니다. 모델링 트랜잭션은 변수, 파일 및 데이터베이스와 같은 외부 저장소, 레이어 다이어그램 및 모델 코드에 영향을 주지 않습니다.

## <a name="example"></a>예제

```
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Interfaces;
    using Microsoft.VisualStudio.Uml.Classes;
    using Microsoft.VisualStudio.Uml.Extensions;
    using System.Linq;
    using System.ComponentModel.Composition;
 ...
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  public void Execute(IMenuCommand command)
  {
    var selectedShapes =
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;
    string firstName = firstElement.Name;
    // Perform changes inside a transaction so that undo
    // works as a single change.
    using (ILinkedUndoTransaction transaction =
      LinkedUndoContext.BeginTransaction("Swap names"))
    {
        firstElement.Name = lastElement.Name;
        lastElement.Name = firstName;
        transaction.Commit();
    }
 }
```

## <a name="see-also"></a>참고 항목
 [UML API를 사용한 프로그래밍](../modeling/programming-with-the-uml-api.md) [모델링 다이어그램에서 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [uml 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md)

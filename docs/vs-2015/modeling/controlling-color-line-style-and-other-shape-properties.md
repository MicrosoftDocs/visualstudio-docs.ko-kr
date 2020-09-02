---
title: 색, 선 스타일 및 기타 모양 속성 제어 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5d296f5ab3f5c584558b373b57c175fb2bacef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667852"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>색, 선 스타일 및 기타 모양 속성 제어
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Color와 같은 일부 셰이프 속성은 ' 노출 ' 될 수 있습니다. 즉, 셰이프의 도메인 속성에 연결 됩니다. 다른 항목은 직접 제어 해야 합니다.

## <a name="exposing-a-property"></a>속성 노출
 Color와 같은 일부 셰이프 속성은 도메인 속성의 값에 연결할 수 있습니다.

 DSL 정의에서 도형, 연결선 또는 다이어그램 클래스를 선택 합니다. 상황에 맞는 메뉴에서 **노출 추가**를 선택한 다음 원하는 속성 (예: 채우기 색)을 선택 합니다.

 이제 셰이프에는 프로그램 코드 또는 사용자로 설정할 수 있는 도메인 속성이 있습니다.

## <a name="dynamically-updating-an-exposed-property"></a>노출 된 속성을 동적으로 업데이트
 일반적으로 노출 되는 속성을 다른 속성에 따라 결정 하려고 합니다. 예를 들어 특정 도메인 속성이 0 보다 작은 경우 셰이프를 빨간색으로 설정 하려고 할 수 있습니다. 이 종속성을 설정 하려면 [규칙](../modeling/rules-propagate-changes-within-the-model.md)을 만듭니다. 예를 들어:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```

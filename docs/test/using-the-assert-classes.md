---
title: MSTest 어설션 클래스 및 메서드
ms.date: 06/07/2018
ms.topic: reference
helpviewer_keywords:
- Assert classes
- Assert methods
- unit tests, Assert classes
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c36916c79bd783ed2c6ce960b068e85478b9971d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592050"
---
# <a name="use-assert-classes-for-unit-testing"></a>단위 테스트를 위한 Assert 클래스 사용

<xref:Microsoft.VisualStudio.TestTools.UnitTesting> 네임스페이스의 Assert 클래스를 사용하여 특정 기능을 확인합니다. 단위 테스트 메서드는 애플리케이션 코드에서 메서드 코드를 실행하지만, Assert 문을 포함하는 경우에만 코드의 동작이 정확한지 여부를 보고합니다.

## <a name="kinds-of-asserts"></a>어설션의 종류

<xref:Microsoft.VisualStudio.TestTools.UnitTesting> 네임스페이스는 다음과 같은 여러 종류의 Assert 클래스를 제공합니다.

테스트 메서드에서 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName> 클래스의 모든 메서드(예: <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType>)를 호출할 수 있습니다. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 클래스에서는 여러 메서드를 선택할 수 있으며, 이러한 메서드는 대부분 여러 오버로드를 포함합니다.

### <a name="compare-strings-and-collections"></a>문자열 및 컬렉션 비교

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert> 클래스를 사용하여 개체 컬렉션을 비교하고 컬렉션의 상태를 확인합니다.

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert> 클래스를 사용하여 문자열을 비교하고 검사합니다. 이 클래스에는 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=nameWithType>, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Matches%2A?displayProperty=nameWithType> 및 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.StartsWith%2A?displayProperty=nameWithType>과 같은 다양하고 유용한 메서드가 포함되어 있습니다.

### <a name="exceptions"></a>예외

테스트가 실패할 때마다 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException> 예외가 throw됩니다. 테스트는 시간이 초과되거나, 예기치 않은 예외가 throw되거나, **Failed** 결과를 생성하는 Assert 문을 포함하는 경우 실패합니다.

테스트 후 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>결과 불충분**결과가 생성될 때마다**이 throw됩니다. 일반적으로는 아직 작업 중엔 테스트에 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Inconclusive%2A?displayProperty=nameWithType> 문을 추가하여 해당 테스트가 아직 실행할 준비가 되지 않았음을 나타냅니다.

> [!NOTE]
> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute> 특성을 사용하여 테스트 실행 준비가 되지 않았음을 표시하는 전략을 사용할 수도 있습니다. 그러나 이 전략을 사용하는 경우 구현되지 않은 테스트 수에 대한 보고서를 쉽게 생성할 수 없다는 단점이 있습니다.

새 Assert 예외 클래스를 작성하는 경우 해당 클래스가 기본 클래스 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>에서 속성을 상속하도록 하면 예외를 어설션 실패로 보다 쉽게 식별할 수 있으며, 테스트 또는 프로덕션 코드에서 예기치 않은 예외가 throw되지 않습니다.

애플리케이션 코드의 메서드가 throw할 것으로 예상했던 예외가 실제로 해당 메서드에서 throw되었는지 확인하려면 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 메서드를 사용하세요.

## <a name="see-also"></a>참고 항목

- [코드 단위 테스트](../test/unit-test-your-code.md)

---
title: Assert 클래스 사용 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6a4f7f1631ac4bfc651f5df347db010cf47a656
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657131"
---
# <a name="using-the-assert-classes"></a>Assert 클래스 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UnitTestingFramework 네임스페이스의 Assert 클래스를 사용하여 특정 기능을 확인합니다. 단위 테스트 메서드는 개발 코드에서 메서드 코드를 실행하지만, Assert 문을 포함하는 경우에만 코드의 동작이 정확한지 여부를 보고합니다.

## <a name="kinds-of-asserts"></a>Assert의 종류
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 네임스페이스는 다음과 같은 여러 종류의 Assert 클래스를 제공합니다.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

 테스트 메서드에서는 Assert.AreEqual()과 같은 Assert 클래스의 메서드를 원하는 수만큼 사용할 수 있습니다. Assert 클래스에서는 여러 메서드를 선택할 수 있으며, 이러한 메서드는 대부분 여러 오버로드를 포함합니다.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

 CollectionAssert 클래스를 사용하여 개체 컬렉션을 비교하고 컬렉션 하나 이상의 상태를 확인합니다.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

 StringAssert 클래스를 사용하여 문자열을 비교합니다. 이 클래스에는 StringAssert.Contains, StringAssert.Matches, StringAssert.StartsWith 등의 여러 가지 유용한 메서드가 포함되어 있습니다.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

 테스트가 실패할 때마다 AssertFailedException 예외가 throw됩니다. 테스트는 시간이 초과되거나, 예기치 않은 예외가 throw되거나, Failed 결과를 생성하는 Assert 문을 포함하는 경우 실패합니다.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

 테스트 결과 Inconclusive 결과가 생성될 때마다 AssertInconclusiveException 예외가 throw됩니다. 일반적으로는 아직 작업 중엔 테스트에 Assert.Inconclusive 문을 추가하여 해당 테스트가 아직 실행할 준비가 되지 않았음을 나타냅니다.

> [!NOTE]
> Ignore 특성을 사용하여 테스트 실행 준비가 되지 않았음을 표시하는 전략을 사용할 수도 있습니다. 그러나 이 전략을 사용하는 경우 구현 과정이 남아 있는 테스트 수에 대한 보고서를 쉽게 생성할 수 없다는 단점이 있습니다.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 새 Assert 예외 클래스를 작성하는 경우 해당 클래스가 기본 클래스 UnitTestAssertException에서 속성을 상속하도록 하면 예외를 어설션 실패로 보다 쉽게 식별할 수 있으며, 테스트 또는 프로덕션 코드에서 예기치 않은 예외가 throw되지 않습니다.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 개발 코드의 메서드가 throw할 것으로 예상했던 예외가 실제로 해당 메서드에서 throw됨을 테스트 메서드가 확인하도록 하려는 경우 ExpectedExceptionAttribute 특성으로 테스트 메서드를 데코레이팅합니다.

## <a name="see-also"></a>관련 항목
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> [기존 코드에 대한 단위 테스트 만들기 및 실행](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)

---
title: 'CA1812: 인스턴스화되지 않은 내부 클래스를 사용 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 401fbfbccfeeeeec5cbdc0e791b110d1b5f0201b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543977"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|범주|Microsoft 성능|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 어셈블리 수준 형식의 인스턴스가 어셈블리에서 코드에 의해 만들어지지 않습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 형식의 생성자 중 하나에 대 한 호출을 찾으려고 시도 하 고, 호출을 찾을 수 없는 경우 위반을 보고 합니다.

 이 규칙은 다음 형식을 검사 하지 않습니다.

- 값 형식

- 추상 형식

- 열거형

- 대리자

- 컴파일러에서 내보낸 배열 형식

- 인스턴스화할 수 없고 `static` (Visual Basic) 메서드만 정의 하는 형식입니다 `Shared` .

  <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName>분석 중인 어셈블리에 적용 하는 경우 `internal` 다른 어셈블리에서 필드를 사용 하 고 있는지 여부를 확인할 수 없기 때문에로 표시 된 생성자에서이 규칙이 발생 하지 않습니다 `friend` .

  코드 분석에서 이러한 제한을 해결할 수 없는 경우에도 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] `friend` 분석에 모든 어셈블리가 있는 경우 내부 생성자에서 외부 독립 실행형 FxCop가 발생 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 형식을 제거 하거나 해당 형식을 사용 하는 코드를 추가 합니다. 형식에 정적 메서드만 포함 된 경우 다음 중 하나를 형식에 추가 하 여 컴파일러가 기본 공용 인스턴스 생성자를 내보내지 않도록 합니다.

- 버전 1.0 및 1.1를 대상으로 하는 형식의 전용 생성자 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 입니다.

- `static` `Shared` 을 대상으로 하는 형식에 대 한 (Visual Basic) 한정자 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] 입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시 하지 않는 것이 안전 합니다. 다음과 같은 상황에서는이 경고를 표시 하지 않는 것이 좋습니다.

- 클래스는와 같은 런타임에 바인딩된 리플렉션 메서드를 통해 만들어집니다 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> .

- 클래스는 런타임 또는 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]에 의해 자동으로 만들어집니다. 이러한 예로 <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> 또는 <xref:System.Web.IHttpHandler?displayProperty=fullName>를 구현하는 클래스를 들 수 있습니다.

- 클래스는 새 제약 조건이 있는 제네릭 형식 매개 변수로 전달 됩니다. 예를 들어 다음 예제에서는이 규칙을 발생 시킵니다.

  ```csharp
  internal class MyClass
  {
      public DoSomething()
      {
      }
  }
  public class MyGeneric<T> where T : new()
  {
      public T Create()
      {
          return new T();
      }
  }
  // [...]
  MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
  mc.Create();
  ```

  이러한 상황에서는이 경고를 표시 하지 않는 것이 좋습니다.

## <a name="related-rules"></a>관련 규칙
 [CA1811: 호출되지 않는 전용 코드를 사용하지 마세요.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: 사용되지 않은 매개 변수를 검토하세요.](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: 사용되지 않는 로컬 항목을 제거하세요.](../code-quality/ca1804-remove-unused-locals.md)

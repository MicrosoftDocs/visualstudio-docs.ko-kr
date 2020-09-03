---
title: 'CA1024: 필요한 경우 속성을 사용 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a240a6eea86075bbf7f721f8620b6d135d594c20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546668"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: 적합한 속성을 사용하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 메서드의 이름이로 시작 하 `Get` 고, 매개 변수를 사용 하지 않으며, 배열이 아닌 값을 반환 합니다.

## <a name="rule-description"></a>규칙 설명
 대부분의 경우 속성은 데이터를 나타내고 메서드는 작업을 수행 합니다. 속성은 필드와 같은 액세스를 사용 하 여 더 쉽게 사용할 수 있습니다. 이러한 조건 중 하나가 있는 경우 메서드는 속성이 될 수 있는 좋은 후보입니다.

- 인수를 사용 하지 않고 개체의 상태 정보를 반환 합니다.

- 단일 인수를 수락 하 여 개체 상태의 일부를 설정 합니다.

  속성은 필드인 것 처럼 동작 해야 합니다. 메서드를 사용할 수 없는 경우에는 속성으로 변경 하면 안 됩니다. 메서드는 다음과 같은 경우에 속성 보다 우수 합니다.

- 메서드는 시간이 많이 걸리는 작업을 수행 합니다. 메서드는 필드 값을 설정 하거나 가져오는 데 필요한 시간 보다 더 perceivably.

- 메서드는 변환을 수행 합니다. 필드에 액세스 하면 저장 된 데이터의 변환 된 버전이 반환 되지 않습니다.

- Get 메서드는 관찰 가능 파생 효과를 가집니다. 필드의 값을 검색 해도 부작용이 발생 하지 않습니다.

- 실행 순서는 중요 합니다. 필드의 값을 설정 해도 다른 작업의 발생에 의존 하지 않습니다.

- 메서드를 연속 해 서 두 번 호출 하면 다른 결과가 생성 됩니다.

- 메서드는 정적 이지만 호출자가 변경할 수 있는 개체를 반환 합니다. 필드의 값을 검색 하는 경우 호출자가 필드에 의해 저장 된 데이터를 변경할 수 없습니다.

- 메서드는 배열을 반환 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드를 속성으로 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 메서드가 이전에 나열 된 조건 중 하나 이상을 충족 하는 경우이 규칙에서 경고를 표시 하지 않습니다.

## <a name="controlling-property-expansion-in-the-debugger"></a>디버거에서 속성 확장 제어
 프로그래머는 속성을 사용 하지 않는 한 가지 이유는 디버거가 자동으로 확장 하는 것을 원하지 않기 때문입니다. 예를 들어 속성에는 많은 개체를 할당 하거나 P/Invoke를 호출 하는 작업이 포함 될 수 있지만 실제로는 관찰 가능한 부작용이 없을 수 있습니다.

 를 적용 하 여 디버거의 속성 자동 확장을 방지할 수 있습니다 <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName> . 다음 예에서는이 특성을 instance 속성에 적용 하는 방법을 보여 줍니다.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>예제
 다음 예제에는 속성으로 변환 해야 하는 여러 메서드가 포함 되어 있으며, 필드 처럼 동작 하지 않을 수도 있습니다.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]

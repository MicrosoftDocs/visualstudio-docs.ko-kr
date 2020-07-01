---
title: DebuggerTypeProxy를 사용하여 사용자 지정 형식 표시 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerTypeProxyAttribute class
- DebuggerTypeProxy attribute
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b98481cb1727ecad9289f63136291d500c0d577e
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85347965"
---
# <a name="tell-the-debugger-what-type-to-show-using-debuggertypeproxy-attribute-c-visual-basic-ccli"></a>DebuggerTypeProxy 특성을 사용하여 디버거에 표시할 내용 지시(C#, Visual Basic, C++/CLI)

<xref:System.Diagnostics.DebuggerTypeProxyAttribute>는 형식에 대한 프록시 또는 대리 항목을 지정하고 형식이 디버거 창에 표시되는 방식을 변경합니다. 프록시가 있는 변수를 볼 때 원래 형식 대신 프록시가 **표시**에 나타납니다. 디버거 변수 창에는 프록시 형식의 공용 멤버만 표시됩니다. 프라이빗 멤버는 표시되지 않습니다.

이 특성은 다음 항목에 적용될 수 있습니다.

- 구조체
- 클래스
- 어셈블리

> [!NOTE]
> 네이티브 코드의 경우 이 특성은 C++/CLI 코드에서만 지원됩니다.

형식 프록시 클래스에는 프록시가 대체할 형식의 인수를 사용하는 생성자가 있어야 합니다. 디버거는 대상 유형의 변수를 표시해야 할 때마다 형식 프록시 클래스의 새 인스턴스를 만듭니다. 이 동작은 성능에 영향을 미칠 수 있습니다. 따라서 생성자에서 꼭 필요한 것보다 많은 작업을 수행하지 않아야 합니다.

성능 저하를 최소화하기 위해 식 계산기에서는 사용자가 디버거 창에서 + 기호를 클릭하거나 <xref:System.Diagnostics.DebuggerBrowsableAttribute>를 사용하여 형식을 확장한 경우가 아니면 형식의 표시 프록시에 대한 특성을 검사하지 않습니다. 따라서 표시 형식 자체에 특성을 배치하면 안 됩니다. 특성은 표시 형식의 본문에서만 사용할 수 있습니다.

형식 프록시는 특성의 대상인 클래스 내에 중첩된 private 클래스인 것이 좋습니다. 이렇게 하면 형식 프록시에서 내부 멤버에 쉽게 액세스할 수 있습니다.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute>는 상속될 수 있으므로, 해당 파생 클래스에서 자체 형식 프록시를 지정하지 않는 경우 기본 클래스에 지정된 형식 프록시가 모든 파생 클래스에 적용됩니다.

<xref:System.Diagnostics.DebuggerTypeProxyAttribute>가 어셈블리 수준에서 사용되는 경우 `Target` 매개 변수는 프록시가 대체할 형식을 지정합니다.

이 특성을 <xref:System.Diagnostics.DebuggerDisplayAttribute> 및 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>와 함께 사용하는 방법에 관한 예제는 [DebuggerDisplay 특성 사용](../debugger/using-the-debuggerdisplay-attribute.md)을 참조하세요.

## <a name="using-generics-with-debuggertypeproxy"></a>DebuggerTypeProxy와 함께 제네릭 사용

제네릭에 대한 지원은 제한되어 있습니다. C#의 경우 `DebuggerTypeProxy`는 개방형 형식만 지원합니다. 생성되지 않은 형식이라고도 하는 개방형 형식은 해당 형식 매개 변수의 인수를 사용하여 인스턴스화되지 않은 제네릭 형식입니다. 생성된 형식이라고도 하는 닫힌 형식은 지원되지 않습니다.

개방형 형식에 대한 구문은 다음과 같습니다.

`Namespace.TypeName<,>`

`DebuggerTypeProxy`에서 제네릭 형식을 대상으로 사용하는 경우 이 구문을 사용해야 합니다. `DebuggerTypeProxy` 메커니즘은 형식 매개 변수를 자동으로 유추합니다.

C#의 개방형 형식과 폐쇄형 형식에 관한 자세한 내용은 [C# 언어 사양](/dotnet/csharp/language-reference/language-specification)의 섹션 20.5.2 개방형 형식 및 폐쇄형 형식을 참조하세요.

Visual Basic에는 개방형 형식 구문이 없으므로 Visual Basic의 경우 이와 같은 작업을 수행할 수 없습니다. 대신 개방형 형식 이름의 문자열 표현을 사용해야 합니다.

`"Namespace.TypeName'2"`

## <a name="see-also"></a>참조

- [DebuggerDisplay 특성 사용](../debugger/using-the-debuggerdisplay-attribute.md)
- [관리 개체의 사용자 지정 뷰 만들기](../debugger/create-custom-views-of-managed-objects.md)
- [디버거 표시 특성을 사용하여 디버깅 향상](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)

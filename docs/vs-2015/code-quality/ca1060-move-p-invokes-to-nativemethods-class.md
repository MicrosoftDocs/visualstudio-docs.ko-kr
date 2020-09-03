---
title: 'CA1060: P-Invoke를 NativeMethods 클래스로 이동 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e01ad9fc4fc57917c123404d8863d04240585793
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533434"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: P/Invoke를 NativeMethods 클래스로 이동
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|범주|Microsoft 디자인|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 메서드는 플랫폼 호출 서비스를 사용 하 여 비관리 코드에 액세스 하 고 **NativeMethods** 클래스 중 하나의 멤버가 아닙니다.

## <a name="rule-description"></a>규칙 설명
 특성을 사용 하 여 표시 된 것과 같은 플랫폼 호출 메서드 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 또는의 키워드를 사용 하 여 정의 된 메서드는 `Declare` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 비관리 코드에 액세스 합니다. 이러한 메서드는 다음 클래스 중 하나에 있어야 합니다.

- **NativeMethods** -이 클래스는 비관리 코드 권한에 대 한 스택 워크를 표시 하지 않습니다. <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>이 클래스에는 적용 되지 않아야 합니다. 이 클래스는 스택 워크가 수행 되기 때문에 어디에서 나 사용할 수 있는 메서드에 대 한 것입니다.

- **SafeNativeMethods** -이 클래스는 비관리 코드 권한에 대 한 스택 워크를 표시 하지 않습니다. <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>이 클래스에 적용 됩니다. 이 클래스는 모든 사용자가 호출 하는 데 안전 하 게 사용할 수 있는 메서드입니다. 이러한 메서드의 호출자는 모든 호출자가 아무 것도 무해 하므로 사용이 안전한 지 확인 하기 위해 전체 보안 검토를 수행 하는 데 필요 하지 않습니다.

- **UnsafeNativeMethods** -이 클래스는 비관리 코드 권한에 대 한 스택 워크를 표시 하지 않습니다. <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>이 클래스에 적용 됩니다. 이 클래스는 잠재적으로 위험할 수 있는 메서드에 대 한 것입니다. 이러한 메서드의 모든 호출자는 스택 워크가 수행 되지 않기 때문에 사용이 안전한 지 확인 하기 위해 전체 보안 검토를 수행 해야 합니다.

  이러한 클래스는 `internal` (Visual Basic)로 선언 되 `Friend` 고 private 생성자를 선언 하 여 새 인스턴스가 생성 되지 않도록 합니다. 이러한 클래스의 메서드는 `static` 및 `internal` ( `Shared` 및 `Friend` Visual Basic) 여야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 메서드를 적절 한 **NativeMethods** 클래스로 이동 합니다. 대부분의 응용 프로그램에서 P/Invoke를 **NativeMethods** 라는 새 클래스로 이동 하는 것은 충분 합니다.

 그러나 다른 응용 프로그램에서 사용할 라이브러리를 개발 하는 경우 **SafeNativeMethods** 및 **UnsafeNativeMethods**라는 두 개의 다른 클래스를 정의 하는 것이 좋습니다. 이러한 클래스는 **NativeMethods** 클래스와 유사 합니다. 그러나 **SuppressUnmanagedCodeSecurityAttribute**라는 특수 특성을 사용 하 여 표시 됩니다. 이 특성이 적용 되 면 런타임은 모든 호출자에 게 **UnmanagedCode** 권한이 있는지 확인 하기 위해 전체 스택 워크를 수행 하지 않습니다. 런타임은 일반적으로 시작 시이 사용 권한을 확인 합니다. 검사가 수행 되지 않으므로 이러한 관리 되지 않는 메서드에 대 한 호출의 성능을 크게 향상 시킬 수 있으며, 이러한 메서드를 호출 하는 권한이 제한 된 코드를 사용할 수도 있습니다.

 그러나이 특성은 매우 주의 해 서 사용 해야 합니다. 잘못 구현 된 경우 심각한 보안에 영향을 미칠 수 있습니다.

 메서드를 구현 하는 방법에 대 한 자세한 내용은 **NativeMethods** 예제, **SafeNativeMethods** 예제 및 **UnsafeNativeMethods** 예를 참조 하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는이 규칙을 위반 하는 메서드를 선언 합니다. 위반 문제를 해결 하기 위해 P/Invoke만 포함 하도록 디자인 된 적절 한 클래스로 **Removedirectory** p/Invoke를 이동 해야 합니다.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>NativeMethods 예제

### <a name="description"></a>Description
 **NativeMethods** 클래스는 **SuppressUnmanagedCodeSecurityAttribute**를 사용 하 여 표시 해서는 안 됩니다 .이 클래스에 배치 되는 P/invoke에는 **UnmanagedCode** 권한이 있어야 합니다. 대부분의 응용 프로그램은 로컬 컴퓨터에서 실행 되 고 완전 신뢰와 함께 실행 되기 때문에 일반적으로 문제가 되지 않습니다. 그러나 재사용 가능한 라이브러리를 개발 하는 경우 **SafeNativeMethods** 또는 **UnsafeNativeMethods** 클래스를 정의 하는 것이 좋습니다.

 다음 예제에서는 user32.dll에서 **messagebeep** 함수를 래핑하는 **상호 작용** 메서드를 보여 줍니다. **Messagebeep** P/Invoke는 **NativeMethods** 클래스에 배치 됩니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>SafeNativeMethods 예제

### <a name="description"></a>Description
 모든 응용 프로그램에 안전 하 게 노출 될 수 있고 부작용이 없는 P/Invoke 메서드는 **SafeNativeMethods**라는 클래스에 배치 해야 합니다. 권한을 요구할 필요는 없으며, 사용자가 호출 되는 위치에 대해 많은 주의가 필요 하지 않습니다.

 다음 예제에서는 kernel32.dll에서 **GetTickCount** 함수를 래핑하는 **TickCount** 속성을 보여 줍니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods 예제

### <a name="description"></a>Description
 안전 하 게 호출할 수 없고 부작용이 발생 하는 P/Invoke 메서드는 **UnsafeNativeMethods**라는 클래스에 배치 해야 합니다. 이러한 메서드는 사용자에 게 실수로 노출 되지 않도록 엄격 하 게 확인 해야 합니다. Rule [CA2118: Review SuppressUnmanagedCodeSecurityAttribute usage](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) 를 사용 하면 도움이 될 수 있습니다. 또는 메서드를 사용할 때 **UnmanagedCode** 대신 요청 된 다른 사용 권한이 있어야 합니다.

 다음 예제에서는 user32.dll **ShowCursor** 함수를 래핑하는 Cursor 메서드를 보여 줍니다 **.**

### <a name="code"></a>코드
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>참고 항목
 [디자인 경고](../code-quality/design-warnings.md)

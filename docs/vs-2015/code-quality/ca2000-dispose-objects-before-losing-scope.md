---
title: 'CA2000: 범위를 벗어나기 전에 개체를 삭제 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e3de3246980ead0b20d471321a9696451aed81ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534773"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: 범위를 벗어나기 전에 개체를 삭제하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|범주|Microsoft.Reliability|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 형식의 로컬 개체가 만들어지지만 개체 <xref:System.IDisposable> 에 대 한 모든 참조가 범위를 벗어난 후에는 개체가 삭제 되지 않습니다.

## <a name="rule-description"></a>규칙 설명
 개체에 대 한 모든 참조가 범위를 벗어나는 삭제 가능한 개체를 명시적으로 삭제 하지 않으면 가비지 수집기가 개체의 종료자를 실행할 때 개체는 결정 되지 않은 시간에 삭제 됩니다. 개체의 종료 자가 실행 되지 않도록 하는 예외 이벤트가 발생할 수 있으므로 개체를 명시적으로 삭제 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 개체에 <xref:System.IDisposable.Dispose%2A> 대 한 모든 참조가 범위를 벗어나는 개체에 대해를 호출 합니다.

 문을 사용 하 여를 `using` `Using` 구현 하 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 는 개체를 래핑할 수 있습니다 `IDisposable` . 이러한 방식으로 래핑된 개체는 블록 가까이에서 자동으로 삭제 됩니다 `using` .

 다음은 using 문을 사용 하 여 IDisposable 개체를 보호 하는 데 충분 하지 않고 CA2000 발생할 수 있는 몇 가지 경우입니다.

- 삭제 가능한 개체를 반환 하려면 개체가 using 블록 외부의 try/finally 블록에 생성 되어야 합니다.

- Using 문의 생성자에서 삭제 가능한 개체의 멤버를 초기화할 수 없습니다.

- 한 예외 처리기로만 보호 되는 생성자를 중첩 합니다. 예를 들면 다음과 같습니다.

    ```
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     CA2000는 StreamReader 개체 생성에 오류가 발생 하 여 FileStream 개체가 닫히지 않는 원인이 되기 때문에 발생 합니다.

- 동적 개체는 섀도 개체를 사용 하 여 IDisposable 개체의 삭제 패턴을 구현 해야 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 `Dispose`와 같은 <xref:System.IO.Stream.Close%2A>를 호출하는 개체에 대해 메서드를 호출하지 않은 경우나 경고를 발생시킨 메서드가 사용자의 개체를 래핑하는 IDisposable 개체를 반환하는 경우 이 규칙에서 경고를 표시해야 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA2213: 삭제 가능한 필드는 삭제해야 합니다.](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

 [CA2202: 개체를 여러 번 삭제하지 마십시오.](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)

## <a name="example"></a>예
 삭제 가능한 개체를 반환 하는 메서드를 구현 하는 경우 catch 블록 없이 try/finally 블록을 사용 하 여 개체가 삭제 되었는지 확인 합니다. Try/finally 블록을 사용 하 여 오류 지점에서 예외가 발생할 수 있도록 하 고 개체가 삭제 되었는지 확인 합니다.

 OpenPort1 메서드에서 ISerializable 개체 SerialPort 또는 SomeMethod에 대 한 호출을 열기 위한 호출이 실패할 수 있습니다. 이 구현에서 CA2000 경고가 발생 합니다.

 OpenPort2 메서드에서는 두 개의 SerialPort 개체가 선언 되 고 null로 설정 됩니다.

- `tempPort`-메서드 작업이 성공 했는지 테스트 하는 데 사용 됩니다.

- `port`는 메서드의 반환 값에 사용 됩니다.

  는 `tempPort` 블록에서 생성 되 고 열리며 `try` 다른 모든 필수 작업은 동일한 블록에서 수행 됩니다 `try` . 블록의 끝에는 `try` 열린 포트가 `port` 반환 되 고 개체가로 설정 된 개체에 할당 됩니다 `tempPort` `null` .

  `finally`블록은의 값을 확인 합니다 `tempPort` . Null이 아닌 경우에는 메서드의 작업이 실패 하 고 `tempPort` 리소스가 해제 되도록 닫혔습니다. 반환 된 포트 개체에는 메서드의 작업이 성공한 경우 열린 SerialPort 개체가 포함 되 고, 작업이 실패 한 경우에는 null이 됩니다.

  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]

## <a name="example"></a>예
 기본적으로 컴파일러는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 오버플로를 확인 하는 모든 산술 연산자를 포함 합니다. 따라서 Visual Basic 산술 연산은을 throw 할 수 있습니다 <xref:System.OverflowException> . CA2000와 같은 규칙에서 예기치 않은 위반이 발생할 수 있습니다. 예를 들어, 다음 CreateReader1 함수는 Visual Basic 컴파일러가 StreamReader를 삭제 하지 않도록 하는 예외를 throw 할 수 있는 추가에 대 한 오버플로 검사 명령을 내보내기 때문에 CA2000 위반을 발생 시킵니다.

 이 문제를 해결 하려면 프로젝트의 Visual Basic 컴파일러에의 한 오버플로 검사 내보내기를 사용 하지 않도록 설정 하거나 다음 CreateReader2 함수와 같이 코드를 수정할 수 있습니다.

 오버플로 검사 내보내기를 사용 하지 않도록 설정 하려면 솔루션 탐색기에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다. **컴파일**을 클릭 하 고 **고급 컴파일 옵션**을 클릭 한 다음 **정수 오버플로 검사 제거**를 선택 합니다.

<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->

## <a name="see-also"></a>관련 항목
 <xref:System.IDisposable> [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
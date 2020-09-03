---
title: CA5122 P-Invoke 선언이 안전 하 게 중요 한 것은 아닙니다. Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a6a6ee7796ae437b564f6826376219291143e449
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545095"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122 P/Invoke 선언은 안전에 중요한 선언이 아니어야 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|CheckId|CA5122|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 P/Invoke 선언에 <xref:System.Security.SecuritySafeCriticalAttribute>가 표시되었습니다.

```csharp
[assembly: AllowPartiallyTrustedCallers]

// ...
public class C
{
    [SecuritySafeCritical]
    [DllImport("kernel32.dll")]
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke
   }
```

 이 예제에서 `C.Beep(...)`는 보안에 안전한 중요 메서드로 표시되었습니다.

## <a name="rule-description"></a>규칙 설명
 메서드는 보안에 중요한 작업을 수행할 때 SecuritySafeCritical로 표시되지만, 투명 코드에서도 안전하게 사용할 수 있습니다. 보안 투명성 모델의 기본 규칙 중 하나는 투명 코드가 P/Invoke를 통해 네이티브 코드를 절대 직접 호출할 수 없다는 점입니다. 따라서 P/Invoke를 SecuritySafeCritical로 표시할 경우 투명 코드가 P/Invoke를 호출할 수 없으며, 보안 분석에서 잘못 해석하는 원인이 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 투명 코드에서 P/Invoke를 사용할 수 있도록 만들려면 보안에 안전한 중요 래퍼 메서드를 노출하십시오.

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}
```

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

---
title: 'CA1063: IDisposable을 올바르게 구현 하십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04691d2344b232906676180122ad67fff5405891
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539362"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable을 올바르게 구현하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|범주|Microsoft 디자인|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 `IDisposable`가 올바르게 구현 되지 않은 경우 이 문제에 대 한 몇 가지 이유가 여기에 나와 있습니다.

- IDisposable은 클래스에서 다시 구현 됩니다.

- Finalize가 다시 재정의 됩니다.

- Dispose는 무시 됩니다.

- Dispose ()가 public, sealed 또는 명명 된 Dispose가 아닙니다.

- Dispose (bool)는 protected, virtual 또는 봉인 되지 않습니다.

- 봉인 되지 않은 형식의 경우 Dispose ()는 Dispose (true)를 호출 해야 합니다.

- 봉인 되지 않은 형식의 경우 Finalize 구현은 Dispose (bool) 또는 case 클래스 종료자를 모두 호출 하지 않습니다.

  이러한 패턴 중 하나를 위반 하면이 경고가 트리거됩니다.

  봉인 되지 않은 모든 루트 IDisposable 형식은 자체 보호 된 bool (가상 void) 메서드를 제공 해야 합니다. Dispose ()는 Dispose (true)를 호출 하 고 Finalize는 Dispose (false)를 호출 해야 합니다. 봉인 되지 않은 루트 IDisposable 형식을 만드는 경우 Dispose (bool)를 정의 하 고 호출 해야 합니다. 자세한 내용은 .NET Framework 설명서의 [프레임 워크 디자인 지침](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) 섹션에서 [관리 되지 않는 리소스 정리](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) 를 참조 하세요.

## <a name="rule-description"></a>규칙 설명
 모든 IDisposable 형식은 Dispose 패턴을 올바르게 구현해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 코드를 검사 하 고 다음 해결 방법을 확인 하 여이 위반을 해결 합니다.

- 에 의해 구현 된 인터페이스 목록에서 IDisposable을 제거 {0} 하 고 대신 기본 클래스 Dispose 구현을 재정의 합니다.

- 형식에서 종료자를 제거 {0} 하 고 Dispose (bool disposing)를 재정의 한 후 ' disposing '이 false 인 코드 경로에 종료 논리를 넣습니다.

- 제거 {0} 하 고 dispose (bool disposing)를 재정의 한 후 ' disposing '이 true 인 코드 경로에 삭제 논리를 넣습니다.

- {0}이 public으로 선언 되 고 sealed로 선언 되었는지 확인 합니다.

- {0}' Dispose '로 이름을 바꾸고 public 및 sealed로 선언 되어 있는지 확인 합니다.

- {0}이 protected, virtual 및 봉인 되지 않음으로 선언 되었는지 확인 합니다.

- {0}Dispose (true)를 호출 하 고 GC를 호출 하도록 수정 합니다. 현재 개체 인스턴스 (의 ' this ' 또는 ' Me ')에서 Gc.suppressfinalize [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 를 반환 합니다.

- {0}Dispose (false)를 호출한 다음을 반환 하도록 수정 합니다.

- 봉인 되지 않은 루트 IDisposable 클래스를 작성 하는 경우 IDisposable의 구현이이 섹션의 앞부분에서 설명한 패턴을 따르는지 확인 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="pseudo-code-example"></a>의사 코드 예제
 다음 의사 코드는 관리 되는 리소스와 네이티브 리소스를 사용 하는 클래스에서 Dispose (bool)를 구현 하는 방법에 대 한 일반적인 예를 제공 합니다.

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

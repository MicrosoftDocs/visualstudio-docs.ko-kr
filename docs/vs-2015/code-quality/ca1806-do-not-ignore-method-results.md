---
title: 'CA1806: 메서드 결과를 무시 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 726cde42eb08ee5508481887fae2e9d2b059256c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543873"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: 메서드 결과를 무시하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotIgnoreMethodResults|
|CheckId|CA1806|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 이 경고는 다음과 같은 몇 가지 이유로 발생할 수 있습니다.

- 새 개체가 만들어졌지만 사용 되지 않습니다.

- 새 문자열을 만들어 반환 하는 메서드가 호출 되 고 새 문자열은 사용 되지 않습니다.

- 사용 되지 않는 HRESULT 또는 오류 코드를 반환 하는 COM 또는 P/Invoke 메서드입니다. 규칙 설명

  불필요 한 개체를 만들고 사용 하지 않는 개체의 연결 된 가비지 수집을 사용 하면 성능이 저하 됩니다.

  문자열은 변경할 수 없으며 ToUpper와 같은 메서드는 호출 하는 메서드에서 문자열의 인스턴스를 수정 하는 대신 문자열의 새 인스턴스를 반환 합니다.

  HRESULT 또는 오류 코드를 무시 하면 오류 조건 또는 리소스 부족 상태에서 예기치 않은 동작이 발생할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 메서드 A가 사용 되지 않는 B 개체의 새 인스턴스를 만드는 경우 인스턴스를 다른 메서드에 인수로 전달 하거나 인스턴스를 변수에 할당 합니다. 개체를 만들 필요가 없으면 제거 하십시오.-또는-

 메서드 A가 메서드 B를 호출 하지만 메서드 B가 반환 하는 새 문자열 인스턴스를 사용 하지 않는 경우 인스턴스를 다른 메서드에 인수로 전달 하 고, 인스턴스를 변수에 할당 합니다. 필요 하지 않은 경우 호출을 제거 합니다.

 또는

 메서드 A가 메서드 B를 호출 하지만 메서드가 반환 하는 HRESULT 또는 오류 코드를 사용 하지 않는 경우 조건문에서 결과를 사용 하 고 결과를 변수에 할당 하거나 다른 메서드에 인수로 전달 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 개체를 만드는 작업을 수행 하는 경우를 제외 하 고는이 규칙에서 경고를 표시 하지 마십시오.

## <a name="example"></a>예제
 다음 예제에서는 호출 된 String.format의 결과를 무시 하는 클래스를 보여 줍니다.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->

## <a name="example"></a>예제
 다음 예에서는 문자열의 결과를 할당 하 여 이전 위반을 수정 합니다 .를 호출한 변수로 다시 트리밍합니다.

<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->

## <a name="example"></a>예제
 다음 예제에서는 만든 개체를 사용 하지 않는 메서드를 보여 줍니다.

> [!NOTE]
> Visual Basic에서이 위반을 재현할 수 없습니다.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]

## <a name="example"></a>예제
 다음 예제에서는 불필요 한 개체 생성을 제거 하 여 이전 위반을 수정 합니다.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]

## <a name="example"></a>예제
 다음 예제에서는 네이티브 메서드에서 GetShortPathName 반환 하는 오류 코드를 무시 하는 메서드를 보여 줍니다.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 오류 코드를 확인 하 고 호출이 실패할 때 예외를 throw 하 여 이전 위반을 수정 합니다.

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]
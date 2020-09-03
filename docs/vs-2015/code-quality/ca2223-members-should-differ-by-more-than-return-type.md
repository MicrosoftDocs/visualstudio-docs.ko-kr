---
title: 'CA2223: 멤버는 반환 형식 보다 많이 달라 야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4c1071617572af44a73f98953fd435623190e0e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540844"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223: 멤버는 반환 형식 이외의 것도 달라야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|범주|Microsoft 사용|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 두 public 또는 protected 멤버에는 반환 형식을 제외 하 고 동일한 시그니처가 있습니다.

## <a name="rule-description"></a>규칙 설명
 공용 언어 런타임에서는 반환 형식을 사용 하 여 동일한 멤버를 구분할 수 있지만,이 기능은 공용 언어 사양에 있지 않으며 .NET 프로그래밍 언어의 일반적인 기능입니다. 멤버가 반환 형식만 다른 경우 개발자 및 개발 도구는 이러한 멤버를 제대로 구분 하지 못할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 멤버의 디자인을 변경 하 여 해당 이름 및 매개 변수 형식만을 기준으로 고유 하거나 멤버를 노출 하지 않도록 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예
 다음 예제에서는 MSIL (Microsoft 중간 언어)에서이 규칙을 위반 하는 형식을 보여 줍니다. C # 또는 Visual Basic .NET을 사용 하 여이 규칙을 위반할 수 없습니다.

```

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit ReturnTypeTest
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance int32
            AMethod(int32 x) cil managed
    {
      // Code size       6 (0x6)
      .maxstack  1
      .locals init (int32 V_0)
      IL_0000:  ldc.i4.0
      IL_0001:  stloc.0
      IL_0002:  br.s       IL_0004

      IL_0004:  ldloc.0
      IL_0005:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig instance string
            AMethod(int32 x) cil managed
    {
      // Code size       10 (0xa)
      .maxstack  1
      .locals init (string V_0)
      IL_0000:  ldstr      "test"
      IL_0005:  stloc.0
      IL_0006:  br.s       IL_0008

      IL_0008:  ldloc.0
      IL_0009:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method ReturnTypeTest::.ctor

  } // end of class ReturnTypeTest

} // end of namespace UsageLibrary
```

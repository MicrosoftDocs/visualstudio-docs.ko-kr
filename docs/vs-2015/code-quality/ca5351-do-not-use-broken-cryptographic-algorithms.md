---
title: CA5351 손상 된 암호화 알고리즘을 사용 하지 않음 | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ad4698fe469176ae8ed590c44b4efbb4ccf39de2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545056"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 끊어진 암호화 알고리즘 사용 안 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|CheckId|CA5351|
|범주|Microsoft.Cryptography|
|변경 수준|주요 변경 아님|

> [!NOTE]
> 이 경고는 2015년 11월에 마지막으로 업데이트되었습니다.

## <a name="cause"></a>원인
 <xref:System.Security.Cryptography.MD5> 등의 해시 함수와 <xref:System.Security.Cryptography.DES> 및 <xref:System.Security.Cryptography.RC2> 등의 암호화 알고리즘은 상당한 위험을 노출시킬 수 있으며 무차별 암호 대입 공격 및 해시 충돌과 같은 간단한 공격 기법을 통해 중요한 정보가 노출될 수 있습니다.

 아래 암호화 알고리즘 목록은 알려진 암호화 공격을 받습니다. 암호화 해시 알고리즘 <xref:System.Security.Cryptography.MD5> 는 해시 충돌 공격을 받습니다.  사용법에 따라 해시 충돌로 인해 해시 함수의 고유한 암호화 출력을 사용하는 시스템이 가장, 변조 또는 다른 종류의 공격을 받을 수 있습니다. 암호화 알고리즘 <xref:System.Security.Cryptography.DES> 및 <xref:System.Security.Cryptography.RC2> 에는 의도하지 않게 암호화된 데이터가 노출될 수 있는 암호화 공격을 받습니다.

## <a name="rule-description"></a>규칙 설명
 끊어진 암호화 알고리즘은 안전하지 않은 것으로 간주되므로 사용해서는 안 됩니다. 사용 컨텍스트에 따라 구체적인 취약성이 달라지지만 MD5 해시 알고리즘은 알려진 충돌 공격에 취약합니다.  데이터 무결성(예: 파일 서명 또는 디지털 인증서)을 보장하는 데 사용되는 해시 알고리즘이 특히 취약합니다.  이 컨텍스트에서 공격자는 해시 값을 변경하거나 연결된 디지털 서명을 무효화하지 않고 정상적인 데이터가 악성 데이터로 대체될 수 있도록 두 가지 데이터를 생성할 수 있습니다.

 암호화 알고리즘의 경우:

- <xref:System.Security.Cryptography.DES> 암호화는 하루 미만의 무차별 암호 대입 공격일 수 있는 작은 키 크기를 포함합니다.

- <xref:System.Security.Cryptography.RC2> 암호화는 공격자가 모든 키 값 간의 수학적 관계를 찾는 관련 키 공격에 취약합니다.

  이 규칙은 소스 코드에서 위의 암호화 기능을 발견할 때 트리거되며 사용자에게 경고를 throw합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 보다 강력한 암호화 옵션을 사용합니다.

- MD5의 경우 [SHA-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) 제품군의 해시를 사용 합니다 (예:,, <xref:System.Security.Cryptography.SHA512> <xref:System.Security.Cryptography.SHA384> <xref:System.Security.Cryptography.SHA256> ).

- DES 및 RC2의 경우 <xref:System.Security.Cryptography.Aes> 암호화를 사용합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 암호화 전문가가 검토하지 않은 경우 이 규칙의 경고가 표시되지 않도록 하지 마세요.

## <a name="pseudo-code-example"></a>의사 코드 예제
 다음 의사 코드 샘플에서는 이 규칙 및 가능한 대안에 의해 검색되는 패턴을 보여 줍니다.

### <a name="md5-hashing-violation"></a>MD5 해시 위반

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>솔루션

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>RC2 암호화 위반

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

```

### <a name="solution"></a>솔루션

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```

### <a name="des-br-br-encryption-violation"></a>DES <br /><br />암호화 위반

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

```

### <a name="solution"></a>솔루션

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```
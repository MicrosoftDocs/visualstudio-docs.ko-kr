---
title: '&lt;Signature &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <Signature> element [ClickOnce deployment manifest]
ms.assetid: c99b07ad-e8ba-43f2-b0d6-3745e7a7c8b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6f07e2649d6f41e77f453f64c5838c746f22ad0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85835422"
---
# <a name="ltsignaturegt-element-clickonce-deployment"></a>&lt;Signature &gt; 요소 (ClickOnce 배포)
이 배포 매니페스트에 디지털 방식으로 서명하는 데 필요한 정보를 포함합니다.

## <a name="syntax"></a>구문

```xml

<Signature> 
   XML signature information 
</Signature>
```

## <a name="remarks"></a>설명
 봉투 (envelope) 서명을 사용 하 여 배포 매니페스트에 서명 하는 것은 선택 사항 이지만 권장 됩니다. XML 파일에 서명 하는 방법에 대 한 자세한 내용은에 설명 된 World Wide Web 컨소시엄 권장 사항 "XML 서명 구문 및 처리"를 참조 하십시오 [http://www.w3.org/TR/xmldsig-core/](https://www.w3.org/TR/xmldsig-core/) .

 매니페스트에 서명 하려면 모든 파일에 대해 해시를 제공 해야 합니다. 사용자는 해시 되지 않은 파일의 콘텐츠를 확인할 수 없으므로 해시 되지 않은 파일이 있는 매니페스트는 서명할 수 없습니다.

## <a name="example"></a>예
 다음 코드 예제에서는 `Signature` 배포에 사용 되는 배포 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
<Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
  <SignedInfo>
    <CanonicalizationMethod Algorithm=
           "http://www.w3.org/TR/2001/REC-xml-c14n-20010315" />
    <SignatureMethod Algorithm=
           "http://www.w3.org/2000/09/xmldsig#rsa-sha1" />
    <Reference URI="">
      <Transforms>
        <Transform Algorithm=
           "http://www.w3.org/2000/09/xmldsig#enveloped-signature" />
      </Transforms>
      <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <DigestValue>d2z5AE...</DigestValue>
    </Reference>
  </SignedInfo>
  <SignatureValue>
4PHj6SaopoLp...
  </SignatureValue>
  <KeyInfo>
    <X509Data>
      <X509Certificate>
MIIHnTCCBoWgAwIBAgIKJY9+nwAHAAB...
      </X509Certificate>
    </X509Data>
  </KeyInfo>
</Signature>
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)

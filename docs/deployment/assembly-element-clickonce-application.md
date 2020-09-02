---
title: '&lt;assembly &gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b629243920021adc3833f43f268f05638029dc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900762"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;assembly &gt; 요소 (ClickOnce 응용 프로그램)
응용 프로그램 매니페스트에 대 한 최상위 수준 요소입니다.

## <a name="syntax"></a>Syntax

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `assembly`요소는 루트 요소 이며 필수입니다. 처음 포함 된 요소는 요소 여야 합니다 `assemblyIdentity` . 매니페스트 요소는 다음 네임 스페이스 중 하나에 있어야 합니다.

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 어셈블리의 자식 요소도 상속 하거나 태그를 지정 하 여 이러한 네임 스페이스에 있어야 합니다.

 `assembly` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`manifestVersion`|필수 요소. `manifestVersion`특성은로 설정 해야 합니다 `1.0` .|

## <a name="example"></a>예
 다음 코드 예제에서는 응용 프로그램 `assembly` 에 대 한 응용 프로그램 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이 코드 예제는 [ClickOnce 응용 프로그램 매니페스트에](../deployment/clickonce-application-manifest.md)제공 된 더 큰 예제의 일부입니다.

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
- [\<assembly> 요소인](../deployment/assembly-element-clickonce-deployment.md)

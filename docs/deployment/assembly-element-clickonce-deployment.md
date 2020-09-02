---
title: '&lt;assembly &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b639a7f95cfb59844fa37963730e22ead450482
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62929071"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;assembly &gt; 요소 (ClickOnce 배포)
배포 매니페스트에 대 한 최상위 수준 요소입니다.

## <a name="syntax"></a>Syntax

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `assembly`요소는 루트 요소 이며 필수입니다. 처음 포함 된 요소는 요소 여야 합니다 `assemblyIdentity` . 매니페스트 요소는 `urn:schemas-microsoft-com:asm.v1` , 및 네임 스페이스에 있어야 합니다. `urn:schemas-microsoft-com:asm.v2` `http://www.w3.org/2000/09/xmldsig#` 어셈블리의 자식 요소도 상속 하거나 태그를 지정 하 여 이러한 네임 스페이스에 있어야 합니다.

 `assembly` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`manifestVersion`|필수 요소. 이 특성은로 설정 해야 합니다 `1.0` .|

## <a name="example"></a>예
 다음 코드 예제에서는를 `assembly` 사용 하 여 배포 된 응용 프로그램에 대 한 배포 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이 코드 예제는 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md) 항목에 대해 제공 되는 더 큰 예제의 일부입니다.

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> 요소인](../deployment/assembly-element-clickonce-application.md)
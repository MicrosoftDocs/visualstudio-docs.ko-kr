---
title: '&lt;fileAssociation &gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
description: FileAssociation 요소는 응용 프로그램과 연결할 파일 확장명을 식별 합니다. FileAssociation 요소는 선택 사항입니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1908b4f63edcf90643c28523c0c6ed0d0e11a97
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382730"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation &gt; 요소 (ClickOnce 응용 프로그램)
응용 프로그램과 연결할 파일 확장명을 식별 합니다.

## <a name="syntax"></a>구문

```xml
<fileAssociation
    xmlns="urn:schemas-microsoft-com:clickonce.v1"
    extension
    description
    progid
    defaultIcon
/>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `fileAssociation` 요소는 선택적입니다. 요소에는 다음 특성이 있습니다.

|특성|Description|
|---------------|-----------------|
|`extension`|필수 사항입니다. 응용 프로그램과 연결할 파일 확장명입니다.|
|`description`|필수 사항입니다. 셸에서 사용할 파일 형식에 대 한 설명입니다.|
|`progid`|필수 사항입니다. 파일 형식을 고유 하 게 식별 하는 이름입니다.|
|`defaultIcon`|필수 사항입니다. 이 확장명을 가진 파일에 사용할 아이콘을 지정 합니다. 이 요소를 포함 하는 [ \<assembly> 요소](../deployment/assembly-element-clickonce-application.md) 내에서 [ \<file> 요소](../deployment/file-element-clickonce-application.md) 를 사용 하 여 아이콘 파일을 지정 해야 합니다.|

## <a name="remarks"></a>설명
 이 요소는 "urn: 스키마-microsoft-com: clickonce"에 대 한 XML 네임 스페이스 참조를 포함 해야 합니다. 요소를 사용 하는 경우 해당 요소는 `<fileAssociation>` `<application>` 부모 [ \<assembly> 요소의](../deployment/assembly-element-clickonce-application.md)요소 뒤에와 야 합니다.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 는 기존 파일 연결을 덮어쓰지 않습니다. 그러나 ClickOnce 응용 프로그램은 현재 사용자에 대해서만 파일 확장명을 재정의할 수 있습니다. ClickOnce 응용 프로그램이 제거 되 고 나면 ClickOnce에서 사용자에 대 한 파일 연결을 삭제 하 고 컴퓨터별 연결이 다시 활성화 됩니다.

## <a name="example"></a>예
 다음 코드 예제에서는를 `fileAssociation` 사용 하 여 배포 된 텍스트 편집기 응용 프로그램에 대 한 응용 프로그램 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이 코드 예제에는 특성에 필요한 [ \<file> 요소도](../deployment/file-element-clickonce-application.md) 포함 되어 있습니다 `defaultIcon` .

```xml
<file name="text.ico" size="4286">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>
  </hash>
</file>
<file name="writing.ico" size="9662">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>
  </hash>
</file>
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />
```

## <a name="see-also"></a>참조
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
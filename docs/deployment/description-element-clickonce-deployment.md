---
title: '&lt;description &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c359b188894c40f017e3d2a0e06d52de87e9c5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928794"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;description &gt; 요소 (ClickOnce 배포)
제어판에서 셸 존재 및 **프로그램 추가/제거** 항목을 만드는 데 사용 되는 응용 프로그램 정보를 식별 합니다.

## <a name="syntax"></a>Syntax

```xml

      <description 
   publisher 
   product
   suiteName
   supportUrl
/>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `description` 요소는 필수이며 `urn:schemas-microsoft-com:asm.v1` 네임스페이스에 있습니다. 자식 요소를 포함 하지 않으며 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`publisher`|필수 요소. 설치를 위해 배포를 구성한 경우 Windows **시작** 메뉴와 제어판의 **프로그램 추가/제거** 항목에서 아이콘 배치에 사용 되는 회사 이름을 식별 합니다.|
|`product`|필수 요소. 전체 제품 이름을 식별 합니다. Windows **시작** 메뉴에 설치 된 아이콘의 제목으로 사용 됩니다.|
|`suiteName`|선택 사항입니다. `publisher`Windows **시작** 메뉴의 폴더 내에 있는 하위 폴더를 식별 합니다.|
|`supportUrl`|선택 사항입니다. 제어판의 **프로그램 추가/제거** 항목에 표시 되는 지원 URL을 지정 합니다. 이 URL에 대 한 바로 가기는 배포를 설치 하도록 구성 된 경우 Windows **시작** 메뉴에서 응용 프로그램 지원에 대해서도 만들어집니다.|

## <a name="remarks"></a>설명
 설명 요소는 모든 배포 구성에 필요 합니다.

## <a name="example"></a>예
 다음 코드 예제에서는 `description` 배포 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이 코드 예제는 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md) 항목에 대해 제공 되는 더 큰 예제의 일부입니다.

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
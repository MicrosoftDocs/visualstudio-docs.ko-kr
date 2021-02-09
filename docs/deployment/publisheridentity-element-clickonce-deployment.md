---
title: '&lt;publisherIdentity &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
description: PublisherIdentity 요소는 배포 매니페스트를 서명한 게시자에 대 한 정보를 포함 합니다. 서명 된 매니페스트에는 요소가 필요 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891295"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity &gt; 요소 (ClickOnce 배포)
이 배포 매니페스트에 서명한 게시자에 대한 정보를 포함합니다.

## <a name="syntax"></a>구문

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `publisherIdentity`서명 된 매니페스트에는 요소가 필요 합니다. 다음 표에서는 요소가 지 원하는 특성을 보여 줍니다 `publisherIdentity` .

|attribute|Description|
|---------------|-----------------|
|`name`|필수 사항입니다. 이 응용 프로그램을 게시 한 파티의 id를 설명 합니다.|
|`issuerKeyHash`|필수 사항입니다. 인증서 발급자의 공개 키에 대 한 SHA-1 해시를 포함 합니다.|

#### <a name="parameters"></a>매개 변수

## <a name="property-valuereturn-value"></a>속성 값/반환 값

## <a name="exceptions"></a>예외

## <a name="remarks"></a>설명

## <a name="requirements"></a>요구 사항

## <a name="subhead"></a>부제목
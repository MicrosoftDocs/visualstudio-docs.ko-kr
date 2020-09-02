---
title: Xml(XElement 동적 속성) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c794d79d62fc580001efc5cf16993d4ac5fef48b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663841"
---
# <a name="xml-xelement-dynamic-property"></a>Xml(XElement 동적 속성)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요소의 서식이 지정되지 않은 XML 내용을 가져옵니다.

## <a name="syntax"></a>Syntax

```
elem.Xml
```

## <a name="property-valuereturn-value"></a>속성 값/반환 값
 요소의 서식이 지정되지 않은 XML 내용을 나타내는 <xref:System.String>입니다.

## <a name="remarks"></a>설명
 이 속성은 <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> 매개 변수가 <xref:System.Xml.Linq.XNode?displayProperty=fullName>으로 설정된 `SaveOptions` 클래스의 <xref:System.Xml.Linq.SaveOptions> 메서드와 동일합니다.

## <a name="see-also"></a>관련 항목
 [XElement 클래스 동적 속성](../designers/xelement-class-dynamic-properties.md) [값](../designers/value-xelement-dynamic-property.md)

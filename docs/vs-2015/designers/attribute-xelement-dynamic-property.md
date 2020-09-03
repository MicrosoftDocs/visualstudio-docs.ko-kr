---
title: Attribute(XElement 동적 속성) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 551e072b05e7a88ff9624c5d16e4aa199a6afd66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657976"
---
# <a name="attribute-xelement-dynamic-property"></a>특성(XElement 동적 속성)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지정한 확장된 이름에 해당하는 특성 인스턴스를 검색하는 데 사용되는 인덱서를 가져옵니다.

## <a name="syntax"></a>Syntax

```
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>속성 값/반환 값
 `XAttribute Item(String expandedName)` 형식의 인덱서입니다. 이 인덱서는 지정된 특성의 확장된 이름을 사용하여 해당하는 <xref:System.Xml.Linq.XAttribute>를 반환하거나 지정된 이름을 가진 특성이 없는 경우 `null`을 반환합니다.

## <a name="remarks"></a>설명
 이 속성은 <xref:System.Xml.Linq.XElement.Attribute%2A> 클래스의 <xref:System.Xml.Linq.XElement?displayProperty=fullName> 메서드와 동일합니다.

## <a name="see-also"></a>관련 항목
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>[XElement 클래스 동적 속성](../designers/xelement-class-dynamic-properties.md) [값](../designers/value-xattribute-dynamic-property.md)

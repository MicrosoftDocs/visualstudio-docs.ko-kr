---
title: 서식 지정, XML, 텍스트 편집기, 옵션 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670968"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>서식 지정, XML, 텍스트 편집기, 옵션 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 대화 상자를 사용하여 XML 편집기의 서식 설정을 지정할 수 있습니다. **옵션** 대화 상자는 **도구** 메뉴에서 액세스할 수 있습니다.

> [!NOTE]
> 이러한 설정은 **옵션** 대화 상자에서 **텍스트 편집기** 폴더,**XML** 폴더, **서식** 옵션을 차례로 선택할 때 사용할 수 있습니다.

## <a name="attributes"></a>특성
 **수동으로 특성 서식 유지** 특성은 다시 포맷 되지 않습니다. 이것이 기본값입니다.

> [!NOTE]
> 특성이 여러 줄로 된 경우 편집기에서 상위 요소의 들여쓰기에 맞게 특성의 각 줄을 들여씁니다.

 **각각의 줄에 특성 맞춤** 첫 번째 특성의 들여쓰기에 맞게 두 번째 및 이후의 특성을 세로로 정렬 합니다. 다음 XML 텍스트는 특성 정렬 방법의 예입니다.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>자동 서식 다시 설정
 **클립보드에서 붙여 넣을 때** 클립보드에서 붙여 넣은 XML 텍스트를 다시 포맷 합니다.

 **끝 태그 완료 시** 끝 태그가 완료 될 때 요소 서식을 다시 입력 합니다.

## <a name="mixed-content"></a>혼합 내용
 **기본적으로 혼합 내용 유지** 편집기에서 혼합 콘텐츠의 서식을 다시 지정 하는지 여부를 결정 합니다. 혼합 내용이 `xml:space="preserve"` 범위에 있는 경우를 제외하고 기본적으로 편집기에서는 혼합 내용의 서식을 다시 지정하려고 시도합니다.

 요소에 텍스트와 마크업이 혼합되어 있으면 콘텐츠가 혼합된 콘텐츠로 간주됩니다. 다음은 혼합 내용이 포함된 요소의 예제입니다.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>관련 항목
 [Xml 문서 속성, 속성 창](../xml-tools/xml-document-properties-properties-window.md) [Xml 편집기 구성 요소](../xml-tools/xml-editor-components.md)

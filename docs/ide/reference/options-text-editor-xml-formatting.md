---
title: 옵션, 텍스트 편집기, XML, 서식 지정
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5dabfbc4f705d7de9fa881f373994714e43d26a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568141"
---
# <a name="options-text-editor-xml-formatting"></a>옵션, 텍스트 편집기, XML, 서식 지정

**서식 지정** 옵션 페이지를 사용하여 XML 문서에서 요소와 특성의 형식 지정 방법을 지정할 수 있습니다. XML 서식 지정 옵션에 액세스하려면 **도구** > **옵션** > **텍스트 편집기** > **XML**을 선택한 다음, **서식 지정**을 선택합니다.

## <a name="attributes"></a>특성

**수동으로 지정한 특성 서식 유지**

특성 서식을 다시 설정하지 마십시오. 이 설정은 기본값입니다.

> [!NOTE]
> 특성이 여러 줄로 된 경우 편집기에서 상위 요소의 들여쓰기에 맞게 특성의 각 줄을 들여씁니다.

**별도의 줄에 특성 맞춤**

첫 번째 특성의 들여쓰기에 맞게 두 번째 및 이후의 특성을 세로로 정렬합니다. 다음 XML 텍스트는 특성을 정렬하는 방법의 예제입니다.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>자동 서식 다시 설정

**클립보드에서 붙여 넣을 때**

클립보드에서 붙여 넣은 XML 텍스트 서식을 다시 설정합니다.

**끝 태그 완료 시**

끝 태그가 완료될 때 요소 서식을 다시 설정합니다.

## <a name="mixed-content"></a>혼합된 콘텐츠

**기본값으로 혼합 콘텐츠 서식 지정**

`xml:space="preserve"` 범위에 콘텐츠가 있을 때를 제외하고 혼합된 콘텐츠 서식을 다시 설정하려고 합니다. 이 설정은 기본값입니다.

요소에 텍스트와 마크업이 혼합되어 있으면 콘텐츠가 혼합된 콘텐츠로 간주됩니다. 다음은 혼합된 콘텐츠가 있는 요소의 예입니다.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>참고 항목

- [XML 옵션 - 기타](options-text-editor-xml-miscellaneous.md)
- [Visual Studio의 XML 도구](../../xml-tools/xml-tools-in-visual-studio.md)

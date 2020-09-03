---
title: '방법: 사용할 XML 스키마 선택 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666514"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>방법: 사용할 XML 스키마 선택
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 편집기에서는 %InstallDir%\Xml\Schemas 디렉터리에 있는 스키마 캐시를 제공합니다. 이 스키마 캐시에는 잘 알려진 XML 스키마가 포함되어 있으며 이 스키마는 IntelliSense 및 XML 문서 유효성 검사에 사용됩니다.

 **스키마** 문서 속성은 사용할 하나 이상의 XSD (XML 스키마 정의 언어) 스키마를 선택 하는 데 사용 됩니다. 즉, 이 속성을 사용하면 스키마 캐시에서 스키마를 선택하거나 캐시에 없는 스키마를 지정할 수 있습니다.

 지정한 스키마는 다른 모든 XML 문서 속성과 함께 숨겨진 솔루션 사용자 옵션 파일(.suo)에 저장됩니다. 그러므로 다음 번에 솔루션을 열 때 이러한 값을 다시 입력하지 않아도 됩니다.

> [!NOTE]
> 편집기에서는 인라인 스키마 또는 `xsd:schemaLocation` 특성이 참조하는 스키마를 사용하여 유효성을 검사할 수 있습니다. 자세한 내용은 [XML 문서 유효성 검사](../xml-tools/xml-document-validation.md)를 참조 하세요.

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>스키마 캐시에서 XML 스키마를 선택하려면

1. XML 편집기에서 파일을 엽니다.

2. 문서 속성 창의 **스키마** 필드에서 단추를 클릭합니다.

    **XML 스키마** 대화 상자가 표시 됩니다. 이 대화 상자에는 스키마 캐시의 확장명이 .xsd 인 모든 스키마 (catalog.xml 파일에서 참조 되는 스키마 포함)와 현재 솔루션에 있는 스키마, Visual Studio에서 열기, 특성에서 참조 `xsd:schemaLocation` 또는 **스키마** 속성에서 참조 되는 스키마가 나열 됩니다.

3. 다음 중 하나를 수행하여 유효성 검사에 사용할 스키마를 선택합니다.

   - **XML 스키마** 대화 상자에 나열되어 있는 스키마를 선택하고 **사용** 열을 클릭한 다음, **이 스키마 사용**을 선택합니다.

     또는

   - **XML 스키마** 대화 상자에 나열 된 여러 스키마를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **이 스키마 사용**을 선택 합니다.

4. **확인**을 클릭합니다.

    선택한 스키마의 목록이 다시 **스키마** 문서 속성에 복사됩니다.

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>스키마 캐시에 XML 스키마를 추가하려면

1. 문서 속성 창의 **스키마** 필드에서 단추를 클릭합니다.

2. **추가**를 클릭합니다.

     그러면 **XSD 스키마 열기** 대화 상자가 열립니다.

3. 스키마 캐시에 추가할 스키마를 찾아 선택합니다.

4. **열기**를 클릭합니다.

     스키마 캐시에 추가 된 스키마 및 **사용** 열 값 **이이 스키마를 사용**하도록 설정 되어 있습니다.

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>스키마 캐시에서 XML 스키마를 삭제하려면

1. 문서 속성 창의 **스키마** 필드에서 단추를 클릭합니다.

2. 제거할 스키마를 선택하고 **제거**를 클릭합니다.

     그러면 스키마가 메모리 내 스키마 캐시에서 제거되지만 파일 시스템에서는 제거되지 않습니다.

    > [!NOTE]
    > `schemaLocation` 특성 또는 일치하는 `targetNamespace`를 통한 스키마 참조가 아직 남아 있으면 자동 연결로 인해 **제거**를 수행해도 스키마가 제거되지 않습니다. 이 경우에는 **사용** 열에서 스키마를 **선택한 스키마 사용 안 함**으로 표시하는 것이 좋습니다.

## <a name="see-also"></a>관련 항목
 [스키마 캐시](../xml-tools/schema-cache.md) [Xml 스키마 대화 상자](../xml-tools/xml-schemas-dialog-box.md) [xml 편집기](../xml-tools/xml-editor.md)

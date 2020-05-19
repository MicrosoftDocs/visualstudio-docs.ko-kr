---
title: XML 문서 속성, 속성 창
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b21f4435737597136e1ac4a4dd8651decaf4c65
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592427"
---
# <a name="xml-document-properties-properties-window"></a>XML 문서 속성, 속성 창

**속성** 창에서는 XML 편집기에서 활성화된 문서에 대한 기본 정보를 제공합니다. 현재 활성화되어 있는 XML 문서의 형식에 따라 사용할 수 있는 속성이 달라집니다.

> [!NOTE]
> 모든 XML 문서 속성은 솔루션에 저장됩니다. 그러면 다음에 솔루션을 열 때는 이러한 값을 다시 입력하지 않아도 됩니다.

**인코딩**

파일에 대한 문자 인코딩입니다. 이 속성을 변경하면 XML 선언의 인코딩 특성도 변경되며 XML 선언의 인코딩 특성을 변경하면 이 속성도 변경됩니다. 파일을 저장할 때 새 인코딩을 사용하여 파일이 인코딩됩니다.

**입력**

XSLT 스타일시트에 연결된 입력 문서입니다. **XSLT 시작** 명령(예: **XML** > **디버그하지 않고 XSLT 시작**)에서 사용됩니다. 찾아보기( **...** ) 단추를 사용하여 문서를 선택할 수 있습니다.

편집기에서 XSLT 파일이 열려 있는 경우에만 이 속성이 표시됩니다.

**출력**

XML 문서를 변형할 때 생성되는 파일입니다.

파일을 지정하지 않으면 파일 확장명을 결정하는 `xsl:output` 요소의 `method` 특성을 기준으로 기본 파일 이름이 생성됩니다. 기본 파일은 현재 사용자의 임시 디렉터리에 있습니다.

**스키마**

유효성 검사에 사용할 스키마입니다. 이 단추를 클릭하면 사용할 스키마를 선택할 수 있는 **XSD 스키마** 대화 상자가 열립니다.

스키마 경로를 입력할 수도 있습니다. 여러 스키마를 지정할 경우 각 스키마 경로를 큰따옴표로 묶어야 합니다.

**스타일시트**

**XSLT 디버깅 시작** 및 **디버그하지 않고 XSLT 시작** 명령을 사용하는 경우 문서를 변환하는 데 사용되는 XSLT 파일입니다. 이 필드가 비어 있으면 편집기에서 문서의 `xml-stylesheet` 처리 명령에 제공된 값이 사용되거나 파일 이름을 입력하라는 메시지가 나타납니다.

XSLT 파일을 편집할 때 이 속성을 사용하면 **XSLT 디버깅 시작** 또는 **디버그하지 않고 XSLT 시작** 명령을 선택한 경우 다른 스타일시트를 사용하도록 지정할 수 있습니다. 예를 들어, 부모 스타일시트에 포함된 스타일시트를 편집할 때 이 작업을 수행할 수 있습니다.

## <a name="see-also"></a>참조

- [XML 편집기](../xml-tools/xml-editor.md)

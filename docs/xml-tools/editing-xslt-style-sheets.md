---
title: XSLT 스타일시트 편집
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81bab324c58c06cc1ca553bae2f81faf474c4ad0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592843"
---
# <a name="edit-xslt-style-sheets"></a>XSLT 스타일시트 편집

XML 편집기를 사용하여 XSLT 스타일시트를 편집할 수 있습니다. 이 편집기에서는 IntelliSense, 개요, XML 조각 등의 기본 편집기 기능을 사용할 수 있습니다. 또한 XSLT에서 쉽게 개발할 수 있게 하는 새 기능도 있습니다.

## <a name="xslt-features"></a>XSLT 기능

다음 표에서는 XSLT 스타일시트 작업과 관련된 기능을 설명합니다.

**구문 색 지정**

`template`, `match` 등의 XSLT 키워드는 **글꼴 및 색** 설정에 지정된 XSLT 키워드 색으로 표시됩니다.

**물결무늬 밑줄**

XML 편집기에서는 설치된 *xslt.xsd* 파일을 사용하여 XSLT 스타일시트의 유효성을 검사합니다. 유효성 검사 오류는 파란색 물결무늬 밑줄로 표시되고 또한 XML 편집기는 백그라운드에서 스타일시트를 컴파일하고 적합한 물결무늬 밑줄로 컴파일러 오류 또는 경고를 보고합니다.

**스크립트 블록 지원**

XSLT 디버거에서 스크립트 블록의 코드를 지원하므로 중단점을 설정하고 스크립트 블록 코드를 단계별로 실행할 수 있습니다.

**XSLT 출력 보기**

XML 편집기에서 XSL 변환을 실행하고 출력을 볼 수 있습니다. 자세한 내용은 [방법: XML 편집기에서 XSLT 변환 실행](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)을 참조하세요.

**XSLT 디버그**

XML 편집기에서는 XSLT 파일에서 XSLT 디버거를 시작할 수 있습니다. 이 디버거에서는 XSLT 파일에서 중단점 설정, XSLT 실행 상태 보기 등을 지원합니다. XSLT 변수 위로 마우스를 움직이면 변수 값과 함께 도구 설명이 표시됩니다. 이 디버거를 사용하여 스타일시트를 디버깅하거나 다른 애플리케이션에서 호출한 컴파일된 XSL 변환을 디버깅할 수 있습니다. 자세한 내용은 [XSLT 디버깅](../xml-tools/debugging-xslt.md)을 참조하세요.

## <a name="see-also"></a>참조

- [XML 편집기](../xml-tools/xml-editor.md)

---
title: XSLT 스타일 시트 편집 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e1669affa89c91ca3ae1958c22ff3ec4d56bb8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670962"
---
# <a name="editing-xslt-style-sheets"></a>XSLT 스타일시트 편집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 편집기를 사용하여 XSLT 스타일시트를 편집할 수 있습니다. 이 편집기에서는 IntelliSense, 개요, XML 조각 등의 기본 편집기 기능을 사용할 수 있습니다. 또한 XSLT에서 쉽게 개발할 수 있게 하는 새 기능도 있습니다.

## <a name="xslt-features"></a>XSLT 기능
 다음 표에서는 XSLT 스타일시트 작업과 관련된 기능을 설명합니다.

 **구문 색** 지정 , 등의 XSLT 키워드 `template` `match` 는 **글꼴 및 색** 설정에 지정 된 xslt 키워드 색에 표시 됩니다.

 **물결 무늬 밑줄** XML 편집기는 설치 된 xslt .xsd 파일을 사용 하 여 XSLT 스타일 시트의 유효성을 검사 합니다. 유효성 검사 오류는 파란색 물결무늬 밑줄로 표시되고 또한 XML 편집기는 백그라운드에서 스타일시트를 컴파일하고 적합한 물결 무늬 밑줄로 컴파일러 오류 또는 경고를 보고합니다.

 **스크립트 블록 지원** 스크립트 블록의 코드는 XSLT 디버거에서 지원 되므로 중단점을 설정 하 고 스크립트 블록 코드를 단계별로 실행 할 수 있습니다.

 **XSLT 출력 보기** XML 편집기에서 XSL 변환을 실행 하 고 출력을 볼 수 있습니다. 자세한 내용은 [방법: XML 편집기에서 XSLT 변환 실행](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md)을 참조 하세요.

 **XSLT 디버깅** XML 편집기의 XSLT 파일에서 XSLT 디버거를 시작할 수 있습니다. 이 디버거에서는 XSLT 파일에서 중단점 설정, XSLT 실행 상태 보기 등을 지원합니다. XSLT 변수 위로 마우스를 움직이면 변수 값과 함께 도구 설명이 표시됩니다. 이 디버거를 사용하여 스타일시트를 디버깅하거나 다른 애플리케이션에서 호출한 컴파일된 XSL 변환을 디버깅할 수 있습니다. 자세한 내용은 [XSLT 디버깅](../xml-tools/debugging-xslt.md)을 참조하세요.

## <a name="see-also"></a>관련 항목
 [XML 편집기](../xml-tools/xml-editor.md)

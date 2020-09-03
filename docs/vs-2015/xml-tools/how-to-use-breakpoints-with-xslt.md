---
title: '방법: XSLT에 중단점 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656302"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>방법: XSLT에 중단점 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT 스타일시트 또는 XML 소스 문서에서 중단점을 설정할 수 있습니다. 태그에 중단점을 설정한 경우 실행을 시작하면 소스 줄 정보가 있는 다음 문으로 중단점이 이동합니다.

 자세한 내용은 [디버깅 기본 사항: 중단점](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)을 참조 하세요.

## <a name="set-a-breakpoint-in-a-style-sheet"></a>스타일시트에서 중단점 설정
 중단점은 XSLT 스타일시트의 모든 시작 태그, 끝 태그 및 텍스트 노드에 설정할 수 있으며 스크립트 블록의 코드에 대해서도 설정할 수 있습니다.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>스타일시트에서 중단점을 설정하려면

1. XML 편집기에서 스타일시트를 엽니다.

2. 중단점 위치에 커서를 놓고 마우스 오른쪽 단추를 클릭 하 고 **중단점**을 가리킨 다음 **중단점 삽입**을 클릭 합니다.

3. 문서 속성 창의 **입력** 필드에서 찾아보기 단추 (**...**)를 클릭 합니다.

4. XML 원본 문서를 찾고 **열기**를 클릭 합니다.

     그러면 XSLT 변형에 사용되는 소스 문서 파일이 설정됩니다.

5. XML 편집기 도구 모음에서 **XSL 디버깅** 단추를 클릭 합니다.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>XML 소스 문서에서 중단점 설정
 또한 중단점은 XML 소스 문서의 요소, 특성, 네임스페이스 노드, 주석, 처리 명령 및 텍스트 노드에 대해 설정할 수 있습니다. 그러나 부모 요소에서 상속되는 네임스페이스 노드나 문서 노드에 대해서는 중단점을 설정할 수 없습니다.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>XML 소스 문서에서 중단점을 설정하려면

1. XML 편집기에서 XML 문서를 엽니다.

2. 중단점 위치에 커서를 놓고 마우스 오른쪽 단추를 클릭 하 고 **중단점**을 가리킨 다음 **중단점 삽입**을 클릭 합니다.

3. 문서 속성 창의 **스타일 시트** 필드에서 찾아보기 단추 (**...**)를 클릭 합니다.

4. XML 원본 문서를 찾고 **열기**를 클릭 합니다.

     그러면 XSLT 변형에 사용되는 소스 문서 파일이 설정됩니다.

5. XML 편집기 도구 모음에서 **XSL 디버깅** 단추를 클릭 합니다.

## <a name="see-also"></a>관련 항목
 [연습: XSLT 스타일 시트 디버깅](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)

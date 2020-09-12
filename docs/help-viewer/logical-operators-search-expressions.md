---
title: 검색 식의 논리 연산자 (도움말 뷰어)
ms.custom: SEO-VS-2020
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9daceca2540a2da61a46e12a458c012ce7851001
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038636"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>검색 식의 논리 및 고급 연산자

논리 연산자 및 고급 검색 연산자를 사용 하 여 **도움말 뷰어에서**도움말 콘텐츠의 검색을 구체화할 수 있습니다.

## <a name="logical-operators"></a>논리 연산자

논리 연산자는 여러 검색어가 검색 쿼리에서 결합되는 방식을 지정합니다. 다음 표는 논리 연산자 AND, OR, NOT 및 NEAR을 보여줍니다.

|검색 대상|Windows Server Update Services와 함께|예제|결과|
|-------------------|---------|-------------|------------|
|동일한 아티클에 두 용어가 모두 있음|AND|dib AND palette|"dib" 및 "palette"를 둘 다 포함하는 항목|
|아티클에 두 용어 중 하나가 있음|또는|raster OR vector|"raster" 또는 "vector"를 포함하는 항목|
|동일한 아티클에 첫 번째 용어는 있고 두 번째 용어는 없음|NOT|"operating system" NOT DOS|"operating system"을 포함하지만 "DOS"를 포함하지 않는 항목|
|한 아티클에 두 용어가 서로 가까이 있음|NEAR|user NEAR kernel|"kernel"의 근접 범위 내에 "user"를 포함하는 항목|

> [!IMPORTANT]
> 검색 엔진에서 인식할 수 있도록 논리 연산자는 모두 대문자로 입력해야 합니다.

## <a name="advanced-operators"></a>고급 연산자

고급 검색 연산자는 아티클에서 검색어를 찾을 위치를 지정하여 콘텐츠 검색을 구체화합니다. 다음 표에서 4개의 사용 가능한 고급 검색 연산자를 설명합니다.

|검색 대상|Windows Server Update Services와 함께|예제|결과|
|-------------------|---------|-------------|------------|
|아이클 제목의 용어|`title:`|`title:binaryreader`|제목에 “binaryreader”가 포함된 항목입니다.|
|코드 예제의 용어|`code:`|`code:readdouble`|코드 예제에 “readdouble”이 포함된 항목입니다.|
|특정 프로그래밍 언어 예제의 용어|`code:vb:`|`code:vb:string`|Visual Basic 코드 예제에 “string”이 포함된 항목입니다.|
|특정 인덱스 키워드와 연결된 아티클|`keyword:`|`keyword:readbyte`|“readbyte” 인덱스 키워드와 연결된 항목입니다.|

> [!IMPORTANT]
> 검색 엔진이 이러한 연산자를 인식하려면 고급 검색 연산자 뒤에 불필요한 공백 없이 마지막으로 콜론을 입력해야 합니다.

### <a name="programming-languages-for-code-examples"></a>코드 예제에 대한 프로그래밍 언어

`code:` 연산자를 사용하여 여러 프로그래밍 언어에 대한 콘텐츠를 찾을 수 있습니다. 특정 프로그래밍 언어에 대한 예제를 반환하려면 다음과 같은 프로그래밍 언어 값 중 하나를 사용합니다.

|프로그래밍 언어|검색 연산자 구문|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> `code:` 연산자는 일반적으로 코드로 표시되는 콘텐츠와는 반대로, 프로그래밍 언어 레이블로 표시되는 콘텐츠만 찾습니다.

## <a name="see-also"></a>참고 항목

- [방법: 항목 검색](../help-viewer/find-topics.md)
- [Microsoft 도움말 뷰어](../help-viewer/overview.md)

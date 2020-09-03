---
title: DSL 정의의 속성
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee23e15e6cc389ea5a8bdcdd793648365d08c30d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532304"
---
# <a name="properties-of-a-dsl-definition"></a>DSL 정의의 속성
DslDefinition 속성은 버전 번호 매기기와 같은 *도메인별 언어* 정의 속성을 정의 합니다. *도메인 특정 언어 디자이너*에서 다이어그램의 열린 영역을 클릭 하면 **속성** 창에 dsldefinition 속성이 나타납니다.

 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

 DslDefinition에는 다음 표의 속성이 있습니다.

|속성|설명|기본값|
|-|-|-|
|액세스 한정자|도메인 클래스의 액세스 한정자가 public 또는 internal 인지 여부를 확인 합니다.|public|
|사용자 지정 특성|도메인 클래스에 대해 정의 된 사용자 지정 특성입니다.<br /><br /> **참고** 찾아보기 단추를 사용 하 여 특성을 추가 합니다.|\<none>|
|회사 이름|시스템 레지스트리의 현재 회사 이름 이름입니다.|현재 회사 이름|
|Name|이 도메인 클래스의 이름입니다.|현재 이름|
|네임스페이스|이 도메인 클래스와 관련 된 네임 스페이스입니다.|현재 네임 스페이스|
|패키지 Guid|이 DSL에 대해 생성 된 Visual Studio 패키지의 guid입니다.|\<none>|
|패키지 네임 스페이스|이 DSL에 대해 생성 된 Visual Studio 패키지의 네임 스페이스입니다.|\<none>|
|제품 이름|이 DSL에 대해 생성 된 Visual Studio 패키지에 등록할 제품의 이름입니다.|\<none>|
|참고|이 도메인 클래스와 연결 된 메모입니다.|\<none>|
|설명|이 도메인 클래스에 대 한 설명입니다.|\<none>|
|표시 이름|이 도메인 클래스에 대해 생성 된 디자이너에 표시 되는 이름입니다.|\<none>|
|Help Keyword|이 도메인 클래스와 연결 된 도움말 키워드입니다.|\<none>|
|빌드|이 도메인별 언어 정의에 대 한 증분 빌드 번호입니다.|0|
|주 버전|이 도메인별 언어 정의에 대 한 증분 주 빌드 번호입니다.|1|
|부 버전|이 도메인별 언어 정의의 증분 부 빌드 번호입니다.|0|
|수정 버전|이 도메인별 언어 정의에 대 한 증분 수정 버전 빌드 번호입니다.|0|

## <a name="see-also"></a>참고 항목

- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
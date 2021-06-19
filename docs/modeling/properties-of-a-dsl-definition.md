---
title: DSL 정의의 속성
description: DslDefinition 속성이 버전 번호 매기기와 같은 도메인별 언어 정의 속성을 정의하는지 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6212dfcb9e93110a97e7143e5b1c946efebee89f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390843"
---
# <a name="properties-of-a-dsl-definition"></a>DSL 정의의 속성
DslDefinition 속성은 버전 번호 매기기와 같은 *도메인별 언어* 정의 속성을 정의합니다. DslDefinition 속성은 *도메인 특정 언어 디자이너* 다이어그램의 열린 영역을 클릭하면 **속성** 창에 나타납니다.

 자세한 내용은 [Domain-Specific 언어를 정의하는 방법을 참조하세요.](../modeling/how-to-define-a-domain-specific-language.md) 이러한 속성을 사용하는 방법에 대한 자세한 내용은 [Domain-Specific 언어 사용자 지정 및 확장을 참조하세요.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 DslDefinition에는 다음 표의 속성이 있습니다.

|속성|설명|기본값|
|-|-|-|
|액세스 한정자|도메인 클래스에 대한 액세스 한정자가 public 또는 internal인지 확인합니다.|public|
|사용자 지정 특성|도메인 클래스에 대한 사용자 지정 정의 특성입니다.<br /><br /> **참고** 찾아보기 단추를 사용하여 특성을 추가합니다.|\<none>|
|회사 이름|시스템 레지스트리에 있는 현재 회사 이름의 이름입니다.|현재 회사 이름|
|속성|이 도메인 클래스의 이름입니다.|현재 이름|
|네임스페이스|이 도메인 클래스와 관련된 네임스페이스입니다.|현재 네임스페이스|
|패키지 Guid|이 DSL에 대해 생성된 Visual Studio 패키지의 guid입니다.|\<none>|
|패키지 네임스페이스|이 DSL에 대해 생성된 Visual Studio 패키지의 네임스페이스입니다.|\<none>|
|제품 이름|이 DSL에 대해 생성된 Visual Studio 패키지에 등록할 제품의 이름입니다.|\<none>|
|참고|이 도메인 클래스와 관련된 참고 사항입니다.|\<none>|
|설명|이 도메인 클래스에 대한 설명입니다.|\<none>|
|표시 이름|이 도메인 클래스에 대해 생성된 디자이너에 표시할 이름입니다.|\<none>|
|Help Keyword|이 도메인 클래스와 연결된 help 키워드입니다.|\<none>|
|빌드|이 도메인별 언어 정의에 대한 증분 빌드 번호입니다.|0|
|주 버전|이 도메인별 언어 정의에 대한 증분 주 빌드 번호입니다.|1|
|부 버전|이 도메인별 언어 정의에 대한 증분 부 빌드 번호입니다.|0|
|수정 버전|이 도메인별 언어 정의에 대한 증분 수정 빌드 번호입니다.|0|

## <a name="see-also"></a>참고 항목

- [도메인 특정 언어 도구 용어집](/previous-versions/bb126564(v=vs.100))
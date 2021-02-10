---
title: 다이어그램의 속성
description: 다이어그램 및 생성 된 디자이너에서 다이어그램이 표시 되는 방법을 지정 하는 속성을 설정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language, diagram
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 943b634114c28f6f914926c74861a902c663523e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956167"
---
# <a name="properties-of-diagrams"></a>다이어그램의 속성
생성 된 디자이너에서 다이어그램이 표시 되는 방법을 지정 하는 속성을 설정할 수 있습니다. 예를 들어 다이어그램에서 텍스트의 기본 색을 지정할 수 있습니다.

 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

 다음 표에서는 다이어그램의 속성을 보여 줍니다.

|속성|Description|기본값|
|-|-|-|
|채우기 색|다이어그램의 채우기 색입니다.|흰색|
|텍스트 색|다이어그램에 표시 되는 텍스트의 색입니다.|검정|
|액세스 한정자|클래스의 액세스 한정자입니다 (공용 또는 내부).|공용|
|사용자 지정 특성|생성 된 코드 클래스에 특성을 추가 하는 데 사용 됩니다.|\<none>|
|Double 파생을 생성 합니다.|이면 `True` 재정의를 통한 사용자 지정을 지원 하기 위해 기본 클래스와 partial 클래스가 모두 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|False|
|사용자 지정 생성자 있음|이면 `True` 사용자 지정 생성자가 소스 코드에 제공 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하십시오.|False|
|상속 한정자|다이어그램 ( `none` , 또는)에서 생성 되는 소스 코드 클래스의 상속 종류에 대해 설명 합니다 `abstract` `sealed` .|None|
|기본 다이어그램|이 다이어그램의 기본 클래스입니다.|(없음)|
|이름|이 다이어그램의 이름입니다.|현재 이름|
|네임스페이스|이 다이어그램과 관련 된 네임 스페이스입니다.|현재 네임 스페이스|
|표시 되는 클래스|이 다이어그램이 나타내는 루트 도메인 클래스입니다.|해당 하는 경우 현재 루트 클래스|
|참고|이 요소와 연결 된 비공식 메모입니다.|\<none>|
|채우기 색을 속성으로 노출 합니다.|인 경우 `True` 사용자는 생성 된 디자이너 다이어그램의 채우기 색을 설정할 수 있습니다. 이 속성을 설정 하려면 다이어그램 셰이프를 마우스 오른쪽 단추로 클릭 하 고 **노출 추가** 를 클릭 합니다.|False|
|텍스트 색을 속성으로 노출 합니다.|인 경우 `True` 사용자는 생성 된 디자이너에서 다이어그램의 텍스트 색을 설정할 수 있습니다. 이 속성을 설정 하려면 다이어그램 셰이프를 마우스 오른쪽 단추로 클릭 하 고 **노출 추가** 를 클릭 합니다.|False|
|Description|생성 된 디자이너를 문서화 하는 데 사용 되는 설명입니다.|\<none>|
|표시 이름|이 다이어그램에 대해 생성 된 디자이너에 표시 되는 이름입니다.|\<none>|
|Help Keyword|이 다이어그램에 대 한 F1 도움말을 인덱싱하는 데 사용 되는 키워드입니다.|\<none>|

## <a name="see-also"></a>참고 항목

[도메인 특정 언어 도구 용어집](/previous-versions/bb126564(v=vs.100))
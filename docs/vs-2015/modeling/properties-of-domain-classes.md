---
title: 도메인 클래스의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 91599e17fc132001de9fbb1a62a62918321a2dea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652000"
---
# <a name="properties-of-domain-classes"></a>도메인 클래스의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도메인 클래스의 속성은 다음 표에 나와 있습니다. 도메인 클래스에 대 한 자세한 내용은 [모델, 클래스 및 관계 이해](../modeling/understanding-models-classes-and-relationships.md)를 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

|속성|설명|기본값|
|--------------|-----------------|-------------|
|액세스 한정자|도메인 클래스의 액세스 수준입니다(`public` 또는 `internal`).|`public`|
|사용자 지정 특성|이 도메인 클래스에서 생성 되는 소스 코드 클래스에 특성을 추가 하는 데 사용 됩니다.|\<none>|
|Double 파생을 생성 합니다.|이면 `True` 재정의를 통한 사용자 지정을 지원 하기 위해 기본 클래스와 partial 클래스가 모두 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|`False`|
|사용자 지정 생성자 있음|이면 `True` 사용자 지정 생성자가 소스 코드에 제공 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|`False`|
|상속 한정자|도메인 클래스 (또는)에서 생성 되는 소스 코드 클래스의 상속 종류에 대해 설명 `none` 합니다 `abstract` `sealed` .|`none`|
|기본 클래스|이 도메인 클래스가 파생 된 경우 기본 클래스의 이름입니다.|\<none>|
|Name|이 도메인 클래스의 이름입니다.|현재 이름|
|네임스페이스|이 도메인 클래스의 네임 스페이스입니다.|현재 네임 스페이스|
|참고|이 도메인 클래스와 연결 된 비공식 메모입니다.|\<none>|
|설명|생성 된 디자이너의 UI를 문서화 하는 데 사용 되는 설명입니다.|\<none>|
|표시 이름|이 도메인 클래스에 대해 생성 된 디자이너에 표시 되는 이름입니다.|\<none>|
|Help Keyword|이 도메인 클래스에 대 한 F1 도움말을 인덱싱하는 데 사용 되는 선택적 키워드입니다.|\<none>|

## <a name="see-also"></a>관련 항목
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

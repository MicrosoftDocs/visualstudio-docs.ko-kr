---
title: Port 셰이프 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
ms.assetid: 9d69c4c1-4f72-4876-96b6-9b846e0495a4
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 906a35f1b564c4e3794d1000f03cb32cda003ca2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671357"
---
# <a name="properties-of-port-shapes"></a>포트 모양의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

포트 셰이프를 사용 하 여 생성 된 디자이너에서 도메인 클래스를 나타낼 수 있습니다.

 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

 포트 셰이프에는 다음 표에 나열 된 속성이 있습니다.

|속성|설명|기본값|
|--------------|-----------------|-------------|
|채우기 색|이 도형의 채우기 색입니다.|흰색|
|채우기 그라데이션 모드|이 도형의 채우기 그라데이션 모드입니다.|수평적 크기 조정|
|기하 도형|이 도형 (사각형, 둥근 사각형, 타원 또는 원)의 기 하 도형입니다.|직사각형|
|기본 연결 지점이 있음|이면 `True` 셰이프는 생성 된 디자이너에서 위쪽, 아래쪽, 왼쪽 및 오른쪽 연결 위치를 사용 합니다.|False|
|윤곽선 색|이 도형의 윤곽선 색입니다.|검정|
|윤곽선 파선 스타일|이 도형의 윤곽선 대시 스타일 (Solid, 대시, 점, 일점 Dot, DashDotDot 또는 Custom)입니다.|단색|
|윤곽선 두께|이 도형의 윤곽선 두께입니다.|0.03125|
|텍스트 색|이 모양과 연결 된 텍스트 데코레이터에 사용 되는 색입니다.|검정|
|액세스 한정자|클래스의 액세스 수준 ( `public` 또는 `internal` )입니다.|공용|
|사용자 지정 특성|이 셰이프에서 생성 된 소스 코드 클래스에 특성을 추가 하는 데 사용 됩니다.|\<none>|
|Double 파생을 생성 합니다.|이면 `True` 재정의를 통한 사용자 지정을 지원 하기 위해 기본 클래스와 partial 클래스가 모두 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md) 을 참조 하세요.|False|
|사용자 지정 생성자 있음|이면 `True` 사용자 지정 생성자가 소스 코드에 제공 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|False|
|상속 한정자|포트 ( `none` , 또는)에서 생성 되는 소스 코드 클래스의 상속 종류에 대해 설명 `abstract` 합니다 `sealed` .|없음|
|기본 포트|이 도형의 기본 클래스입니다.|(없음)|
|Name|이 셰이프의 이름입니다.|현재 이름|
|네임스페이스|이 모양과 관련 된 네임 스페이스입니다.|현재 네임 스페이스|
|도구 설명 유형|도구 설명을 정의 하는 방법 (고정, 변수 또는 없음)입니다. 고정 된 경우 `Fixed Tooltip Text` 속성 값이 도구 설명으로 사용 되 고, 변수 이면 도구 설명이 사용자 지정 코드에 정의 됩니다.|없음|
|참고|이 셰이프와 연결 된 비공식 메모입니다.|\<none>|
|초기 높이|이 도형의 초기 높이 (인치)입니다.|1|
|초기 너비|이 도형의 초기 너비 (인치)입니다.|1.5|
|속성으로 노출 된 채우기 색<br /><br /> 노출 된 채우기 그라데이션 모드<br /><br /> 제공 된 윤곽선 색을 속성으로 표시<br /><br /> 노출 된 윤곽선 대시 스타일을 속성으로<br /><br /> 개요 두께를 속성으로 노출<br /><br /> 텍스트 색을 노출 합니다.|이면 `True` 사용자가 셰이프의 설명 된 속성을 설정할 수 있습니다. 이를 설정 하려면 셰이프 정의를 마우스 오른쪽 단추로 클릭 하 고 **노출 추가**를 클릭 합니다.|False|
|설명|생성 된 디자이너를 문서화 하는 데 사용 됩니다.|\<none>|
|표시 이름|이 셰이프에 대해 생성 된 디자이너에 표시 되는 이름입니다.|\<none>|
|고정 도구 설명 텍스트|고정 도구 설명에 사용 되는 텍스트입니다.|\<none>|
|Help Keyword|이 모양에 대 한 F1 도움말을 인덱싱하는 데 사용 되는 키워드입니다.|\<none>|

## <a name="see-also"></a>관련 항목
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

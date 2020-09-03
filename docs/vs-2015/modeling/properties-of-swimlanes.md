---
title: 스윔 레인의 속성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b76bef291e23bc570534aa79f9471453c59491c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671335"
---
# <a name="properties-of-swimlanes"></a>스윔 레인의 속성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

스윔 레인을 다이어그램에 추가할 수 있습니다. 스윔 레인 다이어그램을 세로 또는 가로 영역으로 나눕니다. 스윔 레인 내에 표시 될 다른 셰이프를 정의할 수 있습니다. 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

 스윔 레인에는 다음 표에 나열 된 속성이 있습니다.

|속성|설명|기본값|
|--------------|-----------------|-------------|
|본문 채우기 색|스윔 레인 본문의 채우기 색입니다.|흰색|
|머리글 채우기 색|스윔 레인의 머리글에 대 한 채우기 색입니다.|진한 회색|
|구분 기호 색|구분선의 색입니다.|LightGray|
|구분선 스타일|구분선의 스타일입니다 ( `Solid` , `Dash` ,,, `Dot` `DashDot` `DashDotDot` 또는 `Custom` ).|`Dash`|
|구분 기호 두께|구분선의 두께 (인치)입니다.|0.03125|
|텍스트 색|이 스윔 레인에 연결 된 텍스트 데코레이터에 사용 되는 색입니다.|검정|
|액세스 한정자|클래스의 액세스 수준 ( `public` 또는 `internal` )입니다.|공용|
|사용자 지정 특성|이 스윔 레인에서 생성 된 코드 클래스에 특성을 추가 하는 데 사용 됩니다.|\<none>|
|Double 파생을 생성 합니다.|이면 `True` 재정의를 통한 사용자 지정을 지원 하기 위해 기본 클래스와 partial 클래스가 모두 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|False|
|사용자 지정 생성자 있음|이면 `True` 사용자 지정 생성자가 소스 코드에 제공 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|False|
|상속 한정자|스윔 레인 ( `none` , 또는)에서 생성 되는 소스 코드 클래스의 상속 종류에 대해 설명 합니다 `abstract` `sealed` .|없음|
|기본 스윔 레인|이 스윔 레인의 기본 클래스입니다.|(없음)|
|Name|이 스윔 레인의 이름입니다.|현재 이름|
|네임스페이스|이 스윔 레인에 관련 된 네임 스페이스입니다.|현재 네임 스페이스|
|도구 설명 형식|도구 설명을 정의 하는 방법 ( `fixed` , `variable` 또는 `none` )입니다. 이면 `fixed` 속성의 값이 `Fixed Tooltip Text` 사용 되 고 `variable` , 이면 도구 설명이 사용자 지정 코드에 정의 됩니다.|\<none>|
|참고|이 스윔 레인과 관련 된 비공식 메모입니다.|\<none>|
|맞춤|가로 또는 세로 맞춤입니다.|Vertical|
|초기 높이|이 스윔 레인의 초기 높이 (인치)입니다. 가로 스윔 레인에만 적용할 수 있습니다.|0|
|초기 너비|이 스윔 레인의 초기 너비 (인치)입니다. 세로 스윔 레인에만 적용할 수 있습니다.|0|
|텍스트 색을 노출 합니다.|인 경우 `True` 사용자는 생성 된 디자이너에서 스윔 레인의 색을 설정할 수 있습니다. 이를 설정 하려면 스윔 레인 셰이프를 마우스 오른쪽 단추로 클릭 하 고 **노출 추가**를 클릭 합니다.|False|
|설명|생성 된 디자이너를 문서화 하는 데 사용 됩니다.|\<none>|
|표시 이름|이 스윔 레인 클래스를 참조 하기 위해 생성 된 디자이너에 표시 되는 이름입니다.|\<none>|
|고정 도구 설명 텍스트|고정 도구 설명에 사용 되는 텍스트입니다.|\<none>|
|Help Keyword|이 스윔 레인에 대 한 F1 도움말을 인덱싱하는 데 사용 되는 키워드입니다.|\<none>|

## <a name="see-also"></a>관련 항목
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)

---
title: 이미지 모양의 속성
description: 이미지 셰이프 및 이미지 셰이프를 사용하여 도메인 클래스가 생성된 디자이너에 표시되는 방식을 지정하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.selectimagedialog
- vs.dsltools.dsldesigner.imageshape
helpviewer_keywords:
- Domain-Specific Language, image shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98198b1197de6f5fda6a05a5bae58378a323f718
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390557"
---
# <a name="properties-of-image-shapes"></a>이미지 모양의 속성

이미지 셰이프를 사용하여 도메인 클래스가 생성된 디자이너에 표시되는 방식을 지정할 수 있습니다. `Image`클래스의 속성을 미리 정의된 이미지 파일로 설정하여 이미지 셰이프를 정의합니다. 다음 형식이 지원됩니다.

- .gif

- .jpg

- .jpeg

- .bmp

- .wmf

- .emf

- .png

기본적으로 이미지 파일과 같은 디자이너 리소스 파일은 **Dsl** 프로젝트의 **Resources** 폴더에 있습니다.

자세한 내용은 [Domain-Specific 언어를 정의하는 방법을 참조하세요.](../modeling/how-to-define-a-domain-specific-language.md) 이러한 속성을 사용하는 방법에 대한 자세한 내용은 [Domain-Specific 언어 사용자 지정 및 확장을 참조하세요.](../modeling/customizing-and-extending-a-domain-specific-language.md)

이미지 셰이프에는 다음 표에 나열된 속성이 있습니다.

|속성|설명|기본값|
|-|-|-|
|채우기 색|이 도형의 채우기 색입니다.|흰색|
|채우기 그라데이션 모드|이 도형의 채우기 그라데이션 모드입니다.|수평적 크기 조정|
|기본 연결 지점이 있습니다.|이면 `True` 셰이프가 생성된 디자이너에서 위쪽, 아래쪽, 왼쪽 및 오른쪽 연결점을 사용합니다.|거짓|
|윤곽선 색|이 도형의 윤곽선 색입니다.|검정|
|윤곽선 대시 스타일|이 모양의 윤곽선 대시 스타일(Solid, Dash, Dot, DashDot, DashDotDot 또는 Custom)입니다.|단색|
|윤곽선 두께|이 도형의 윤곽선 두께입니다.|0.03125|
|텍스트 색|이 모양과 연결된 텍스트 데코레이터에 사용되는 색입니다.|검정|
|액세스 한정자|기하 도형(public 또는 internal)의 액세스 한정자입니다.|공용|
|사용자 지정 특성|이 셰이프에서 생성된 소스 코드 클래스에 특성을 추가하는 데 사용됩니다.|\<none>|
|Double 파생 생성|이면 `True` 재정의를 통한 사용자 지정을 지원하기 위해 기본 클래스와 partial 클래스가 모두 생성됩니다. 자세한 내용은 [재정의 및 생성된 클래스 확장을 참조하세요.](../modeling/overriding-and-extending-the-generated-classes.md)|거짓|
|사용자 지정 생성자가 있습니다.|이면 `True` 소스 코드에 사용자 지정 생성자가 제공됩니다. 자세한 내용은 [재정의 및 생성된 클래스 확장을 참조하세요.](../modeling/overriding-and-extending-the-generated-classes.md)|거짓|
|상속 한정자|이미지 셰이프( , 또는 )에서 생성된 소스 코드 클래스의 상속 종류를 `none` `abstract` `sealed` 설명합니다.|없음|
|기본 이미지 셰이프|이 셰이프의 기본 클래스입니다.|(없음)|
|속성|이 셰이프의 이름입니다.|현재 이름|
|네임스페이스|이 셰이프와 관련된 네임스페이스입니다.|현재 네임스페이스|
|도구 설명 형식|도구 설명이 정의된 위치(고정, 변수 또는 없음)입니다. 고정된 경우 `Fixed Tooltip Text` 속성 값이 도구 설명으로 사용됩니다. 변수이면 도구 설명이 사용자 지정 코드에 정의됩니다.|없음|
|참고|이 셰이프와 관련된 비공식 메모입니다.|\<none>|
|초기 높이|이 셰이프의 초기 높이(인치)입니다.|1|
|초기 너비|이 셰이프의 초기 너비(인치)입니다.|1.5|
|속성으로 노출된 채우기 색<br /><br /> 노출된 채우기 그라데이션 모드<br /><br /> 노출되는 윤곽선 색을 속성으로<br /><br /> 윤곽선 대시 스타일을 속성으로 노출<br /><br /> 노출되는 윤곽선 두께를 속성으로<br /><br /> 텍스트 색 노출|이면 `True` 사용자가 도형의 명시된 속성을 설정할 수 있습니다. 이를 설정하려면 도형 정의를 마우스 오른쪽 단추로 클릭하고 **노출된 추가를** 클릭합니다.|거짓|
|설명|생성된 디자이너를 문서화하는 데 사용됩니다.|\<none>|
|표시 이름|이 셰이프에 대해 생성된 디자이너에 표시할 이름입니다.|\<none>|
|고정 도구 설명 텍스트|고정 도구 설명에 사용되는 텍스트입니다.|\<none>|
|Help Keyword|이 요소에 대한 F1 도움말을 인덱싱하는 데 사용되는 키워드입니다.|\<none>|
|이미지|이 셰이프에 사용되는 이미지 파일의 경로입니다.|\<none>|

## <a name="see-also"></a>참조

- [도메인 특정 언어 도구 용어집](/previous-versions/bb126564(v=vs.100))
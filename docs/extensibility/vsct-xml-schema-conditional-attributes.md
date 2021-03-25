---
title: VSCT XML 스키마 조건부 특성 | Microsoft Docs
description: VSCT XML 스키마 목록 및 항목에 조건부 특성을 적용 하는 방법에 대해 알아봅니다. 특성은 결과 출력을 제어 하는 true 또는 false로 평가 됩니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bc1bcb9d80474b467e90de6262e797087589065
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062358"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 스키마 조건부 특성
모든 목록 및 항목에 조건부 특성을 적용할 수 있습니다. 논리 연산자 및 기호 확장 식은 true 또는 false로 계산 됩니다. True 이면 연결 된 목록 또는 항목이 결과 출력에 포함 됩니다.

 다른 토큰 확장 또는 상수에 대해 토큰 확장을 테스트할 수 있습니다. 함수는 `Defined()` 값이 없는 경우에도 특정 이름이 정의 되었는지 여부를 테스트 합니다.

 조건 특성이 목록에 적용 되 면 해당 조건이 목록의 모든 자식 요소에 적용 됩니다. 자식 요소 자체에 조건 특성이 포함 된 경우 해당 조건이 AND 연산에 의해 부모 식과 결합 됩니다.

 값 1, ' 1 ' 및 ' t r u e '는 true로 평가 되 고 0, ' 0 ' 및 ' f a l s e '는 false로 평가 됩니다.

## <a name="operators"></a>연산자
 다음 연산자를 사용 하 여 조건식을 계산할 수 있습니다.

|연산자|정의|
|--------------|----------------|
|(,)|Grouping(그룹화)|
|!|논리 NOT|
|\<, >, \<=, >=, ==, !=|관계형 및 같음|
|및|부울|
|또는|부울|

## <a name="examples"></a>예

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 명령 테이블 (. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

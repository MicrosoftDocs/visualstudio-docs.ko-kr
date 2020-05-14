---
title: VSCT XML 스키마 조건부 특성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697942"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 스키마 조건부 특성
모든 목록 및 항목에 조건부 특성을 적용할 수 있습니다. 논리 연산자 및 기호 확장 식은 true 또는 false로 평가합니다. true이면 연관된 목록 또는 항목이 결과 출력에 포함됩니다.

 다른 토큰 확장 또는 상수에 대해 토큰 확장을 테스트할 수 있습니다. 함수는 `Defined()` 값이 없는 경우에도 특정 이름이 정의되었는지 여부를 테스트합니다.

 조건 특성이 목록에 적용되면 조건은 목록의 모든 자식 요소에 적용됩니다. 자식 요소 자체에 조건 특성이 포함되어 있으면 해당 조건은 AND 연산에 의해 상위 식과 결합됩니다.

 값 1, '1' 및 'true'는 true로 평가되고 0, '0' 및 'false'는 false로 평가됩니다.

## <a name="operators"></a>연산자
 다음 연산자를 사용하여 조건식을 평가합니다.

|연산자|정의|
|--------------|----------------|
|(,)|Grouping(그룹화)|
|!|논리 NOT|
|\<, >, \<=, >=, ==, !=|관계형 및 같음|
|and|부울|
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

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블(. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

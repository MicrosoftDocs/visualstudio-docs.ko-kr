---
title: 요소 정의 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc09de1d822f41b25397c7a56c7cce4449a9e551
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712264"
---
# <a name="define-element"></a>요소 정의
기호 이름과 값 쌍을 정의합니다. 이 기호는 조건부 특성으로 평가할 수 있습니다. 자세한 내용은 [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오. [기호 요소도](../extensibility/symbols-element.md)참조하십시오.

## <a name="syntax"></a>구문

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|name|필수 사항입니다. 기호의 이름:<br /><br /> 이름="모드"|
|값|필수 사항입니다. 기호의 값:<br /><br /> 값="표준"|
|조건|(선택 사항) 자세한 내용은 [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 테이블 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE(통합 개발 환경)에 제공하는 명령을 나타내는 모든 요소를 정의합니다. 예를 들어 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자를 예로 들 수 있습니다.|

## <a name="example"></a>예제

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

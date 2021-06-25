---
title: Define 요소 | Microsoft Docs
description: Define 요소는 기호 이름 및 값 쌍을 정의 합니다. 이 기호는 조건부 특성으로 평가할 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 409621410db727f933e41bae894f125dc877b4c2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898047"
---
# <a name="define-element"></a>Define 요소
기호 이름 및 값 쌍을 정의 합니다. 이 기호는 조건부 특성으로 평가할 수 있습니다. 자세한 내용은 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요. 또한 [기호 요소](../extensibility/symbols-element.md)를 참조 하세요.

## <a name="syntax"></a>구문

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|name|필수 요소. 기호의 이름입니다.<br /><br /> name = "모드"|
|value|필수 요소. 기호의 값입니다.<br /><br /> value = "Standard"|
|조건|선택 사항입니다. 자세한 내용은 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE (통합 개발 환경)에 제공 하는 명령을 나타내는 모든 요소를 정의 합니다. 예를 들어 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자가 있습니다.|

## <a name="example"></a>예제

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

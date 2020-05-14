---
title: 요소 포함 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ea89185d28be2816a690d867dbb3eccbb739e04
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710354"
---
# <a name="include-element"></a>요소 포함
포함 요소는 현재 파일에 삽입하기 위해 제공된 포함 경로에 위치할 수 있는 파일을 지정합니다.  정의된 모든 기호 및 형식은 컴파일된 결과의 일부가 됩니다.

## <a name="syntax"></a>구문

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|href|필수 사항입니다. 헤더 파일에 대한 경로:<br /><br /> href="stdidcmd.h"|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 테이블 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE에 제공하는 명령(즉, 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자)을 나타내는 모든 요소를 정의합니다.|

## <a name="example"></a>예제

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

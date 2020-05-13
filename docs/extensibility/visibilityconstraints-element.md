---
title: 가시성 제약 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1aaa9573b883910ac6fa5d921a9bc79ce1c1cf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698185"
---
# <a name="visibilityconstraints-element"></a>가시성 제약 요소
가시성제약 요소는 명령 및 도구 모음 그룹의 정적 가시성을 결정합니다. VSPackage를 로드하지 않고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE(통합 개발 환경)에 의해 먼저 가시성이 제어됩니다.

## <a name="syntax"></a>구문

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[가시성항목 요소](../extensibility/visibilityitem-element.md)|명령 및 도구 모음의 정적 가시성을 결정합니다.|
|[가시성 제약 조건](../extensibility/visibilityconstraints-element.md)|명령 및 도구 모음 그룹의 정적 가시성을 결정합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 테이블 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE에 제공하는 명령(예: 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자)을 나타내는 모든 요소를 정의합니다.|

## <a name="example"></a>예제

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>참조
- [가시성항목 요소](../extensibility/visibilityitem-element.md)
- [비주얼 스튜디오 명령 테이블(. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

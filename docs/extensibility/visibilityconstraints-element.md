---
title: VisibilityConstraints 요소 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698185"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints 요소
VisibilityConstraints 요소는 명령 및 도구 모음 그룹의 정적 표시 여부를 결정 합니다. 표시 유형은 먼저 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage를 로드 하지 않고 IDE (통합 개발 환경)에 의해 제어 됩니다.

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

|특성|설명|
|---------------|-----------------|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[VisibilityItem 요소](../extensibility/visibilityitem-element.md)|명령 및 도구 모음의 정적 표시 여부를 결정 합니다.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|명령 및 도구 모음 그룹의 정적 표시 여부를 결정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE에 제공 하는 명령 (예: 메뉴 항목, 메뉴, 도구 모음, 콤보 상자)을 나타내는 요소를 모두 정의 합니다.|

## <a name="example"></a>예제

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>참고 항목
- [VisibilityItem 요소](../extensibility/visibilityitem-element.md)
- [Visual Studio 명령 테이블 (. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

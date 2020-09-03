---
title: Include 요소 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710354"
---
# <a name="include-element"></a>Include 요소
Include 요소는 현재 파일에 삽입 하기 위해 제공 된 포함 경로에 있을 수 있는 파일을 지정 합니다.  정의 된 모든 기호 및 형식은 컴파일된 결과의 일부가 됩니다.

## <a name="syntax"></a>구문

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|href|필수 요소. 헤더 파일에 대 한 경로입니다.<br /><br /> href = "stdidcmd"|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage IDE에 제공 하는 명령, 즉 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자를 나타내는 모든 요소를 정의 합니다.|

## <a name="example"></a>예제

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

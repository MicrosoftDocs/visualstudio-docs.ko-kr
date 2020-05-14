---
title: 커맨드 테이블 엘리먼트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a362763d34335b9a18c4114a7c35b23f0efee020
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739652"
---
# <a name="commandtable-element"></a>명령 테이블 요소
명령 테이블은 *.vsct* 파일의 루트 요소입니다. VSPackage가 IDE에 제공하는 명령의 실제 레이아웃과 유형을 정의하는 파일입니다. 명령에는 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자가 포함될 수 있습니다. 자세한 내용은 [Visual Studio 명령 테이블(.vsct) 파일을](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)참조하십시오.

## <a name="syntax"></a>구문

```xml
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >
  <Extern>... </Extern>
  <Include>... </Include>
  <Define>... </Define>
  <Commands>... </Commands>
  <CommandPlacements>... </CommandPlacements>
  <VisibilityConstraints>... </VisibilityConstraints>
  <KeyBindings>... </KeyBindings>
  <UsedCommands... </UsedCommands>
  <Symbols>... </Symbols>
</CommandTable>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

| attribute | 설명 |
|-----------| - |
| xmlns | 필수 사항입니다. XML 네임스페이스:<br /><br /> `xmlns=http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable`<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| 언어 | (선택 사항) 언어 특성을 사용하여 명령 테이블의 모든 \<String> 요소의 기본 언어를 지정할 수 있습니다.  언어를 지정하지 않으면 현재 프로세스의 언어가 사용됩니다.<br /><br /> 언어="en-us" |

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[외향적 요소](../extensibility/extern-element.md)|(선택 사항) 컴파일러에 대한 사전 처리자 지시문을 포함합니다.|
|[요소 포함](../extensibility/include-element.md)|(선택 사항) 컴파일에 포함할 모든 파일에 대한 경로를 포함합니다.|
|[요소 정의](../extensibility/define-element.md)|(선택 사항) 이름과 값이 지정된 기호를 정의합니다.|
|[명령 요소](../extensibility/commands-element.md)|(선택 사항) VSPackage에 대한 모든 명령을 정의하는 부모 요소는 다른 모든 요소를 포함합니다.|
|[명령 위치 요소](../extensibility/commandplacements-element.md)|(선택 사항) 명령 모음에서 명령을 배치할 위치를 정의합니다.|
|[가시성 제약 요소](../extensibility/visibilityconstraints-element.md)|(선택 사항) 명령 및 도구 모음의 정적 가시성을 결정합니다.|
|[키 바인딩 요소](../extensibility/keybindings-element.md)|(선택 사항) 명령에 대한 바로 가기 키 조합(있는 경우)을 지정합니다.|
|[중고 명령 요소](../extensibility/usedcommands-element.md)|(선택 사항) VSPackage가 다른 VSPackage에서 원래 지원하는 자체 버전의 기능을 선택적으로 구현할 수 있습니다.|
|[기호 요소](https://www.microsoft.com/download/details.aspx?id=55984)|(선택 사항) 컴파일러에 대한 GUID, 아이디 등과 같은 기호 데이터가 포함됩니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|None||

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

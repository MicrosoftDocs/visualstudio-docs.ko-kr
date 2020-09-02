---
title: Strings 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699726"
---
# <a name="strings-element"></a>Strings 요소
Strings 요소는 **Buttontext** 자식 요소를 하나 이상 포함 해야 합니다. 다른 모든 자식 요소는 선택 사항입니다. ' & ' 및 ' < '와 같은 잘못 된 XML 문자는 엔터티 (' &amp; ' 및 ' ' 등)로 코딩 되어야 합니다 &lt; .

 텍스트 문자열의 앰퍼샌드는 명령에 대 한 바로 가기 키를 지정 합니다.

## <a name="syntax"></a>구문

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|language|선택 사항입니다. Language = "."|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|ButtonText|이 필드 및 명령 정의에서 5 개의 다음 텍스트 필드를 사용 하 여 다양 한 메뉴에 표시 되는 텍스트를 지정할 수 있습니다. 기본적으로이 `ButtonText` 필드는 메뉴 컨트롤러에 표시 됩니다. `ButtonText`다른 텍스트 필드가 비어 있는 경우에도 필드가 기본값이 됩니다. `ButtonText`다른 텍스트 필드가 지정 된 경우에도 필드를 비워 둘 수 없습니다.|
|ToolTipText|`ToolTipText`필드는 메뉴 항목에 대 한 도구 설명에 표시 되는 텍스트를 지정 합니다.<br /><br /> `ToolTipText`필드가 비어 있으면 `ButtonText` 필드가 사용 됩니다.|
|확장|`MenuText`필드는 주 메뉴, 도구 모음, 바로 가기 메뉴 또는 하위 메뉴에 있는 명령에 대해 표시 되는 텍스트를 지정 합니다. `MenuText`필드가 비어 있으면 IDE (통합 개발 환경)에서 필드를 사용 합니다 `ButtonText` . 이 `MenuText` 필드는 지역화에도 사용할 수 있습니다.<br /><br /> 바로 가기 메뉴의 경우 `MenuText` 이 필드는 IDE에서 바로 가기 메뉴를 사용자 지정할 수 있도록 하는 바로 가기 메뉴 도구 모음에 표시 되는 이름입니다. 따라서 바로 가기 메뉴의 이름을 지정 해야 합니다. 예를 들어 "바로 가기" 대신 "위젯 패키지 바로 가기 메뉴"를 사용 합니다.<br /><br /> 필드를 `MenuText` 지정 하지 않으면 `ButtonText` 필드가 사용 됩니다.|
|CommandName|`CommandName`필드는 **도구** 메뉴에서 **사용자 지정** 을 클릭 하 여 사용할 수 있는 **사용자 지정** 대화 상자의 **명령** 탭에서 키보드 범주에 표시 되는 텍스트를 지정 합니다.|
|CanonicalName|영어 필드는 명령 `CanonicalName` 창에 입력 하 여 메뉴 항목을 실행 하는 데 사용할 수 **Command** 있는 명령 이름을 영어 텍스트로 지정 합니다. IDE는 문자, 숫자, 밑줄 또는 포함 된 마침표가 아닌 모든 문자를 제거 합니다. 그런 다음이 텍스트를 필드에 연결 `ButtonText` 하 여 명령을 정의 합니다. 예를 들어 **파일** 메뉴의 **새 프로젝트** 는 파일. newproject 명령이 됩니다.<br /><br /> 영어 필드를 `CanonicalName` 지정 하지 않으면 IDE는 필드를 사용 하 `ButtonText` 고 문자, 숫자, 밑줄 및 포함 된 마침표를 제외 하 고 모두 제거 합니다. 예를 들어 "&명령을 정의 하는" 단추 텍스트는 앰퍼샌드, 공백 및 줄임표가 제거 되는 DefineCommands가 됩니다.<br /><br /> `TextChanges`플래그가 지정 되 고 명령의 텍스트가 변경 된 경우 **명령** 창에서 인식 하는 해당 명령은 변경 되지 않으며 원래 `ButtonText` 또는 영어 필드의 정규 형식으로 유지 됩니다 `CanonicalName` .|
|LocCanonicalName|`LocCanonicalName`필드는 영어 필드와 동일 하 게 동작 `CanonicalName` 하지만 지역화 된 명령 텍스트를 지정할 수 있습니다. 두 정식 필드를 모두 지정할 수 있습니다. IDE는 **명령** 창에 입력 한 텍스트를 구문 분석 하 여 명령과 연결 하므로 영어와 영어가 아닌 텍스트를 모두 동일한 명령에 연결할 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Button 요소](../extensibility/button-element.md)|사용자가 조작할 수 있는 요소를 정의 합니다.|
|[Menu 요소](../extensibility/menu-element.md)|단일 메뉴 항목을 정의 합니다.|
|[Combo 요소](../extensibility/combo-element.md)|콤보 상자에 표시 되는 명령을 정의 합니다.|

## <a name="see-also"></a>추가 정보
- [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

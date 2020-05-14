---
title: VSCT XML 스키마 레퍼런스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697909"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML 스키마 참조
각각에 대해 허용된 자식 요소 및 특성이 있는 명령 테이블 컴파일러 스키마 요소 테이블을 제공합니다.

 XML 기반 명령 테이블 구성(.vsct) 파일은 VSPackage가 통합 개발 환경(IDE)에 제공하는 명령 요소를 정의합니다. 이러한 요소에는 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자가 포함됩니다.

> [!NOTE]
> VSCT 컴파일러는 .vsct 파일에서 사전 처리자를 실행할 수 있습니다. 일반적으로 C++ 전처리기이므로 C++ 파일에 사용되는 구문이 동일한 포함 및 매크로를 정의할 수 있습니다. 이 예제는 **새 프로젝트** 마법사가 VSPackage 프로젝트에 대해 만드는 .vsct 파일에 제공됩니다.

## <a name="optional-elements"></a>선택적 요소
 일부 VSCT 요소는 선택 사항입니다. `Parent` 인수를 지정하지 않으면 Group_Undefined:0 암시됩니다. `Icon` 인수를 지정하지 않으면 guidOfficeIcon:msotcidNoIcon이 암시됩니다. 바로 가기 키가 정의되면 일반적으로 사용되지 않는 에뮬레이션은 선택 사항입니다.

 `href` 비트맵 항목은 인수에서 비트맵 스트립의 위치를 지정하여 컴파일 타임에 포함될 수 있습니다. 비트맵 스트립은 DLL의 리소스에서 추출되지 않고 병합 중에 복사됩니다. 인수가 `href` 제공되면 인수는 `usedList` 선택 사항이 되고 비트맵 스트립의 모든 슬롯이 사용되는 것으로 간주됩니다.

 모든 GUID 및 ID 값은 기호 이름을 사용하여 정의해야 합니다. 이러한 이름은 헤더 파일 또는 VSCT \<기호> 섹션에 정의될 수 있습니다. 기호 이름은 로컬이거나 포함 \<> 요소를 통해 포함되거나 Extern> 요소에서 \<참조해야 합니다. 기호 이름은 \<#define SYMBOL 값의 간단한 패턴을 따르는 경우 Extern> 요소에 지정된 헤더 파일에서 가져옵니다. 해당 기호가 이전에 정의된 경우 값은 다른 기호일 수 있습니다. GUID 정의는 OLE 또는 C++ 형식을 따라야 합니다. ID 값은 다음과 같이 소수 자릿수 또는 0x 앞에 오는 육각형 숫자일 수 있습니다.

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 }

  XML 주석을 사용할 수 있지만 왕복 그래픽 사용자 인터페이스(GUI) 도구는 삭제할 수 있습니다. > 요소의 \<내용은 형식에 관계없이 유지 관리됩니다.

## <a name="schema-hierarchy"></a>스키마 계층 구조
 .vsct 파일에는 다음과 같은 주요 요소가 있습니다.

- [명령 테이블 요소](../extensibility/commandtable-element.md)

- [외향적 요소](../extensibility/extern-element.md)

- [요소 포함](../extensibility/include-element.md)

- [요소 정의](../extensibility/define-element.md)

- [명령 요소](../extensibility/commands-element.md)

- [명령 위치 요소](../extensibility/commandplacements-element.md)

- [가시성 제약 요소](../extensibility/visibilityconstraints-element.md)

- [키 바인딩 요소](../extensibility/keybindings-element.md)

- [중고 명령 요소](../extensibility/usedcommands-element.md)

- [부모 요소](../extensibility/parent-element.md)

- [아이콘 요소](../extensibility/icon-element.md)

- [문자열 요소](../extensibility/strings-element.md)

- [명령 플래그 요소](../extensibility/command-flag-element.md)

- [기호 요소](../extensibility/symbols-element.md)

- [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>참조
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VS패키지의 명령 라우팅](../extensibility/internals/command-routing-in-vspackages.md)

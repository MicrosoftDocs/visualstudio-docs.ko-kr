---
title: VSCT XML 스키마 참조 | Microsoft Docs
description: VSCT XML 스키마 참조 문서에서는 각 스키마에 허용되는 자식 요소와 특성이 있는 명령 테이블 컴파일러 스키마 요소에 대해 설명합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d82cda9c91642b094deea50eda02676f9bb73f3
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905230"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML 스키마 참조
각각에 대해 허용되는 자식 요소와 특성이 있는 Command Table Compiler 스키마 요소의 테이블을 제공합니다.

 XML 기반 명령 테이블 구성(.vsct) 파일은 VSPackage가 IDE(통합 개발 환경)에 제공하는 명령 요소를 정의합니다. 이러한 요소에는 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자가 포함됩니다.

> [!NOTE]
> VSCT 컴파일러는 .vsct 파일에서 전처리기를 실행할 수 있습니다. 일반적으로 C++ 전처리기이므로 C++ 파일에 사용되는 구문이 동일한 includes 및 매크로를 정의할 수 있습니다. 이에 대한 예제는 새 프로젝트 마법사가 VSPackage **프로젝트에** 대해 만드는 .vsct 파일에 제공됩니다.

## <a name="optional-elements"></a>선택적 요소
 일부 VSCT 요소는 선택 사항입니다. `Parent`인수를 지정하지 않으면 Group_Undefined:0 는 암시됩니다. `Icon`인수를 지정하지 않으면 guidOfficeIcon:msotcidNoIcon이 암시됩니다. 바로 가기 키가 정의되면 일반적으로 사용되지 않는 에뮬레이션은 선택 사항입니다.

 인수에서 비트맵 스트립의 위치를 지정하여 컴파일 시간에 비트맵 항목을 포함할 수 `href` 있습니다. 비트맵 스트립은 DLL의 리소스에서 추출되지 않고 병합 중에 복사됩니다. `href`인수가 제공되면 `usedList` 인수는 선택 사항이 되고 비트맵 스트립의 모든 슬롯이 사용되는 것으로 간주됩니다.

 모든 GUID 및 ID 값은 기호 이름을 사용하여 정의해야 합니다. 이러한 이름은 헤더 파일 또는 VSCT 섹션에서 정의할 수 \<Symbols> 있습니다. 기호 이름은 로컬이거나, 요소를 통해 \<Include> 포함되거나, 요소에서 참조되어야 \<Extern> 합니다. 기호 이름은 기호 값 #define 단순 패턴을 따르는 경우 요소에 지정된 헤더 파일에서 \<Extern> 가져옵니다. 값은 해당 기호가 이전에 정의된 한 다른 기호일 수 있습니다. GUID 정의는 OLE 또는 C++ 형식을 따라야 합니다. ID 값은 다음 줄과 같이 0x 앞에 오는 10진수 또는 16진수일 수 있습니다.

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  XML 주석을 사용할 수 있지만 라운드트립 GUI(그래픽 사용자 인터페이스) 도구에서 삭제할 수 있습니다. 요소의 내용은 \<Annotation> 형식에 관계없이 유지 관리됩니다.

## <a name="schema-hierarchy"></a>스키마 계층 구조
 .vsct 파일에는 다음과 같은 주요 요소가 있습니다.

- [CommandTable 요소](../extensibility/commandtable-element.md)

- [Extern 요소](../extensibility/extern-element.md)

- [Include 요소](../extensibility/include-element.md)

- [요소 정의](../extensibility/define-element.md)

- [Commands 요소](../extensibility/commands-element.md)

- [CommandPlacements 요소](../extensibility/commandplacements-element.md)

- [VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)

- [KeyBindings 요소](../extensibility/keybindings-element.md)

- [UsedCommands 요소](../extensibility/usedcommands-element.md)

- [부모 요소](../extensibility/parent-element.md)

- [Icon 요소](../extensibility/icon-element.md)

- [Strings 요소](../extensibility/strings-element.md)

- [Command Flag 요소](../extensibility/command-flag-element.md)

- [Symbols 요소](../extensibility/symbols-element.md)

- [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>참조
- [VSPackages에서 사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VSPackages의 명령 라우팅](../extensibility/internals/command-routing-in-vspackages.md)

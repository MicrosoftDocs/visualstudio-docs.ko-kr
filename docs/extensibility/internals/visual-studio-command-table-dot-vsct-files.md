---
title: 비주얼 스튜디오 명령 테이블(. Vsct) 파일 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704032"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio 명령 테이블(.Vsct) 파일
명령 테이블 구성 파일은 VSPackage에 포함된 명령 집합을 설명하는 텍스트 파일입니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령 테이블(VSCT) 컴파일러는 XML 기반 구성 파일(.vsct 파일)을 이진 명령 테이블 출력(.cto) 파일로 컴파일합니다. 결과 .cto 파일은 명령 테이블(CTC) 컴파일러를 사용하여 .ctc 구성 파일을 컴파일하여 만든 파일과 동일합니다. 그러나 XML 기반 .vsct 파일에는 XML 편집기 및 XML IntelliSense와 같은 몇 가지 장점이 있습니다.

 .vsct 파일의 구문 및 의미 체계에 대한 자세한 내용은 [XML 명령 테이블 디자인() Vsct) 파일](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>섹션 내용
 [XML 명령 테이블(.Vsct) 파일 디자인](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 .vsct 파일을 디자인하는 방법을 설명합니다.

 [방법: .Vsct 파일 만들기](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 .vsct 파일을 만드는 메서드를 비교합니다. 새 .vsct 파일을 수동으로 만드는 프로세스에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
 [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)

 명령 테이블 XML 구성 파일의 각 섹션에 대한 세부 정보를 제공합니다.

 [명령 테이블 구성(. Ctc) 파일은](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) 더 이상 사용되지 않은 .ctc 파일 형식에 대한 개요를 제공합니다.

 [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 명령 테이블 형식 사양을 설명합니다.

 [VSPackage의 리소스](../../extensibility/internals/resources-in-vspackages.md)

 관리되는 VSPackage에서 관리되는 리소스와 관리되지 않는 리소스를 사용하는 방법을 설명합니다.

 [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)

 메뉴, 도구 모음 및 명령 콤보 상자를 포함하는 UI를 만드는 방법을 설명합니다.

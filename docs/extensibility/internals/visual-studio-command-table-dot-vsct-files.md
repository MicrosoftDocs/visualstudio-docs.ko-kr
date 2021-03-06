---
title: Visual Studio 명령 테이블 (. Vsct) 파일 | Microsoft Docs
description: VSPackage에 포함 된 명령 집합을 설명 하는 텍스트 파일인 명령 테이블 구성 파일에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 305bf0e5463fd4e030f2ce3e9f7fa6eca99bfe20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085743"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio 명령 테이블(.Vsct) 파일
명령 테이블 구성 파일은 VSPackage에 포함 된 명령 집합을 설명 하는 텍스트 파일입니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]명령 테이블 (vsct) 컴파일러는 XML 기반 구성 파일 (.cvsct 파일)을 이진 명령 테이블 출력 (.cto) 파일로 컴파일합니다. 이러한 파일은 CTO (명령 테이블) 컴파일러를 사용 하 여 생성 하는 것과 동일 합니다. cto 구성 파일을 컴파일합니다. 그러나 xml 기반. vsct 파일에는 XML 편집기 및 XML IntelliSense와 같은 몇 가지 이점이 있습니다.

 . Vsct 파일의 구문 및 의미 체계에 대 한 자세한 내용은 [XML 명령 테이블 디자인 (을 참조 하세요. Vsct) 파일](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>섹션 내용
 [XML 명령 테이블(.Vsct) 파일 디자인](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 . Vsct 파일을 디자인 하는 방법을 설명 합니다.

 [방법: .Vsct 파일 만들기](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 . Vsct 파일을 만드는 방법을 비교 합니다. 새. vsct 파일을 수동으로 만드는 프로세스에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [VSCT XML 스키마 참조](../../extensibility/vsct-xml-schema-reference.md)

 명령 테이블 XML 구성 파일의 각 섹션에 대 한 세부 정보를 제공 합니다.

 [명령 테이블 구성 (. Ctc) 파일](/previous-versions/bb165153(v=vs.100)) 은 사용 되지 않는. ctc 파일 형식에 대 한 개요를 제공 합니다.

 [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 명령 테이블 형식 사양을 설명 합니다.

 [VSPackage의 리소스](../../extensibility/internals/resources-in-vspackages.md)

 관리 되는 Vspackage 관리 되는 리소스와 관리 되지 않는 리소스를 사용 하는 방법을 설명 합니다.

 [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)

 메뉴, 도구 모음 및 명령 콤보 상자를 포함하는 UI를 만드는 방법을 설명합니다.
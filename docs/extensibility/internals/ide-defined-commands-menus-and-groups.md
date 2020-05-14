---
title: IDE 정의 명령, 메뉴 및 그룹 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, environment-defined
- .vsct files, environment-defined constants
- command groups, environment-defined
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6557f49b019a6793698dabe852919ec2e9f28cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707724"
---
# <a name="ide-defined-commands-menus-and-groups"></a>IDE 정의 명령, 메뉴 및 그룹
많은 메뉴, 명령 및 명령 그룹은 이미 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에서 사용하도록 정의되어 있습니다. 이러한 명령은 확장 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]할 때 사용할 수도 있습니다.

## <a name="finding-environment-defined-commands"></a>환경 정의 명령 찾기
 환경 명령은 네 개의 .vsct 파일 집합에 정의됩니다.

- 공유CmdDef.vsct

- 공유CmdPlace.vsct

- 쉘CmdDef.vsct

- 쉘CmdPlace.vsct

  이 파일은 * \<Visual Studio SDK 설치 경로>* \VisualStudioIntegration\Common\Inc\\. 이러한 파일은 VSPackage의 명령 테이블 구성(.vsct) 파일에서 사용자 고유의 메뉴, 그룹 및 명령에 대한 컨테이너로 사용할 수 있는 메뉴 및 그룹의 정의 및 GUID를 제공합니다.

## <a name="in-this-section"></a>섹션 내용
- [Visual Studio 메뉴의 GUID 및 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)

 Visual Studio 메뉴 모음및 메뉴에 포함된 그룹의 GUID 및 ID 값을 제공합니다.

- [Visual Studio 도구 모음의 GUID 및 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)

 Visual Studio IDE 및 도구 모음에 포함된 그룹의 도구 모음의 GUID 및 ID 값을 제공합니다.

- [Visual Studio 명령의 GUID 및 ID](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)

 Visual Studio IDE에서 정의한 명령의 GUID 및 ID 값을 제공합니다.

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.Vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [프로젝트 시스템 확장을 위한 IDE 정의 명령](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
- [VSPackage에서 사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

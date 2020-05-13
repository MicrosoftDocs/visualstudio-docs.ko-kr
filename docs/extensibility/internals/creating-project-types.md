---
title: 프로젝트 유형 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709076"
---
# <a name="create-project-types"></a>프로젝트 유형 만들기
새 프로젝트 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 유형을 만들어 확장할 수 있습니다. 새 프로젝트 유형을 만들려면 여러 개념을 이해하고 여러 단계를 완료해야 합니다. 다음 항목에서는 프로젝트 유형을 만드는 방법에 대한 개요를 제공합니다.

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 유형 설계 결정](../../extensibility/internals/project-type-design-decisions.md)

 새 프로젝트 유형을 만들기 전에 해야 하는 항목, 프로젝트 파일 지속성 및 약속 역학 설계 결정에 대해 설명합니다.

- [검사 목록: 새 프로젝트 유형 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)

 코드 편집 및 편집, 빌드, 디버깅 및 프로젝트에서 응용 프로그램 배포와 같은 프로그래밍 작업을 지원하는 새 프로젝트 형식을 만들기 위해 따라야 하는 단계에 대한 개요를 제공합니다.

- [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 생성](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 프로젝트 팩터리를 제공하고 사용하여 새 프로젝트의 인스턴스를 만드는 방법에 대한 정보를 제공합니다.

- [프로젝트 유형 등록](../../extensibility/internals/registering-a-project-type.md)

 기본 경로 및 데이터를 제공하는 레지스트리의 명령문 코드 샘플과 각 명령문에 대한 레지스트리 스크립트의 항목을 포함하는 테이블을 제공합니다.

- [프로젝트 지속성](../../extensibility/internals/project-persistence.md)

 파일 및 비파일 기반 프로젝트 개체를 유지 하는 데 사용 `IPersistFileFormat` 하는 방법에 대해 설명 합니다.

- [MSBuild 사용](../../extensibility/internals/using-msbuild.md)

 프로젝트 유형이 [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] 빌드 엔진을 사용하여 사용자가 명령줄에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 빌드할 수 있도록 하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
- [심볼 브라우징 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 **개체 브라우저** 및 **클래스 보기** 창과 같은 코드 보기 도구의 아키텍처에 대해 설명합니다. VSPackage에서 개체 탐색을 구현하는 데 사용되는 인터페이스와 메서드에 대해 설명합니다.

- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)

 프로젝트 항목이 열릴 때 사용되는 편집기와 프로젝트 리소스를 조작할 수 있는 방법을 결정하는 데 프로젝트가 미치는 중요성에 대해 설명합니다.

- [윈도우 설치 관리자와 VS패키지 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 VSPackage에 고유한 ID를 지정하는 방법과 WINDOWS 설치 관리자 패키지에서 VSPackage DLL 및 기타 정보를 래핑하는 방법을 보여*줍니다. MSI* 파일)을 통해 고객에게 배포할 수 있습니다.

- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)

 보기 및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 계층 구조를 해결하는 방법을 설명합니다.

- [VSPackage](../../extensibility/internals/vspackages.md)

 환경을 확장하고 사용자 고유의 VSPackage를 구현하는 방법에 대해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 설명하는 설치 가능한 COM 개체인 VSPackage에 대한 개요를 제공합니다.

- [프로젝트 형식](../../extensibility/internals/project-types.md)

 프로젝트를 사용하여 코드를 수정하고, 코드를 컴파일 및 빌드하고, 코드를 실행하고 디버그하는 방법에 대해 설명하고 프로젝트 형식을 만드는 방법에 대한 자세한 항목에 대한 링크를 제공합니다.

---
title: 프로젝트 형식 만들기 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709076"
---
# <a name="create-project-types"></a>프로젝트 형식 만들기
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]새 프로젝트 형식을 만들어를 확장할 수 있습니다. 새 프로젝트 형식을 만들려면 몇 가지 개념을 이해 하 고 여러 단계를 완료 해야 합니다. 다음 항목에서는 프로젝트 형식을 만드는 방법에 대 한 개요를 제공 합니다.

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 형식 디자인 결정](../../extensibility/internals/project-type-design-decisions.md)

 새 프로젝트 형식을 만들기 전에 수행 해야 하는 항목, 프로젝트 파일 지 속성 및 약정 정비공 디자인 결정에 대해 설명 합니다.

- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)

 코드를 편집 하 고 프로젝트에서 응용 프로그램을 컴파일, 빌드, 디버깅 및 배포 하는 등의 프로그래밍 작업을 지 원하는 새 프로젝트 형식을 만들기 위해 수행 해야 하는 단계에 대 한 개요를 제공 합니다.

- [프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 프로젝트 팩터리를 제공 하 고 사용 하 여 새 프로젝트의 인스턴스를 만드는 방법에 대 한 정보를 제공 합니다.

- [프로젝트 형식 등록](../../extensibility/internals/registering-a-project-type.md)

 기본 경로와 데이터를 제공 하는 레지스트리의 문과 각 문에 대 한 레지스트리 스크립트의 항목이 포함 된 테이블에 대 한 코드 샘플을 제공 합니다.

- [프로젝트 지 속성](../../extensibility/internals/project-persistence.md)

 를 사용 하 여 `IPersistFileFormat` 파일 및 파일 기반이 아닌 프로젝트 개체를 모두 유지 하는 방법을 설명 합니다.

- [MSBuild 사용](../../extensibility/internals/using-msbuild.md)

 프로젝트 형식에서 빌드 엔진을 사용 하 여 [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] 사용자가 명령줄에서 빌드하는 방법을 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="related-sections"></a>관련 단원
- [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 **개체 브라우저** 및 **클래스 뷰** 창과 같은 코드 보기 도구의 아키텍처에 대해 설명 합니다. VSPackage에서 개체 검색을 구현 하는 데 사용 되는 인터페이스 및 메서드에 대해 설명 합니다.

- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)

 프로젝트에서 프로젝트 항목을 열 때 사용 되는 편집기를 확인 하 고 프로젝트 리소스를 조작할 수 있는 방법을 설명 합니다.

- [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 VSPackage에 고유한 id를 제공 하는 방법 및 VSPackage Dll 및 기타 정보를 Windows Installer 패키지 ()에 래핑하는 방법을 보여 줍니다 *. MSI* 파일)을 배포 합니다.

- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]보기 및 주소 계층 구조를 설명 합니다.

- [VSPackages](../../extensibility/internals/vspackages.md)

 환경을 확장 하 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 고 고유한 VSPackage를 구현 하는 방법에 대해 설명 하는 설치 가능한 COM 개체인 VSPackage의 개요를 제공 합니다.

- [프로젝트 형식](../../extensibility/internals/project-types.md)

 프로젝트를 사용 하 여 코드를 수정 하 고, 코드를 컴파일 및 빌드하고, 코드를 디버그 하 고, 프로젝트 형식을 만드는 방법에 대 한 자세한 항목의 링크를 제공 하는 방법을 설명 합니다.

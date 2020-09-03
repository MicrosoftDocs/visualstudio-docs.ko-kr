---
title: 프로젝트 하위 유형 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c528486db99ddf07b2a2d1e18dcee4fc46e8713b
ms.sourcegitcommit: a3edc753c951f317b67ce294cd2fc74f0c45390c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89426978"
---
# <a name="project-subtypes"></a>프로젝트 하위 형식
프로젝트 하위 유형을 사용 하면의 프로젝트 시스템 동작을 사용자 지정 하거나 버전을 지정할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 사용자 지정은 프로젝트 파일에 추가 데이터를 저장 하 고, **새 항목 추가** 대화 상자에서 항목을 추가 또는 필터링 하 고, 어셈블리를 디버그 및 배포 하는 방법을 제어 하 고, 프로젝트 **속성 페이지** 대화 상자를 확장 합니다. Vspackage COM 집계를 사용 하 여 프로젝트 하위 유형을 구현 합니다.

> [!NOTE]
> Visual C++ 프로젝트 시스템은 프로젝트 하위 유형을 지원 하지 않습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 자체는 프로젝트 하위 유형을 사용 하 여 SQL Server 및 스마트 장치 프로젝트를 구현 합니다.

## <a name="in-this-section"></a>섹션 내용

- [프로젝트 하위 형식 디자인](../../extensibility/internals/project-subtypes-design.md)

  프로젝트 하위 형식의 개념을 설명 합니다.

- [프로젝트 하위 형식의 초기화 시퀀스](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  환경 별로 프로그래밍 방식의 프로젝트 하위 형식 초기화 시퀀스를 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [프로젝트 하위 형식에 의해 확장된 속성 및 메서드](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  프로젝트 하위 유형을 사용 하 여 가장 자주 확장 된 기능 및 메서드에 대해 자세히 설명 합니다.

- [MSBuild 프로젝트 파일의 데이터 유지](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  프로젝트 파일에 데이터를 저장 하는 방법과를 사용 하 여 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 하위 형식 집계 수준에서 프로젝트 파일의 데이터를 유지 관리 하는 방법을 설명 합니다.

- [프로젝트 속성 사용자 인터페이스](../../extensibility/internals/project-property-user-interface.md)

  프로젝트 하위 유형이 프로젝트 **속성 페이지** 대화 상자를 수정 하는 방법을 설명 합니다.

- [기본 프로젝트의 개체 모델 확장](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  프로젝트 하위 형식이 Automation Extender를 사용 하 여 자동화 개체 모델을 확장 하는 방법에 대 한 정보를 제공 합니다.

- [새 항목 추가 대화 상자에 적용](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  **새 항목 추가** 대화 상자에 항목을 추가 하는 방법에 대해 설명 합니다.

- [프로젝트 파일에 데이터 저장](../../extensibility/saving-data-in-project-files.md)

  프로젝트 하위 유형이 MPF (관리 패키지 프레임 워크)를 사용 하 여 프로젝트 파일에서 하위 형식 관련 데이터를 저장 하 고 검색 하는 방법을 설명 합니다.

- [특수 배포 처리](../../extensibility/internals/handling-specialized-deployment.md)

  인터페이스를 구현 하 여 프로젝트 하위 유형이 특수 배포 동작을 제공 하는 방법을 설명 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> .

- [속성 페이지 추가 및 제거](../../extensibility/adding-and-removing-property-pages.md)

  프로젝트 디자이너에서 속성 페이지를 추가 및 제거 하는 방법을 설명 합니다.

## <a name="related-sections"></a>관련 섹션

- [프로젝트 형식](../../extensibility/internals/project-types.md):

  프로젝트를 자세히 설명 하는 항목에 대 한 링크를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다.

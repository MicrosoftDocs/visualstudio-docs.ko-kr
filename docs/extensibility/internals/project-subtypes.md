---
title: 프로젝트 하위 형식 | Microsoft Docs
description: 프로젝트 하위 형식을 통해 Visual Studio 프로젝트 시스템의 동작을 사용자 지정하는 방법을 알아봅니다. VSPackages는 COM 집계를 사용하여 프로젝트 하위 형식을 구현합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cd0f959d300fdc797d9e42d581a163b8b0892591
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903582"
---
# <a name="project-subtypes"></a>프로젝트 하위 형식
프로젝트 하위 형식을 사용하면 의 프로젝트 시스템 동작을 사용자 지정하거나 지정할 수 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다. 사용자 지정에는 프로젝트 파일에 추가 데이터 저장, **새 항목 추가** 대화 상자에서 항목 추가 또는 필터링, 어셈블리 디버그 및 배포 방법 제어, 프로젝트 속성 **페이지** 대화 상자 확장 등이 포함됩니다. VSPackages는 COM 집계를 사용하여 프로젝트 하위 형식을 구현합니다.

> [!NOTE]
> Visual C++ 프로젝트 시스템은 프로젝트 하위 형식을 지원하지 않습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 자체에서는 프로젝트 하위 형식을 사용하여 SQL Server 및 스마트 디바이스 프로젝트를 구현합니다.

## <a name="in-this-section"></a>섹션 내용

- [프로젝트 하위 형식 디자인](../../extensibility/internals/project-subtypes-design.md)

  프로젝트 하위 형식의 개념을 설명합니다.

- [프로젝트 하위 형식의 초기화 시퀀스](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)

  환경별 프로그래밍 방식 프로젝트 하위 형식 초기화 시퀀스에 대해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 설명합니다.

- [프로젝트 하위 형식에 의해 확장된 속성 및 메서드](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

  프로젝트 하위 형식을 사용하여 가장 자주 확장되는 기능 및 메서드에 대한 자세한 설명을 제공합니다.

- [MSBuild 프로젝트 파일의 데이터 유지](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

  프로젝트 파일에 데이터를 유지하는 방법 및 를 사용하여 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 하위 형식 집계 수준에서 프로젝트 파일의 데이터를 유지 관리하는 방법을 설명합니다.

- [프로젝트 속성 사용자 인터페이스](../../extensibility/internals/project-property-user-interface.md)

  프로젝트 하위 유형이 프로젝트 속성 **페이지** 대화 상자를 수정하는 방법을 설명합니다.

- [기본 프로젝트의 개체 모델 확장](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)

  프로젝트 하위 유형에서 Automation Extenders를 사용하여 자동화 개체 모델을 확장하는 방법에 대한 정보를 제공합니다.

- [새 항목 추가 대화 상자에 적용](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)

  새 항목 추가 대화 상자에 항목을 **추가하는** 방법을 설명합니다.

- [프로젝트 파일에 데이터 저장](../../extensibility/saving-data-in-project-files.md)

  프로젝트 하위 형식이 MPF(Managed Package Framework)를 사용하여 프로젝트 파일에서 하위 형식별 데이터를 저장하고 검색하는 방법을 설명합니다.

- [특수 배포 처리](../../extensibility/internals/handling-specialized-deployment.md)

  프로젝트 하위 형식이 인터페이스를 구현하여 특수 배포 동작을 제공하는 방법을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 설명합니다.

- [속성 페이지 추가 및 제거](../../extensibility/adding-and-removing-property-pages.md)

  프로젝트 디자이너에서 속성 페이지 추가 및 제거에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원

- [프로젝트 형식](../../extensibility/internals/project-types.md):

  프로젝트에 대해 자세히 설명하는 항목에 대한 링크를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제공합니다.

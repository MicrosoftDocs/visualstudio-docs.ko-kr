---
title: 소스 제어 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704724"
---
# <a name="supporting-source-control"></a>소스 제어 지원
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]는 프로젝트 또는 편집기의 파일 체크 아웃, 체크 인 및 기타 소스 제어 작업을 지원합니다. 소스 제어 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 클라이언트는 동적으로 정의된 파일 집합에 대한 [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]보관, 버전 관리 및 제어 시설을 제공하는 와 같은 소스 제어 패키지와 상호 작용하도록 설계되었습니다.

## <a name="in-this-section"></a>섹션 내용
- [소스 제어 패키지 모델](../../extensibility/internals/model-for-source-control-packages.md)

 프로젝트 유형이 소스 제어를 지원하기 위해 구현해야 하는 인터페이스에 대해 설명합니다.

- [디자인 결정](../../extensibility/internals/source-control-design-decisions.md)

 프로젝트 유형을 구현하는 방법을 변경하는 답변을 제공하는 질문을 제공합니다.

- [구성 세부 정보](../../extensibility/internals/source-control-configuration-details.md)

 지원 소스 제어가 프로젝트 유형의 구현을 변경하는 방법을 설명합니다.

- [프로젝트 및 편집기에 대한 추가 지침](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 프로젝트 유형 및 편집자에 대한 모범 사례에 대해 설명합니다.

- [런타임 세부 정보](../../extensibility/internals/source-control-runtime-details.md)

 사용자가 프로젝트를 소스 제어 시스템에 추가할 때 프로젝트를 등록하는 방법을 설명합니다.

## <a name="reference"></a>참조
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>파일이 메모리에서 변경되거나 저장될 환경 또는 소스 제어 패키지를 나타냅니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>프로젝트 및 계층 구조가 소스 제어에 자신을 등록하고 소스 제어 상태에 대한 정보를 얻을 수 있도록 합니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>프로젝트 파일 및 프로젝트 항목에 대한 소스 제어를 제공하기 위해 프로젝트 시스템에서 구현됩니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>프로젝트에서 솔루션에서 파일 또는 디렉터리 이름을 추가, 제거 또는 이름을 바꿀 수 있는 권한을 쿼리하는 데 사용됩니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>프로젝트 파일 또는 디렉터리에 대한 변경 내용을 클라이언트에 통보합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 유형](../../extensibility/internals/project-types.md)

 통합 개발 환경(IDE)의 기본 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 구성 요소로서 프로젝트의 개요를 제공합니다. 프로젝트가 빌드 및 컴파일 코드를 제어하는 방법을 설명하는 추가 항목에 대한 링크가 제공됩니다.

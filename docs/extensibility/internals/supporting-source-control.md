---
title: 소스 제어 지원 | Microsoft Docs
description: Visual Studio에서 프로젝트 또는 편집기에 대 한 파일 체크 아웃, 체크 인 및 기타 소스 제어 작업을 지 원하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6923eb7a534a4cacf8062883d073ddddc9395e17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892556"
---
# <a name="supporting-source-control"></a>소스 제어 지원
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 프로젝트 또는 편집기에 대 한 파일 체크 아웃, 체크 인 및 기타 소스 제어 작업을 지원 합니다. 원본 제어 클라이언트는 동적으로 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] 정의 된 파일 집합에 대 한 보관, 버전 관리 및 제어 기능을 제공 하는와 같은 소스 제어 패키지와 상호 작용 하도록 설계 되었습니다.

## <a name="in-this-section"></a>섹션 내용
- [소스 제어 패키지 모델](../../extensibility/internals/model-for-source-control-packages.md)

 소스 제어를 지원 하기 위해 프로젝트 형식이 구현 해야 하는 인터페이스에 대해 설명 합니다.

- [디자인 결정](../../extensibility/internals/source-control-design-decisions.md)

 프로젝트 형식을 구현 하는 방법에 대 한 답변이 변경 된 질문을 제공 합니다.

- [구성 세부 정보](../../extensibility/internals/source-control-configuration-details.md)

 지원 소스 제어에서 프로젝트 형식의 구현을 변경 하는 방법을 설명 합니다.

- [프로젝트 및 편집기에 대한 추가 지침](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 프로젝트 형식 및 편집기에 대 한 모범 사례를 설명 합니다.

- [런타임 세부 정보](../../extensibility/internals/source-control-runtime-details.md)

 사용자가 프로젝트를 소스 제어 시스템에 추가할 때 프로젝트를 등록 하는 방법을 설명 합니다.

## <a name="reference"></a>참조
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 파일이 메모리에서 변경 되거나 저장 되는 환경이 나 소스 제어 패키지를 나타냅니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> 프로젝트 및 계층 구조에서 소스 제어를 사용 하 여 자신을 등록 하 고 소스 제어 상태에 대 한 정보를 가져올 수 있습니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 프로젝트 파일 및 프로젝트 항목에 대 한 소스 제어를 제공 하기 위해 프로젝트 시스템에서 구현 됩니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 프로젝트에서 솔루션의 파일이 나 디렉터리를 추가, 제거 또는 이름을 변경할 수 있는 권한을 환경에 쿼리 하는 데 사용 됩니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> 프로젝트 파일이 나 디렉터리에 대 한 변경 내용을 클라이언트에 알립니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 형식](../../extensibility/internals/project-types.md):

 IDE (통합 개발 환경)의 기본 구성 요소로 프로젝트 개요를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. 프로젝트에서 코드 빌드 및 컴파일을 제어 하는 방법을 설명 하는 추가 항목에 대 한 링크가 제공 됩니다.

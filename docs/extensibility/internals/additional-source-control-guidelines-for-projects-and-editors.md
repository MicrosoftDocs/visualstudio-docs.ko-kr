---
title: 프로젝트 및 편집자를 위한 추가 소스 제어 지침 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710117"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>프로젝트 및 편집자에 대한 추가 소스 제어 지침
소스 제어를 지원하기 위해 프로젝트와 편집자가 준수해야 하는 여러 가지 지침이 있습니다.

## <a name="guidelines"></a>지침
 프로젝트 또는 편집기는 소스 제어를 지원하기 위해 다음을 수행해야 합니다.

|영역|Project|편집기|세부 정보|
|----------|-------------|------------|-------------|
|파일의 비공개 사본|X||환경은 파일의 개인 복사본을 지원합니다. 즉, 프로젝트에 참여한 각 사람은 해당 프로젝트에 있는 파일의 개인 복사본을 가지고 있습니다.|
|ANSI/유니코드 지속성|X|X|지속성 코드를 작성하는 경우 대부분의 소스 제어 프로그램이 현재 유니코드를 지원하지 않으므로 ANSI 양식에 파일을 유지합니다.|
|파일 열거|X||프로젝트에는 해당 내의 모든 파일의 특정 목록이 포함되어야 하며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 또는(VSH_PROPID_First_Child/Next_Sibling)를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 사용하여 파일 목록을 열거할 수 있어야 합니다. 또한 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> 구현 및 지원 이름 조회(특수 파일 포함)를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> 통해 구현을 통해 항목 이름을 노출해야 합니다.|
|텍스트 형식|X|X|가능하면 파일은 다른 버전의 병합을 지원하기 위해 텍스트 형식으로 되어 있어야 합니다. 텍스트 형식이 아닌 파일은 나중에 파일의 다른 버전과 병합할 수 없습니다. 기본 텍스트 형식은 XML입니다.|
|참조 기반|X||참조 기반 프로젝트는 소스 제어에서 쉽게 지원됩니다. 그러나 디렉터리 기반 프로젝트는 해당 파일이 디스크에 있는지 여부에 관계없이 프로젝트가 요청 시 해당 파일 목록을 생성할 수 있는 한 소스 제어에 의해 지원됩니다. 소스 컨트롤에서 프로젝트를 열 때 프로젝트 파일보다 먼저 프로젝트 파일이 다운됩니다.|
|개체 및 속성을 예측 가능한 순서로 유지|X|X|병합을 용이하게 하기 위해 사전순과 같은 예측 가능한 순서로 파일을 유지합니다.|
|다시 로드|X|X|디스크에서 파일이 변경되면 편집기에서 파일을 다시 로드할 수 있어야 합니다. 원본 제어에 참여하면 환경이 구현을 호출하여 데이터를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> 다시 로드합니다. 가장 어려운 다시 로드 사례는 IVsQueryEditQuerySave::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 및 처리 정보를 호출할 때 체크 아웃이 발생하는 경우입니다. 그러나 이 상황에서는 다시 로드 코드를 실행할 수 있어야 합니다.<br /><br /> 환경은 자동으로 프로젝트 파일을 다시 로드합니다. 그러나 중첩된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 프로젝트 파일 다시 로드를 지원하려면 프로젝트가 중첩된 계층을 가지고 있는 경우 구현해야 합니다.|

## <a name="see-also"></a>참조
- [지원 소스 제어](../../extensibility/internals/supporting-source-control.md)

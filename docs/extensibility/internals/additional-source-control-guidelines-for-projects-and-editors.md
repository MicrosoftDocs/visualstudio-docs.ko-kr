---
title: 프로젝트 및 편집기에 대 한 추가 소스 제어 지침 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710117"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>프로젝트 및 편집기에 대 한 추가 소스 제어 지침
소스 제어를 지원 하기 위해 프로젝트와 편집기에서 준수 해야 하는 여러 가지 지침이 있습니다.

## <a name="guidelines"></a>지침
 프로젝트 또는 편집기에서 소스 제어를 지원 하려면 다음을 수행 해야 합니다.

|영역|프로젝트|편집기|세부 정보|
|----------|-------------|------------|-------------|
|파일의 전용 복사본|X||환경에서는 파일의 전용 복사본을 지원 합니다. 즉, 프로젝트에 참여 하는 각 사용자에 게는 해당 프로젝트의 파일에 대 한 자체 개인 사본이 있습니다.|
|ANSI/유니코드 지 속성|X|X|지 속성 코드를 작성 하는 경우 대부분의 소스 제어 프로그램에서 현재 유니코드를 지원 하지 않으므로 ANSI 폼에 파일을 저장 합니다.|
|파일 열거|X||프로젝트에는 포함 된 모든 파일의 특정 목록이 포함 되어야 하며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling)를 사용 하 여 파일 목록을 열거할 수 있어야 합니다. 또한 프로젝트는 구현을 통해 항목 이름을 노출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> 하 고 해당 구현을 통해 이름 조회 (특수 파일 포함)를 지원 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> .|
|텍스트 형식|X|X|가능 하면 파일은 서로 다른 버전의 병합을 지원 하기 위해 텍스트 형식 이어야 합니다. 텍스트 형식이 아닌 파일은 나중에 다른 파일 버전과 병합할 수 없습니다. 기본 텍스트 형식은 XML입니다.|
|참조 기반|X||참조 기반 프로젝트는 소스 제어에서 즉시 지원 됩니다. 그러나 해당 파일이 디스크에 있는지 여부에 관계 없이 프로젝트에서 요청 시 파일 목록을 생성할 수 있는 한, 디렉터리 기반 프로젝트도 소스 제어에서 지원 됩니다. 소스 제어에서 프로젝트를 열 때 프로젝트 파일은 파일 앞에 먼저 있습니다.|
|개체 및 속성을 예측 가능한 순서로 유지|X|X|병합을 용이 하 게 하기 위해 파일을 알파벳 순서와 같은 예측 가능한 순서로 유지 합니다.|
|다시 로드|X|X|디스크에서 파일을 변경 하면 편집기에서 파일을 다시 로드할 수 있어야 합니다. 소스 제어에 참여 하는 경우 환경에서 구현을 호출 하 여 데이터를 다시 로드 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> . 가장 어려운 다시 로드 사례는 IVsQueryEditQuerySave:: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 를 호출 하 고 정보를 처리 하는 경우 체크 아웃이 수행 되는 경우입니다. 그러나이 경우에는 다시 로드 코드를 실행할 수 있어야 합니다.<br /><br /> 환경에서 프로젝트 파일을 자동으로 다시 로드 합니다. 그러나 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 중첩 된 프로젝트 파일 다시 로드를 지원 하기 위해 프로젝트가 중첩 된 계층 구조를 포함 하는 경우에는 프로젝트를 구현 해야 합니다.|

## <a name="see-also"></a>참고 항목
- [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)

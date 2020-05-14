---
title: 프로젝트 지속성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706454"
---
# <a name="project-persistence"></a>프로젝트 지속성
지속성은 프로젝트의 주요 설계 고려 사항입니다. 대부분의 프로젝트는 파일을 나타내는 프로젝트 항목을 사용합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 또한 데이터가 파일 기반이 아닌 프로젝트를 지원합니다. 프로젝트가 소유한 파일과 프로젝트 파일은 모두 유지되어야 합니다. IDE는 프로젝트 자체 또는 프로젝트 항목을 저장하도록 지시합니다.

 프로젝트에 대한 템플릿이 프로젝트 팩터리로 전달됩니다. 템플릿은 특정 프로젝트 유형의 요구 사항에 따라 모든 프로젝트 항목의 초기화를 지원해야 합니다. 이러한 템플릿은 나중에 프로젝트 파일로 저장하고 솔루션을 통해 IDE에서 관리할 수 있습니다. 자세한 내용은 프로젝트 팩터리 및 [솔루션을](../../extensibility/internals/solutions-overview.md) [사용하여 프로젝트 인스턴스 만들기를](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) 참조하십시오.

 프로젝트 항목은 파일 기반이거나 파일 기반이 아닐 수 있습니다.

- 파일 기반 항목은 로컬 또는 원격일 수 있습니다. 예를 들어 C#의 웹 프로젝트에서는 원격 시스템의 파일에 대한 연결이 로컬로 유지되지만 파일 자체는 원격 시스템에서 유지됩니다.

- 파일 기반이 아닌 항목은 항목을 데이터베이스 또는 리포지토리에 저장할 수 있습니다.

## <a name="commit-models"></a>커밋 모델
 프로젝트 항목의 위치를 결정한 후 적절한 커밋 모델을 선택해야 합니다. 예를 들어 로컬 파일이 있는 파일 기반 모델에서는 각 프로젝트를 자율적으로 저장할 수 있습니다. 리포지토리 모델에서 한 트랜잭션에 여러 항목을 저장할 수 있습니다. 자세한 내용은 [프로젝트 유형 설계 결정을](../../extensibility/internals/project-type-design-decisions.md)참조하십시오.

 파일 이름 확장명을 결정하기 위해 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 프로젝트는 개체의 클라이언트가 **저장 문자** 저장 **드롭다운** 목록을 채우고 초기 파일 이름 확장명을 관리할 수 있는 정보를 제공하는 인터페이스를 구현합니다.

 IDE는 프로젝트의 `IPersistFileFormat` 인터페이스를 호출하여 프로젝트가 프로젝트 항목을 적절히 유지해야 함을 나타냅니다. 따라서 개체는 파일 및 형식의 모든 측면을 소유합니다. 여기에는 개체 형식의 이름이 포함됩니다.

 항목이 파일이 `IPersistFileFormat` 아닌 경우 파일 기반이 아닌 항목이 유지되는 방식은 여전히 남아 있습니다. 프로젝트에 대한 .vbp 파일이나 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트에 대한 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .vcproj 파일과 같은 프로젝트 파일도 유지되어야 합니다.

 저장 작업의 경우 IDE는 실행 중인 문서 테이블(RDT)을 검사하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 계층 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 구조는 명령을 인터페이스와 인터페이스에 전달합니다. 이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> 메서드는 항목이 수정되었는지 여부를 확인하기 위해 구현됩니다. 항목이 있는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> 수정된 항목을 저장 하기 위해 메서드가 구현 됩니다.

 인터페이스의 `IVsPersistHierarchyItem2` 메서드는 항목을 다시 로드할 수 있는지 여부와 항목이 다시 로드할 수 있는 경우 를 결정하는 데 사용됩니다. 또한 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> 구현하여 변경된 항목을 저장하지 않고 삭제할 수 있습니다.

## <a name="see-also"></a>참조
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

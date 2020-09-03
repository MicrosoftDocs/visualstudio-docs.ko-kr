---
title: 프로젝트 지 속성 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706454"
---
# <a name="project-persistence"></a>프로젝트 지속성
지 속성은 프로젝트에 중요 한 디자인 고려 사항입니다. 대부분의 프로젝트는 파일을 나타내는 프로젝트 항목을 사용 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 는 파일 기반이 아닌 데이터가 있는 프로젝트도 지원 합니다. 프로젝트와 프로젝트 파일이 소유한 파일을 모두 유지 해야 합니다. IDE는 프로젝트에 자체 또는 프로젝트 항목을 저장 하도록 지시 합니다.

 프로젝트에 대 한 템플릿이 프로젝트 팩터리에 전달 됩니다. 템플릿은 특정 프로젝트 형식에 대 한 요구 사항에 따라 모든 프로젝트 항목의 초기화를 지원 해야 합니다. 이러한 템플릿은 나중에 프로젝트 파일로 저장 하 고 솔루션을 통해 IDE에서 관리할 수 있습니다. 자세한 내용은 프로젝트 팩터리 및 [솔루션](../../extensibility/internals/solutions-overview.md)을 [사용 하 여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) 를 참조 하세요.

 프로젝트 항목은 파일 기반 이거나 파일 기반이 아닐 수 있습니다.

- 파일 기반 항목은 로컬 또는 원격 일 수 있습니다. 예를 들어 c #의 웹 프로젝트에서는 원격 시스템의 파일에 대 한 연결이 로컬로 유지 되는 반면 파일 자체는 원격 시스템에 유지 됩니다.

- 파일 기반이 아닌 항목은 데이터베이스 또는 리포지토리에 항목을 저장할 수 있습니다.

## <a name="commit-models"></a>모델 커밋
 프로젝트 항목의 위치를 결정 한 후 적절 한 커밋 모델을 선택 해야 합니다. 예를 들어 로컬 파일이 있는 파일 기반 모델에서는 각 프로젝트를 자율적으로 저장할 수 있습니다. 리포지토리 모델에서는 여러 항목을 하나의 트랜잭션으로 저장할 수 있습니다. 자세한 내용은 [프로젝트 형식 디자인 결정](../../extensibility/internals/project-type-design-decisions.md)을 참조 하세요.

 파일 이름 확장명을 확인 하기 위해 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 개체의 클라이언트에서 **다른 이름** 으로 저장 대화 상자를 구현 하는 데 사용할 수 있는 정보를 제공 하는 인터페이스를 구현 합니다. 즉, 파일 **형식** 드롭다운 목록을 채우고 초기 파일 이름 확장명을 관리할 수 있습니다.

 IDE는 프로젝트의 인터페이스를 호출 하 여 프로젝트에서 프로젝트 `IPersistFileFormat` 항목을 적절 하 게 유지 해야 함을 표시 합니다. 따라서 개체는 파일 및 형식의 모든 측면을 소유 합니다. 여기에는 개체의 형식 이름이 포함 됩니다.

 항목이 파일이 아닌 경우는 `IPersistFileFormat` 여전히 파일 기반이 아닌 항목을 유지 하는 방법입니다. 프로젝트에 대 한 .vbp 파일, 프로젝트에 대 한 .vcproj 파일 등의 프로젝트 파일도 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 유지 되어야 합니다.

 저장 동작의 경우 IDE는 실행 중인 문서 테이블 (RDT)을 검사 하 고 계층 구조는 명령을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 및 인터페이스에 전달 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>메서드는 항목이 수정 되었는지 여부를 확인 하기 위해 구현 됩니다. 항목에가 있는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> 메서드는 수정 된 항목을 저장 하도록 구현 됩니다.

 인터페이스의 메서드는 `IVsPersistHierarchyItem2` 항목을 다시 로드할 수 있는지 여부를 확인 하는 데 사용 되 고, 항목을 다시 로드 하려면 항목을 다시 로드 하는 데 사용 됩니다. 또한 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> 구현 하 여 변경 된 항목을 저장 하지 않고 삭제 하도록 할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

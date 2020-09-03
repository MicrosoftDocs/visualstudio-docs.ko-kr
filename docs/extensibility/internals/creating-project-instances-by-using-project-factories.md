---
title: 프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709057"
---
# <a name="create-project-instances-by-using-project-factories"></a>프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기
의 프로젝트 형식은 프로젝트 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] *팩터리* 를 사용 하 여 project 개체의 인스턴스를 만듭니다. 프로젝트 팩터리는 공동 생성 가능한 COM 개체에 대 한 표준 클래스 팩터리와 비슷합니다. 그러나 프로젝트 개체는 공동 생성할 수 없습니다. 프로젝트 팩터리를 사용 해야만 만들 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE는 사용자가 기존 프로젝트를 로드 하거나에서 새 프로젝트를 만들 때 VSPackage에 구현 된 프로젝트 팩터리를 호출 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 새 프로젝트 개체는 **솔루션 탐색기**을 채울 수 있는 충분 한 정보를 IDE에 제공 합니다. 또한 새 프로젝트 개체는 IDE에서 시작 하는 모든 관련 UI 작업을 지 원하는 데 필요한 인터페이스를 제공 합니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>프로젝트의 클래스에서 인터페이스를 구현할 수 있습니다. 일반적으로 자체 모듈에 상주 합니다.

 소유자가 집계 하는 것을 지 원하는 프로젝트는 해당 프로젝트 파일에 소유자 키를 유지 해야 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>소유자 키가 있는 프로젝트에서 메서드를 호출 하는 경우 소유 된 프로젝트는 소유자 키를 프로젝트 팩터리 GUID로 변환한 다음 `CreateProject` 이 프로젝트 팩터리에 대해 메서드를 호출 하 여 실제 생성을 수행 합니다.

## <a name="create-an-owned-project"></a>소유 된 프로젝트 만들기
 소유자는 다음과 같은 두 단계로 소유 된 프로젝트를 만듭니다.

1. 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> 합니다. 이렇게 하면 소유 하는 프로젝트에서 입력 제어를 기반으로 집계 된 프로젝트 개체를 만들 수 `IUnknown` 있습니다. 소유 된 프로젝트는 내부 `IUnknown` 및 집계 된 개체를 소유자 프로젝트에 다시 전달 합니다. 이렇게 하면 소유 하는 프로젝트에서 내부를 저장할 수 `IUnknown` 있습니다.

2. 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> 합니다. 소유 `IVsProjectFactory::CreateProject` 하지 않은 프로젝트의 경우와 같이를 호출 하는 대신이 메서드를 호출 하는 경우 소유 된 프로젝트는 모든 인스턴스화를 수행 합니다. 입력 `VSOWNEDPROJECTOBJECT` 열거형은 일반적으로 집계 된 소유 프로젝트입니다. 소유 하는 프로젝트에서는이 변수를 사용 하 여 해당 프로젝트 개체가 이미 만들어졌는지 (쿠키가 NULL이 아닌 경우) 아니면 만들어야 하는지 (쿠키가 NULL 인 경우)를 확인할 수 있습니다.

   프로젝트 형식은 cocreatable 수 있는 COM 개체의 CLSID와 유사한 고유한 프로젝트 GUID로 식별 됩니다. 일반적으로 한 프로젝트 팩터리는 하나 이상의 프로젝트 형식 GUID를 처리할 수 있지만 단일 프로젝트 형식의 인스턴스를 만드는 과정을 처리 합니다.

   프로젝트 형식은 특정 파일 이름 확장명과 연결 됩니다. 사용자가 기존 프로젝트 파일을 열거나 템플릿을 복제 하 여 새 프로젝트를 만들려고 시도 하면 IDE는 파일의 확장을 사용 하 여 해당 하는 프로젝트 GUID를 확인 합니다.

   IDE는 새 프로젝트를 만들거나 특정 형식의 기존 프로젝트를 열어야 하는지 여부를 확인 하는 즉시 **[HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\projects]** 아래에 있는 시스템 레지스트리의 정보를 사용 하 여 필요한 프로젝트 팩터리를 구현 하는 VSPackage를 확인 합니다. IDE에서이 VSPackage를 로드 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>메서드에서 VSPackage는 메서드를 호출 하 여 IDE에 프로젝트 팩터리를 등록 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> .

   인터페이스의 기본 메서드는 이며 `IVsProjectFactory` ,이는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> 기존 프로젝트를 열고 새 프로젝트를 만드는 두 가지 시나리오를 처리 해야 합니다. 대부분의 프로젝트는 프로젝트 파일에 프로젝트 상태를 저장 합니다. 일반적으로 새 프로젝트는 메서드에 전달 된 템플릿 파일의 복사본을 만든 `CreateProject` 다음 복사본을 열어 만듭니다. 기존 프로젝트는 메서드에 전달 된 프로젝트 파일을 직접 열어 인스턴스화할 수 `CreateProject` 있습니다. `CreateProject`메서드는 필요에 따라 사용자에 게 추가 UI 기능을 표시할 수 있습니다.

   프로젝트에서 파일을 사용 하지 않고 데이터베이스 또는 웹 서버와 같은 파일 시스템 이외의 저장소 메커니즘에 해당 프로젝트 상태를 저장할 수도 있습니다. 이 경우 메서드에 전달 되는 파일 이름 매개 변수는 `CreateProject` 실제로는 파일 시스템 경로가 아니라 고유한 문자열 (URL) 이므로 프로젝트 데이터를 식별 합니다. 에 전달 되는 템플릿 파일을 복사 하 여 `CreateProject` 실행할 적절 한 생성 시퀀스를 트리거할 필요가 없습니다.

## <a name="see-also"></a>추가 정보
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)

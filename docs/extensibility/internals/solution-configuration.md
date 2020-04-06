---
title: 솔루션 구성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705385"
---
# <a name="solution-configuration"></a>솔루션 구성
솔루션 구성은 솔루션 수준 속성을 저장합니다. 시작(F5) **Start** 키 및 **빌드** 명령의 동작을 지시합니다. 기본적으로 이러한 명령은 디버그 구성을 빌드하고 시작합니다. 두 명령은 솔루션 구성의 컨텍스트에서 실행됩니다. 즉, 사용자는 설정을 통해 구성된 활성 솔루션에 관계없이 F5가 시작되고 빌드될 것으로 예상할 수 있습니다. 환경은 구축 및 실행에 있어 프로젝트가 아닌 솔루션에 최적화되도록 설계되었습니다.

 표준 Visual Studio 도구 모음에는 시작 단추와 시작 버튼 오른쪽에 있는 솔루션 구성 드롭다운이 포함되어 있습니다. 이 목록을 통해 사용자는 F5를 누를 때 시작할 구성을 선택하거나, 자체 솔루션 구성을 만들거나, 기존 구성을 편집할 수 있습니다.

> [!NOTE]
> 솔루션 구성을 만들거나 편집할 수 있는 확장성 인터페이스는 없습니다. `DTE.SolutionBuild`을 사용해야 합니다. 그러나 솔루션 빌드를 관리하기 위한 확장성 API가 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>을 참조하세요.

 프로젝트 유형에서 지원하는 솔루션 구성을 구현하는 방법은 다음과 같습니다.

- Project

   현재 솔루션에 있는 프로젝트의 이름을 표시합니다.

- 구성

   프로젝트 유형에서 지원되고 속성 페이지에 표시되는 구성 목록을 제공하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>을 구현합니다.

   구성 열에는 이 솔루션 구성에서 빌드할 프로젝트 구성의 이름이 표시되고 화살표 단추를 클릭할 때 모든 프로젝트 구성이 나열됩니다. 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> 이 목록을 작성하는 메서드를 호출합니다. 메서드가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 프로젝트가 구성 편집을 지원한다는 것을 나타내면 새 선택 또는 편집 선택 항목도 구성 제목 아래에 표시됩니다. 이러한 각 선택 항목은 `IVsCfgProvider2` 인터페이스의 메서드를 호출하여 프로젝트 구성을 편집하는 대화 상자를 시작합니다.

   프로젝트가 구성을 지원하지 않는 경우 구성 열에 없음이 표시되고 비활성화됩니다.

- 플랫폼

   선택한 프로젝트 구성이 빌드하는 플랫폼을 표시하고 화살표 단추를 클릭할 때 프로젝트에 사용할 수 있는 모든 플랫폼을 나열합니다. 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> 이 목록을 작성하는 메서드를 호출합니다. 메서드가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 프로젝트가 플랫폼 편집을 지원한다는 것을 나타내면 새 선택 또는 편집 선택 항목도 플랫폼 제목 아래에 표시됩니다. 이러한 각 선택 항목은 메서드를 호출하여 `IVsCfgProvider2` 프로젝트의 사용 가능한 플랫폼을 편집하는 대화 상자를 시작합니다.

   프로젝트가 플랫폼을 지원하지 않는 경우 해당 프로젝트의 플랫폼 열에 없음이 표시되고 비활성화됩니다.

- 빌드

   현재 솔루션 구성에 의해 프로젝트가 빌드되는지 여부를 지정합니다. 선택되지 않은 프로젝트는 포함된 프로젝트 종속성에도 불구하고 솔루션 수준 빌드 명령이 호출될 때 빌드되지 않습니다. 빌드하도록 선택되지 않은 프로젝트는 여전히 솔루션의 디버깅, 실행, 패키징 및 배포에 포함됩니다.

- 배포

   선택한 솔루션 빌드 구성에서 시작 또는 배포 명령을 사용할 때 프로젝트를 배포할지 여부를 지정합니다. 이 필드에 대한 확인란을 사용할 수 있습니다 프로젝트에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 개체에 인터페이스를 구현 하 여 배포를 지원 하는 경우.

  새 솔루션 구성이 추가되면 사용자는 표준 도구 모음의 솔루션 구성 드롭다운 목록 상자에서 선택하여 해당 구성을 빌드 및/또는 시작할 수 있습니다.

## <a name="see-also"></a>참조
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)

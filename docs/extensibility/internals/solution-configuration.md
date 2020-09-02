---
title: 솔루션 구성 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705385"
---
# <a name="solution-configuration"></a>솔루션 구성
솔루션 구성에서는 솔루션 수준 속성을 저장 합니다. **시작** (F5) 키와 **빌드** 명령의 동작을 지시 합니다. 기본적으로이 명령은 디버그 구성을 빌드하고 시작 합니다. 두 명령은 모두 솔루션 구성의 컨텍스트에서 실행 됩니다. 이는 사용자가 설정으로 구성 된 활성 솔루션을 시작 하 고 빌드할 수 있습니다. 환경은 빌드하고 실행 하는 경우 프로젝트가 아닌 솔루션을 최적화 하도록 설계 되었습니다.

 표준 Visual Studio 도구 모음에는 시작 단추와 시작 단추의 오른쪽에 있는 솔루션 구성 드롭다운이 포함 되어 있습니다. 이 목록을 통해 사용자는 F5 키를 누를 때 시작할 구성을 선택 하거나, 고유한 솔루션 구성을 만들거나, 기존 구성을 편집할 수 있습니다.

> [!NOTE]
> 솔루션 구성을 만들거나 편집할 수 있는 확장성 인터페이스가 없습니다. `DTE.SolutionBuild`을 사용해야 합니다. 그러나 솔루션 빌드를 관리 하기 위한 확장성 Api는 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>를 참조하세요.

 프로젝트 형식에서 지 원하는 솔루션 구성을 구현 하는 방법은 다음과 같습니다.

- 프로젝트

   현재 솔루션에 있는 프로젝트의 이름을 표시 합니다.

- 구성

   프로젝트 형식에서 지원 되 고 속성 페이지에 표시 되는 구성 목록을 제공 하려면를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 합니다.

   구성 열은이 솔루션 구성에서 빌드할 프로젝트 구성의 이름을 표시 하 고 화살표 단추를 클릭 하면 모든 프로젝트 구성을 나열 합니다. 환경에서는 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> 하 여이 목록을 채웁니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>메서드가 프로젝트에서 구성 편집을 지원함을 나타내는 경우에는 구성 제목 아래에 새 선택 항목 또는 편집 항목도 표시 됩니다. 이러한 선택 항목은 모두 인터페이스의 메서드를 호출 하 여 프로젝트의 구성을 편집 하는 대화 상자를 시작 `IVsCfgProvider2` 합니다.

   프로젝트에서 구성을 지원 하지 않으면 구성 열에 없음이 표시 되 고 사용 하지 않도록 설정 됩니다.

- 플랫폼

   선택한 프로젝트 구성이 빌드되는 플랫폼을 표시 하 고 화살표 단추를 클릭할 때 프로젝트에 사용할 수 있는 모든 플랫폼을 나열 합니다. 환경에서는 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> 하 여이 목록을 채웁니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>메서드가 프로젝트에서 플랫폼 편집을 지원함을 나타내는 경우에는 플랫폼 제목 아래에 새 선택 항목 또는 편집 항목도 표시 됩니다. 이러한 선택 항목은 모두 메서드를 호출 하 여 `IVsCfgProvider2` 프로젝트의 사용 가능한 플랫폼을 편집 하는 대화 상자를 시작 합니다.

   프로젝트에서 플랫폼을 지원 하지 않는 경우 해당 프로젝트의 플랫폼 열에 없음이 표시 되 고 사용 하지 않도록 설정 됩니다.

- 빌드

   현재 솔루션 구성에서 프로젝트를 빌드 하는지 여부를 지정 합니다. 솔루션 수준 빌드 명령이 포함 된 프로젝트 종속성에도 불구 하 고 솔루션 수준 빌드 명령이 호출 되는 경우 선택 되지 않은 프로젝트는 빌드되지 않습니다. 빌드 하도록 선택 되지 않은 프로젝트는 솔루션의 디버깅, 실행, 패키징 및 배포에 계속 포함 됩니다.

- 배포

   선택한 솔루션 빌드 구성과 함께 시작 또는 배포 명령을 사용할 때 프로젝트를 배포할지 여부를 지정 합니다. 프로젝트에서 개체에 인터페이스를 구현 하 여 배포를 지 원하는 경우이 필드에 대 한 확인란을 사용할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> .

  새 솔루션 구성이 추가 되 면 사용자는 표준 도구 모음의 솔루션 구성 드롭다운 목록 상자에서 선택 하 여 해당 구성을 빌드 및/또는 시작할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [프로젝트 구성 개체](../../extensibility/internals/project-configuration-object.md)

---
title: 솔루션 개요
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705307"
---
# <a name="solutions-overview"></a>솔루션 개요

솔루션은 응용 프로그램을 만들기 위해 함께 작동하는 하나 이상의 프로젝트를 그룹화하는 것입니다. 솔루션과 관련된 프로젝트 및 상태 정보는 두 개의 서로 다른 솔루션 파일에 저장됩니다. [솔루션(.sln) 파일은](solution-dot-sln-file.md) 텍스트 기반이며 소스 코드 제어 하에 배치되어 사용자 간에 공유할 수 있습니다. [솔루션 사용자 옵션(.suo) 파일은](solution-user-options-dot-suo-file.md) 바이너리입니다. 따라서 .suo 파일은 소스 코드 제어 하에 배치할 수 없으며 사용자 별 정보를 포함합니다.

모든 VSPackage는 두 가지 유형의 솔루션 파일에 쓸 수 있습니다. 파일의 특성상 파일에 쓰기 위해 구현된 두 가지 인터페이스가 있습니다. 인터페이스는 .sln 파일에 텍스트 정보를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 쓰고 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> .suo 파일에 이진 스트림을 씁니다.

> [!NOTE]
> 프로젝트는 솔루션 파일에 자체에 대한 항목을 명시적으로 작성할 필요가 없습니다. 환경은 프로젝트에 대해 이를 처리합니다. 따라서 솔루션 파일에 특별히 추가 콘텐츠를 추가하려는 경우가 아니면 이러한 방식으로 VSPackage를 등록할 필요가 없습니다.

각 VSPackage 지원 솔루션 지속성은 세 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 가지 인터페이스, 즉 환경에서 구현되고 VSPackage에서 `IVsPersistSolutionProps` `IVsPersistSolutionOpts`호출되는 인터페이스와 VSPackage에서 구현되는 인터페이스를 사용합니다. 개인 `IVsPersistSolutionOpts` 정보를 .suo 파일에 VSPackage에서 작성해야 하는 경우에만 인터페이스를 구현해야 합니다.

솔루션이 열리면 다음 프로세스가 수행됩니다.

1. 환경에서 솔루션을 읽습니다.

2. 환경이 `CLSID`을 찾으면 해당 VSPackage를 로드합니다.

3. VSPackage가 로드된 경우 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> VSPackage에 필요한 인터페이스에 대한 인터페이스를 요구합니다. `QueryInterface`

   - .sln 파일에서 읽을 때 환경이 `IVsPersistSolutionProps`를 호출합니다. `QueryInterface`

   - .suo 파일에서 읽을 때 환경이 `IVsPersistSolutionOpts`를 호출합니다. `QueryInterface`

   이러한 파일의 사용과 관련된 특정 정보는 솔루션(에서 찾을 수 [있습니다. Sln) 파일](../../extensibility/internals/solution-dot-sln-file.md) 및 [솔루션 사용자 옵션(. Suo) 파일](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> 두 프로젝트의 구성으로 구성된 새 솔루션 구성을 만들고 빌드에서 세 번째 를 제외하려면 속성 페이지 UI 또는 자동화를 사용해야 합니다. 솔루션 빌드 관리자 구성 및 해당 속성을 직접 변경할 수는 없지만 자동화 모델에서 `SolutionBuild` DTE의 클래스를 사용하여 솔루션 빌드 관리자를 조작할 수 있습니다. 솔루션 구성에 대한 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md)을 참조하십시오.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

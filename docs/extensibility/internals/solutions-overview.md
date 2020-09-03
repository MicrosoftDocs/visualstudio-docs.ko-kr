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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705307"
---
# <a name="solutions-overview"></a>솔루션 개요

솔루션은 응용 프로그램을 만들기 위해 함께 작동 하는 하나 이상의 프로젝트를 그룹화 한 것입니다. 솔루션과 관련 된 프로젝트 및 상태 정보는 서로 다른 두 솔루션 파일에 저장 됩니다. [솔루션 (.sln) 파일](solution-dot-sln-file.md) 은 텍스트 기반 이며, 소스 코드 제어에 배치 되 고 사용자 간에 공유 될 수 있습니다. [솔루션 사용자 옵션 (.suo) 파일](solution-user-options-dot-suo-file.md) 은 이진 파일입니다. 따라서 .suo 파일은 소스 코드 제어 아래에 배치 될 수 없으며 사용자 관련 정보를 포함 합니다.

모든 VSPackage는 두 가지 유형의 솔루션 파일에 쓸 수 있습니다. 파일의 특성으로 인해 이러한 파일에 쓰도록 구현 된 두 가지 인터페이스가 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>인터페이스는 텍스트 정보를 .sln 파일에 쓰고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> 인터페이스는 이진 스트림을 .suo 파일에 씁니다.

> [!NOTE]
> 프로젝트는 자신에 대 한 항목을 솔루션 파일에 명시적으로 작성할 필요가 없습니다. 환경에서 프로젝트에 대 한를 처리 합니다. 따라서 솔루션 파일에 추가 콘텐츠를 추가 하려는 경우가 아니면 이러한 방식으로 VSPackage를 등록할 필요가 없습니다.

각 VSPackage 지원 솔루션 지 속성은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 환경에서 구현 되 고 VSPackage에 의해 호출 되는 인터페이스와 `IVsPersistSolutionProps` `IVsPersistSolutionOpts` VSPackage에 의해 구현 되는 및와 같은 세 가지 인터페이스를 사용 합니다. `IVsPersistSolutionOpts`VSPackage에서 .suo 파일에 개인 정보를 쓸 경우에만 인터페이스를 구현 해야 합니다.

솔루션이 열리면 다음 프로세스가 수행 됩니다.

1. 환경에서 솔루션을 읽습니다.

2. 환경에서를 찾으면 `CLSID` 해당 VSPackage을 로드 합니다.

3. VSPackage가 로드 되 면 환경에서 VSPackage에 `QueryInterface` 필요한 인터페이스에 대 한 인터페이스를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> .

   - .Sln 파일에서 읽을 때 환경에서는를 호출 합니다 `QueryInterface` `IVsPersistSolutionProps` .

   - .Suo 파일에서 읽을 때 환경에서는를 호출 합니다 `QueryInterface` `IVsPersistSolutionOpts` .

   이러한 파일의 사용과 관련 된 구체적인 정보는 솔루션 ()에서 찾을 수 있습니다 [. Sln) 파일](../../extensibility/internals/solution-dot-sln-file.md) 및 [솔루션 사용자 옵션 (. .Suo) 파일](../../extensibility/internals/solution-user-options-dot-suo-file.md)

> [!NOTE]
> 두 프로젝트의 구성으로 구성 된 새 솔루션 구성을 만들고 세 번째를 빌드에서 제외 하려면 속성 페이지 UI 또는 자동화를 사용 해야 합니다. 솔루션 빌드 관리자 구성과 해당 속성을 직접 변경할 수는 없지만 `SolutionBuild` 자동화 모델에서 DTE의 클래스를 사용 하 여 솔루션 빌드 관리자를 조작할 수 있습니다. 솔루션을 구성 하는 방법에 대 한 자세한 내용은 [솔루션 구성](../../extensibility/internals/solution-configuration.md)을 참조 하세요.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>

---
title: 다중 프로세서를 사용하여 프로젝트 빌드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multiple processors
- MSBuild, multiple processor systems
ms.assetid: 49fa36c9-8e14-44f5-8a2b-34146cf6807b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5dc62112324f7ad19c47b346ac8c1e3f86570b0
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631304"
---
# <a name="use-multiple-processors-to-build-projects"></a>다중 프로세서를 사용하여 프로젝트 빌드

MSBuild에서는 다중 프로세서 또는 다중 핵심 프로세서가 있는 시스템을 사용할 수 있습니다. 사용 가능한 각 프로세서에 대해 별도 빌드 프로세스가 만들어집니다. 예를 들어 시스템에 4개의 프로세서가 있는 경우 네 개의 빌드 프로세스가 만들어집니다. MSBuild는 이러한 빌드를 동시에 처리할 수 있기 때문에 전체 빌드 시간이 감소합니다. 그러나 병렬 빌드에서는 빌드 프로세스가 발생하는 방법과 관련하여 몇 가지 사항이 변경되었습니다. 이 항목에서는 이러한 변경 내용에 대해 설명합니다.

## <a name="project-to-project-references"></a>프로젝트 간 참조

 Microsoft Build Engine은 병렬 빌드를 사용하여 프로젝트를 빌드하는 동안 P2P(프로젝트 간) 참조가 발생하면 해당 참조를 한 번만 빌드합니다. 두 프로젝트에 동일한 P2P 참조가 있는 경우 각 프로젝트에 대해 참조가 다시 빌드되지 않습니다. 대신 빌드 엔진은 의존하는 두 프로젝트 모두에 대해 동일한 P2P 참조를 반환합니다. 동일한 대상에 대한 세션의 후속 요청에 동일한 P2P 참조가 제공됩니다.

## <a name="cycle-detection"></a>주기 검색

 주기 검색은 현재 MSBuild가 다른 시간이나 빌드에서 주기 검색을 보고할 수 있다는 점을 제외하고 MSBuild 2.0의 경우와 동일하게 작동합니다.

## <a name="errors-and-exceptions-during-parallel-builds"></a>병렬 빌드 중 오류 및 예외

 병렬 빌드에서는 비병렬 빌드에서 수행하는 것과는 다른 시간에 오류 및 예외가 발생할 수 있고, 하나의 프로젝트가 빌드되지 않을 때 다른 프로젝트가 계속 빌드될 수 있습니다. MSBuild는 한 프로젝트 빌드가 실패한 경우에도 병렬로 수행 중인 다른 프로젝트 빌드가 중지되지 않습니다. 따라서 다른 프로젝트는 성공 또는 실패할 때까지 계속 빌드됩니다. 그러나 <xref:Microsoft.Build.Framework.IBuildEngine.ContinueOnError%2A>가 활성화된 경우 오류가 발생하더라도 빌드가 중지되지 않습니다.

## <a name="c-project-vcxproj-and-solution-sln-files"></a>C++ 프로젝트(.vcxproj) 및 솔루션(.sln) 파일

 C++ 프로젝트( *.vcxproj*) 및 솔루션( *.sln*) 파일은 둘 다 [MSBuild 작업](../msbuild/msbuild-task.md)에 전달될 수 있습니다. C++ 프로젝트의 경우 VCWrapperProject가 호출된 다음 내부 MSBuild 프로젝트가 만들어집니다. C++ 솔루션의 경우 SolutionWrapperProject가 호출된 다음 내부 MSBuild 프로젝트가 만들어집니다. 두 경우 모두 결과 프로젝트는 다른 MSBuild 프로젝트와 동일하게 처리됩니다.

## <a name="multi-process-execution"></a>다중 프로세스 실행

 거의 모든 빌드 관련 작업을 수행할 때 경로 관련 오류를 방지하기 위해 빌드 프로세스 전체에서 현재 디렉터리가 일정하게 유지되어야 합니다. 따라서 여러 디렉터리가 만들어지는 결과를 가져오므로 프로젝트를 MSBuild의 여러 다른 스레드에서 실행할 수 없습니다.

 이 문제를 방지하면서 여전히 다중 프로세서 빌드를 사용하기 위해 MSBuild에서는 "프로세스 격리"를 사용합니다. 프로세스 격리를 사용하여 MSBuild는 최대 `n`개의 프로세스를 만들 수 있습니다. 여기서 `n`은 시스템에서 사용할 수 있는 프로세서 수입니다. 예를 들어 MSBuild가 2개의 프로세서가 있는 시스템에서 솔루션을 빌드할 경우 빌드 프로세스가 2개만 만들어집니다. 이러한 프로세스는 솔루션의 모든 프로젝트를 빌드하기 위해 다시 사용됩니다.

## <a name="see-also"></a>참조

- [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
- [작업](../msbuild/msbuild-tasks.md)

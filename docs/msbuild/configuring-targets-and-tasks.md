---
title: 대상 및 작업 구성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a3d6ba3eff6a01c2d0ff68b4132d883eadb90f
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634398"
---
# <a name="configure-targets-and-tasks"></a>대상 및 작업 구성

MSBuild 대상 및 작업을 구성하여 MSBuild를 통해 out-of-process로 실행할 수 있으므로 현재 실행하고 있는 컨텍스트와는 다른 컨텍스트를 대상으로 지정할 수 있습니다. 예를 들어, 개발 컴퓨터가 64비트 .NET Framework 4.5 운영 체제에서 실행되는 동안 32비트 .NET Framework 2.0 애플리케이션을 대상으로 지정할 수 있습니다. 또한 .NET Framework 4 또는 이전 버전을 실행하는 컴퓨터를 대상으로 지정할 수 있습니다. 32비트 또는 64비트 및 특정 .NET Framework 버전의 조합은 *대상 컨텍스트*로 알려져 있습니다.

## <a name="installation"></a>설치

  Visual Studio와 개별적으로 MSBuild를 설치하려면 [MSBuild 다운로드](https://www.microsoft.com/download/details.aspx?id=40760)에서 설치 패키지를 다운로드할 수 있습니다. 또한 사용하려는 .NET Framework 버전도 설치해야 합니다.

## <a name="targets-and-tasks"></a>대상 및 작업

 MSBuild는 특정 빌드 작업을 프로세스 외부에서 실행하여 더 큰 컨텍스트 집합을 대상으로 지정합니다.  예를 들어, 32비트 MSBuild가 64비트 프로세스에서 빌드 작업을 실행하여 64비트 컴퓨터를 대상으로 지정할 수 있습니다. 이 작업은 `UsingTask` 인수 및 `Task` 매개 변수에 의해 제어됩니다. .NET Framework 4.5에 의해 설치된 대상은 이러한 인수 및 매개 변수를 설정하고, 다양한 대상 컨텍스트를 위한 애플리케이션을 빌드하는 데 필요한 변경 사항은 없습니다.

 대상 컨텍스트를 직접 만들려면 이러한 인수 및 매개 변수를 적절하게 설정해야 합니다. .NET Framework 4.5 *Microsoft.Common.targets* 파일과 *Microsoft.Common.Tasks* 파일에서 예제를 살펴봅니다.  여러 대상 컨텍스트를 사용하여 작업할 수 있는 사용자 지정 작업 만들기 또는 기존 작업을 수정하는 방법에 대한 자세한 내용은 [방법: 대상 및 작업 구성](../msbuild/how-to-configure-targets-and-tasks.md)을 참조하세요.

## <a name="see-also"></a>참조

- [멀티 타기팅](../msbuild/msbuild-multitargeting-overview.md)

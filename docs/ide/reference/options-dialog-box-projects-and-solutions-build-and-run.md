---
title: 옵션 대화 상자, 프로젝트 및 솔루션, 빌드 및 실행
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ba5bbf34ecc12c2508c538e74909ee0a10aef4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68461387"
---
# <a name="options-dialog-box-projects-and-solutions--build-and-run"></a>옵션 대화 상자: 프로젝트 및 솔루션 \> 빌드 및 실행

이 대화 상자에서 동시에 빌드할 수 있는 C++ 또는 C# 프로젝트의 최대 개수, 특정 기본 빌드 동작 및 몇 가지 빌드 로그 설정을 지정할 수 있습니다. 이러한 옵션에 액세스하려면 **도구** > **옵션**을 선택하고 **프로젝트 및 솔루션**을 확장한 다음, **빌드 및 실행**을 선택합니다.

**최대 병렬 프로젝트 빌드 수**

동시에 빌드할 수 있는 C++ 및 C# 프로젝트의 최대 개수를 지정합니다. 빌드 프로세스를 최적화하기 위해 최대 병렬 프로젝트 빌드 수는 자동으로 컴퓨터의 CPU 수로 설정됩니다. 최대값은 32입니다.

**실행할 때 시작 프로젝트와 종속성만 빌드**

**F5** 키, **디버그** > **디버깅 시작** 메뉴 명령 또는 **빌드** 메뉴의 해당 명령을 사용할 때 시작 프로젝트와 해당 종속성만 빌드합니다. 선택 취소하면 모든 프로젝트와 종속성이 빌드됩니다.

**실행 시 프로젝트가 만료된 경우**

‘C++ 프로젝트에만 적용됩니다.’ 

**F5** 키 또는 **디버그** > **디버깅 시작** 명령을 사용하여 프로젝트를 실행할 때 기본 설정인 **빌드 여부 묻기**에서 프로젝트 구성이 만료된 경우 메시지가 표시됩니다. 실행될 때마다 프로젝트를 빌드하려면 **항상 빌드**를 선택합니다. 프로젝트를 실행할 때 모든 자동 빌드를 표시하지 않으려면 **빌드 안 함**을 선택합니다.

**실행 시 빌드 또는 배포 오류가 발생한 경우**

‘C++ 프로젝트에만 적용됩니다.’ 

**F5** 키 또는 **디버그** > **디버깅 시작** 명령을 사용하여 프로젝트를 실행할 때 기본 설정인 **시작 여부 묻기**에서 빌드에 실패해도 프로젝트를 실행해야 하는 경우 메시지가 표시됩니다. 마지막으로 성공한 빌드를 자동으로 시작하려면 **이전 버전 시작** 을 선택합니다. 그러면 실행 중인 코드와 소스 코드 간에 불일치가 발생할 수 있습니다. 메시지를 표시하지 않으려면 **시작하지 않음**을 선택합니다.

**새 솔루션에 대해 현재 선택한 프로젝트를 시작 프로젝트로 사용**

이 옵션을 설정하면 새 솔루션에서 현재 선택한 프로젝트를 시작 프로젝트로 사용합니다.

**MSBuild 프로젝트 빌드 출력의 자세한 정도**

**출력** 창에 표시할 빌드 프로세스 정보의 양을 결정합니다.

**MSBuild 프로젝트 빌드 로그 파일의 자세한 정도**

‘C++ 프로젝트에만 적용됩니다.’ 

*\\\<ProjectName>\Debug\\\<ProjectName>.log*에 있는 빌드 로그 파일에 작성되는 정보의 양을 결정합니다.

## <a name="see-also"></a>참조

- [컴파일 및 빌드](../../ide/compiling-and-building-in-visual-studio.md)
- [옵션 대화 상자, 프로젝트 및 솔루션](projects-and-solutions-options-dialog-box.md)
- [옵션 대화 상자, 프로젝트 및 솔루션, 웹 프로젝트](options-dialog-box-projects-and-solutions-web-projects.md)
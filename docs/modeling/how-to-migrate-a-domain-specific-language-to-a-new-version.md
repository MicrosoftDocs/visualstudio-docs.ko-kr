---
title: '방법: Domain-Specific 언어 프로젝트 마이그레이션'
description: 도메인 특정 언어 프로젝트를 최신 버전의 Visual Studio로 마이그레이션하는 방법에 대 한 정보를 제공 합니다.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: dacb13ef14768f4f59a414f6159bbea8d24c4de8
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "92298407"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>방법: 도메인별 언어를 새 버전으로 마이그레이션
도메인 특정 언어를 정의 하 고 사용 하는 프로젝트는 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] 와 함께 배포 된 버전에서로 마이그레이션할 수 있습니다 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 마이그레이션 도구는의 일부로 제공 됩니다 [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . 도구는 DSL 도구를 사용 하거나 정의 하는 Visual Studio 프로젝트 및 솔루션을 변환 합니다.

 마이그레이션 도구는 명시적으로 실행 해야 합니다. Visual Studio에서 솔루션을 열 때 자동으로 시작 되지 않습니다. 도구 및 자세한 지침 문서는 다음 경로에서 찾을 수 있습니다.

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>DSL 프로젝트를 마이그레이션하기 전에
 마이그레이션 도구는 Visual Studio 프로젝트 파일 (**.csproj**) 및 솔루션 파일 (**.sln**)을 수정 합니다.

#### <a name="to-prepare-projects-for-migration"></a>마이그레이션을 위해 프로젝트를 준비 합니다.

- **.Csproj** 및 **.sln** 파일을 쓸 수 있는지 확인 합니다. 소스 제어에서 사용 중인 경우 체크 아웃 되었는지 확인 합니다.

- 마이그레이션하려는 폴더의 복사본을 만듭니다.

## <a name="migrating-a-collection-of-projects"></a>프로젝트 컬렉션 마이그레이션

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL 프로젝트 및 솔루션을 Visual Studio 2010로 마이그레이션하려면

1. DSL 마이그레이션 도구를 시작 합니다.

   - Windows 탐색기 (또는 파일 탐색기)에서 도구를 두 번 클릭 하거나 명령 프롬프트에서 도구를 시작할 수 있습니다. 이 도구는 다음 위치에 있습니다.

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. 변환 하려는 솔루션과 프로젝트가 포함 된 폴더를 선택 합니다.

   - 도구 위쪽의 상자에 경로를 입력 하거나 **찾아보기**를 클릭 합니다.

     마이그레이션 도구는 Dsl을 정의 하거나 사용 하는 프로젝트 트리를 표시 합니다. 트리에는 **VisualStudio** 또는 **texttemplating** 어셈블리를 사용 하는 모든 프로젝트가 포함 되어 있습니다.

3. 프로젝트 트리를 검토 하 고 변환 하지 않으려는 프로젝트의 선택을 취소 합니다.

   - 프로젝트 또는 솔루션을 선택 하 여 도구에서 수행 하는 변경 내용 목록을 표시 합니다.

       > [!NOTE]
       > 폴더 이름 옆에 표시 되는 확인란은 아무런 영향을 주지 않습니다. 프로젝트 및 솔루션을 검사 하려면 폴더를 확장 해야 합니다.

4. 프로젝트를 변환 합니다.

   1. **변환**을 클릭 합니다.

        각 프로젝트 파일이 변환 되기 전에 _프로젝트_**.csproj** 복사본이**vs2008** _로 저장 됩니다._

        각 솔루션의 복사본 _solution_**. sln** 은**vs2008** _로 저장 됩니다._

   2. 보고 된 실패 한 변환을 조사 합니다.

        오류는 텍스트 창에 보고 됩니다. 또한 트리 뷰는 변환에 실패 한 각 노드에 빨간색 플래그를 표시 합니다. 노드를 클릭 하 여 해당 오류에 대 한 자세한 정보를 볼 수 있습니다.

5. 성공적으로 변환 된 프로젝트를 포함 하는 솔루션의 **모든 템플릿을 변환** 합니다.

   1. 솔루션을 엽니다.

   2. 솔루션 탐색기 머리글에서 **모든 템플릿 변환** 단추를 클릭 합니다.

       > [!NOTE]
       > 이 단계를 불필요 하 게 만들 수 있습니다. 자세한 내용은 [모든 템플릿 변환을 자동화 하는 방법](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))을 참조 하세요.

6. 변환 된 프로젝트에서 사용자 지정 코드를 업데이트 합니다.

   - 프로젝트 빌드를 시도 하 고 오류를 조사 합니다.

   - 디자이너를 테스트 합니다.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>참조

- [관련 블로그 게시물](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
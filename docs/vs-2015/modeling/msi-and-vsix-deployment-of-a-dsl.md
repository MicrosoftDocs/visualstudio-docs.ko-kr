---
title: DSL의 VSIX 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be9d3d44bfceaae1f2912086c3d20c90ce1e094b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916555"
---
# <a name="vsix-deployment-of-a-dsl"></a>DSL의 VSIX 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

도메인 특정 언어를 사용자의 컴퓨터 또는 다른 컴퓨터에 설치할 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 는 대상 컴퓨터에 이미 설치 되어 있어야 합니다.

## <a name="installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> VSX를 사용 하 여 DSL 설치 및 제거
 이 방법으로 DSL을 설치 하는 경우 사용자는 내에서 DSL 파일을 열 수 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 있지만 Windows 탐색기에서 파일을 열 수는 없습니다.

#### <a name="to-install-a-dsl-by-using-the-vsix"></a>VSIX를 사용 하 여 DSL을 설치 하려면

1. 컴퓨터에서 DSL 패키지 프로젝트를 통해 빌드된 **.vsix** 파일을 찾습니다.

    1. **솔루션 탐색기**에서 **dslpackage** 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **Windows 탐색기에서 폴더 열기**를 클릭 합니다.

    2. 파일 ** \\ \* bin \\ **_프로젝트_를 찾습니다 **. 패키지 vsix**

2. DSL을 설치할 대상 컴퓨터에 **.vsix** 파일을 복사 합니다. 이 컴퓨터는 사용 중인 컴퓨터이거나 다른 컴퓨터일 수 있습니다.

    - 대상 컴퓨터에는 런타임에 Dsl을 지 원하는 버전 중 하나가 있어야 합니다 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . 자세한 내용은 [지원 되는 Visual Studio 버전 시각화 & 모델링 SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)를 참조 하세요.

    - 대상 컴퓨터에 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **DslPackage\source.extensions.manifest**에 지정 된 버전 중 하나가 있어야 합니다.

3. 대상 컴퓨터에서 **.vsix** 파일을 두 번 클릭 합니다.

     **Visual Studio 확장 설치 관리자** 에서 확장을 열고 설치합니다.

4. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 시작하거나 다시 시작합니다.

5. DSL을 테스트 하려면를 사용 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 하 여 dsl에 대해 정의한 확장명이 있는 새 파일을 만듭니다.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX를 사용 하 여 설치 된 DSL을 제거 하려면

1. **도구** 메뉴에서 **확장 관리자**를 클릭 합니다.

2. **설치된 확장**을 확장합니다.

3. DSL이 정의 된 확장을 선택 하 고 **제거**를 클릭 합니다.

   드물게 결함이 있는 확장은 로드되지 않고 오류 창에 보고서를 생성하지만 확장 관리자에 나타나지 않습니다. 이 경우 다음 위치에서 파일을 삭제하여 확장을 제거할 수 있습니다.

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

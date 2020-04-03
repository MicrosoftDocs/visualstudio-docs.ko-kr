---
title: '방법: 빌드 로그 파일 보기, 저장 및 구성 | Microsoft Docs'
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84efda930066c4236fa4397fbadf287c6774fdb0
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472784"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>방법: 빌드 로그 파일 보기, 저장 및 구성

Visual Studio IDE에서 프로젝트를 빌드한 후에 **출력** 창에서 해당 빌드에 대한 정보를 볼 수 있습니다. 예를 들어 이 정보를 사용하여 빌드 실패를 해결할 수 있습니다.

- C++ 프로젝트의 경우 프로젝트를 빌드할 때 생성되고 저장되는 로그 파일에서도 동일한 정보를 볼 수 있습니다. 

- 관리 코드 프로젝트의 경우 빌드 출력 창 안을 클릭하고 **Ctrl**+**S**를 누를 수 있습니다. Visual Studio에서 **출력** 창의 정보를 로그 파일로 저장할 위치를 묻는 메시지가 표시됩니다.

또한 IDE를 사용하여 각 빌드에 대해 보려는 어떤 종류의 정보를 지정할 수 있습니다.

MSBuild를 사용하여 종류를 불문하고 프로젝트를 빌드하는 경우 로그 파일을 만들어 빌드에 대한 정보를 저장할 수 있습니다. 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)를 참조하세요.

## <a name="to-view-the-build-log-file-for-a-c-project"></a>C++ 프로젝트에 대한 빌드 로그 파일을 보려면

1. **Windows 탐색기** 또는 **파일 탐색기**에서 다음 파일을 엽니다(프로젝트 루트 폴더에 상대적인 경로). *릴리스*\\<ProjectName>\>.Log* 또는 *Debug\\<프로젝트 이름\>.log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>관리 코드 프로젝트에 빌드 로그 파일을 만들려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

2. **출력** 창에서 텍스트의 아무 곳이나 클릭합니다.

3. **Ctrl**+**S**를 누릅니다.

   Visual Studio에서 빌드 출력을 저장할 위치를 묻는 메시지가 표시됩니다.

`-fileLogger`(`-fl`) 명령줄 옵션을 사용하여 명령 줄에서 직접 MSBuild를 실행하여 로그를 생성할 수도 있습니다. [MSBuild를 사용하여 빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)를 참조하세요.

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>빌드 로그에 포함되는 정보의 양을 변경하려면

1. 메뉴 모음에서 **도구** > **옵션**을 차례로 선택합니다.

2. **프로젝트 및 솔루션** 페이지에서 **빌드 및 실행** 페이지를 선택합니다.

3. **MSBuild 프로젝트 빌드 출력 세부 정보 표시** 목록에서 다음 값 중 하나를 선택하고 **확인** 단추를 선택합니다.

    |세부 정보 표시 수준|Description|
    | - |-----------------|
    |**자동**|빌드의 요약만을 표시합니다.|
    |**최소**|매우 중요한 항목으로 분류된 빌드 및 오류, 경고 및 메시지의 요약을 표시합니다.|
    |**보통**|매우 중요한 항목으로 분류된 빌드 및 오류, 경고 및 메시지의 요약, 빌드의 주요 단계를 표시합니다. 이 수준의 세부 정보를 가장 자주 사용합니다.|
    |**자세히**|매우 중요한 항목으로 분류된 빌드 및 오류, 경고 및 메시지의 요약, 빌드의 모든 단계, 보통 중요한 항목으로 분류된 메시지를 표시합니다.|
    |**진단**|빌드에 사용할 수 있는 모든 데이터를 표시합니다. 이 수준의 세부 정보를 사용하여 사용자 지정 빌드 스크립트 및 기타 빌드 문제를 포함한 문제를 디버깅할 수 있습니다.|

     자세한 내용은 [옵션 대화 상자, 프로젝트 및 솔루션, 빌드 및 실행](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) 및 <xref:Microsoft.Build.Framework.LoggerVerbosity>를 참조하세요.

    > [!IMPORTANT]
    > **출력** 창(모든 프로젝트) 및 *\<ProjectName>.txt* 파일(C++ 프로젝트에만 해당)에 적용할 변경 내용에 대한 프로젝트를 다시 빌드해야 합니다.

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>큰 로그 파일을 더욱 쉽게 찾아볼 수 있도록 이진 로그 사용

이진 로그는 .NET 프로젝트의 선택적 기능으로, 큰 로그에서 정보를 쉽게 찾을 수도 있는 풍부한 로그 탐색 환경을 제공합니다. 이진 로그를 사용하려면 [프로젝트 시스템 도구](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools)를 설치합니다. 자세한 내용은 [https://msbuildlog.com](https://msbuildlog.com) 및 [이진 로그](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 프로젝트 및 솔루션 빌드 및 정리](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)

---
title: '방법: 빌드 로그 파일 보기, 저장 및 구성 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffc1c620136c55c42f3468129ed164075d762bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670503"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>방법: 빌드 로그 파일 보기, 저장 및 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio IDE에서 프로젝트를 빌드한 후에 **출력** 창에서 해당 빌드에 대한 정보를 볼 수 있습니다. 예를 들어 이 정보를 사용하여 빌드 실패를 해결할 수 있습니다. C++ 프로젝트의 경우 자동으로 만들고 저장된 .txt 파일에서도 동일한 정보를 볼 수 있습니다. 관리 코드 프로젝트의 경우 **출력** 창에서 .txt 파일로 정보를 복사하고 붙여넣은 다음, 직접 저장할 수 있습니다. 또한 IDE를 사용하여 각 빌드에 대해 보려는 어떤 종류의 정보를 지정할 수 있습니다.

 MSBuild를 사용하여 모든 종류의 프로젝트를 빌드하는 경우 .txt 파일을 만들어 빌드에 대한 정보를 저장할 수 있습니다. 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md)를 참조하세요.

### <a name="to-view-the-build-log-file-for-a-c-project"></a>C++ 프로젝트에 대한 빌드 로그 파일을 보려면

1. **Windows 탐색기** 또는 **파일 탐색기**에서 다음 파일을 엽니다 \\ .. ..\Visual Studio *버전*\projects \\ *projectname* \\ *projectname*\Debug \\ *projectname*.txt

### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>관리 코드 프로젝트에 빌드 로그 파일을 만들려면

1. 메뉴 모음에서 **빌드**, **솔루션 빌드**를 선택합니다.

2. **출력** 창에서 빌드의 정보를 강조 표시 한 다음 클립보드에 복사 합니다.

3. 메모장과 같은 텍스트 편집기를 열고 정보를 파일에 붙여넣은 다음 저장합니다.

### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>빌드 로그에 포함되는 정보의 양을 변경하려면

1. 메뉴 모음에서 **도구**, **옵션**을 선택 합니다.

2. **프로젝트 및 솔루션** 페이지에서 **빌드 및 실행** 페이지를 선택합니다.

3. **MSBuild 프로젝트 빌드 출력 세부 정보 표시** 목록에서 다음 값 중 하나를 선택하고 **확인** 단추를 선택합니다.

    |세부 정보 표시 수준|설명|
    |---------------------|-----------------|
    |Quiet|빌드의 요약만을 표시합니다.|
    |최소|매우 중요한 항목으로 분류된 빌드 및 오류, 경고 및 메시지의 요약을 표시합니다.|
    |보통|매우 중요한 항목으로 분류된 빌드 및 오류, 경고 및 메시지의 요약, 빌드의 주요 단계를 표시합니다. 이 수준의 세부 정보를 가장 자주 사용합니다.|
    |자세히|매우 중요한 항목으로 분류된 빌드 및 오류, 경고 및 메시지의 요약, 빌드의 모든 단계, 보통 중요한 항목으로 분류된 메시지를 표시합니다.|
    |진단|빌드에 사용할 수 있는 모든 데이터를 표시합니다. 이 수준의 세부 정보를 사용하여 사용자 지정 빌드 스크립트 및 기타 빌드 문제를 포함한 문제를 디버깅할 수 있습니다.|

     자세한 내용은 [옵션 대화 상자, 프로젝트 및 솔루션, 빌드 및 실행](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) 및를 참조 하세요 <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > **출력** 창 (모든 프로젝트) 및 *ProjectName*.Txt 파일 (c + + 프로젝트에만 해당)에 변경 내용을 적용 하려면 프로젝트를 다시 빌드해야 합니다.

## <a name="see-also"></a>관련 항목
 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md) [Visual Studio에서 프로젝트 및 솔루션 빌드 및 정리](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)

---
title: 빌드 전 이벤트/빌드 후 이벤트 명령줄 대화 상자
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEventsBuilder
- vb.ProjectPropertiesBuildEventsBuilder
helpviewer_keywords:
- $(SolutionExt)
- $(ProjectDir)
- $(TargetPath)
- $(ProjectExt)
- $(TargetFileName)
- $(PlatformName)
- $(SolutionName)
- macros, build events
- $(SolutionPath)
- $(ProjectPath)
- $(ProjectFileName)
- $(DevEnvDir)
- $(TargetName)
- $(TargetDir)
- $(SolutionDir)
- $(TargetExt)
- $(OutDir)
- $(ConfigurationName)
- $(SolutionFileName)
- $(ProjectName)
- build events, macros
ms.assetid: d49b2c57-24bf-4fb2-8351-5c4b6cca938f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a9ec2acb6802c19b48ba6254fb0a8812935d400
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038363"
---
# <a name="pre-build-eventpost-build-event-command-line-dialog-box"></a>빌드 전 이벤트/빌드 후 이벤트 명령줄 대화 상자

편집 상자에서 직접 [빌드 이벤트 페이지, 프로젝트 디자이너(C#)](../../ide/reference/build-events-page-project-designer-csharp.md)에 대한 빌드 전후 이벤트를 입력할 수 있습니다. 또는 사용 가능한 매크로 목록에서 빌드 전후 매크로를 선택할 수 있습니다.

> [!NOTE]
> 프로젝트가 최신 상태이고 빌드가 트리거되지 않으면 빌드 전 이벤트가 실행되지 않습니다.

## <a name="ui-element-list"></a>UI 요소 목록

**명령줄 편집 상자**

빌드 전 또는 빌드 후에 실행할 이벤트를 포함합니다.

> [!NOTE]
> .bat 파일을 실행하는 모든 빌드 후 이벤트 명령 앞에 `call` 문을 추가합니다. 예를 들어 `call C:\MyFile.bat` 또는 `call C:\MyFile.bat call C:\MyFile2.bat`입니다.

**매크로**

입력란을 확장하여 명령줄 편집 상자에 삽입할 매크로의 목록을 표시합니다.

**매크로 테이블**

사용 가능한 매크로 및 해당 값을 나열합니다. 각각에 대한 설명은 아래 매크로를 참조하세요. 한 번에 명령줄 편집 상자에 삽입할 하나의 매크로만을 선택할 수 있습니다.

**삽입**

매크로 테이블에서 선택된 매크로를 명령줄 편집 상자에 삽입합니다.

### <a name="macros"></a>Macros

이 매크로 중 하나를 사용하여 파일 위치를 지정하거나 여러 개를 선택한 경우 입력 파일의 실제 이름을 가져올 수 있습니다. 이러한 매크로는 대/소문자를 구분하지 않습니다.

|매크로|Description|
|-----------|-----------------|
|`$(ConfigurationName)`|현재 프로젝트 구성의 이름(예: "디버그")입니다.|
|`$(OutDir)`|프로젝트 디렉터리를 기준으로 하는 출력 파일 디렉터리에 대한 경로입니다. 출력 디렉토리 속성에 대한 값으로 확인됩니다. 뒤에 백슬래시 '\\'를 포함합니다.|
|`$(DevEnvDir)`|Visual Studio의 설치 디렉터리(드라이브 및 경로로 정의됨)이며 뒤에 백슬래시 '\\'를 포함합니다.|
|`$(PlatformName)`|현재 대상 플랫폼의 이름입니다. 예: "AnyCPU".|
|`$(ProjectDir)`|프로젝트의 디렉터리(드라이브 및 경로로 정의됨)이며, 뒤에 백슬래시 '\\'를 포함합니다.|
|`$(ProjectPath)`|프로젝트의 절대 경로 이름(드라이브, 경로, 기본 이름 및 파일 확장명으로 정의됨)입니다.|
|`$(ProjectName)`|프로젝트의 기본 이름입니다.|
|`$(ProjectFileName)`|프로젝트의 파일 이름(기본 이름 및 파일 확장명으로 정의됨)입니다.|
|`$(ProjectExt)`|프로젝트의 파일 확장명입니다. 파일 확장명 앞에 '.'을 포함합니다.|
|`$(SolutionDir)`|솔루션의 디렉터리(드라이브 및 경로로 정의됨)이며, 뒤에 백슬래시 '\\'를 포함합니다.|
|`$(SolutionPath)`|솔루션의 절대 경로 이름(드라이브, 경로, 기본 이름 및 파일 확장명으로 정의됨)입니다.|
|`$(SolutionName)`|솔루션의 기본 이름입니다.|
|`$(SolutionFileName)`|솔루션의 파일 이름(기본 이름 및 파일 확장명으로 정의됨)입니다.|
|`$(SolutionExt)`|솔루션의 파일 확장명입니다. 파일 확장명 앞에 '.'을 포함합니다.|
|`$(TargetDir)`|빌드에 대한 기본 출력 파일의 디렉터리(드라이브 및 경로로 정의됨)입니다. 뒤에 백슬래시 '\\'를 포함합니다.|
|`$(TargetPath)`|빌드에 대한 기본 출력 파일의 절대 경로 이름(드라이브, 경로, 기본 이름 및 파일 확장명으로 정의됨)입니다.|
|`$(TargetName)`|빌드에 대한 기본 출력 파일의 기본 이름입니다.|
|`$(TargetFileName)`|빌드에 대한 기본 출력 파일의 파일 이름(기본 이름 및 파일 확장명으로 정의됨)입니다.|
|`$(TargetExt)`|빌드에 대한 기본 출력 파일의 파일 확장명입니다. 파일 확장명 앞에 '.'을 포함합니다.|

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 사용자 지정 빌드 이벤트 지정](../../ide/specifying-custom-build-events-in-visual-studio.md)
- [프로젝트 디자이너, 빌드 이벤트 페이지(C#)](../../ide/reference/build-events-page-project-designer-csharp.md)
- [방법: 빌드 이벤트 지정(Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [방법: 빌드 이벤트 지정(C#)](../../ide/how-to-specify-build-events-csharp.md)

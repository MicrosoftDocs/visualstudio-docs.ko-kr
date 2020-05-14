---
title: 기타 파일
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], miscellaneous
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793500faf217c74772506b4b7394d926447ffd40
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585299"
---
# <a name="miscellaneous-files"></a>기타 파일

Visual Studio 편집기를 사용하여 프로젝트 또는 솔루션의 파일에 대해 개별적으로 작업을 수행할 수 있습니다. 솔루션이 열려 있는 동안 솔루션 또는 프로젝트에 추가하지 않고 파일을 열고 수정할 수 있습니다. 개별적으로 작업하려는 파일을 기타 파일이라고 합니다. 기타 파일은 솔루션 및 프로젝트 외부에 있고, 빌드에 포함되지 않으며, 소스 제어 솔루션에 포함할 수 없습니다.

프로젝트 또는 솔루션에서 개별적으로 파일을 열면 여러 가지 이유로 유용합니다. 프로젝트 기반 솔루션을 개발하는 동안 보고 싶지만 솔루션 개발에 필수는 아닌 파일이 있을 수 있습니다. 일반적인 예로 개발 메모 또는 지침, 데이터베이스 스키마 및 코드 클립이 있습니다. 또한 독립 실행형 파일을 만들 수도 있습니다.

![솔루션 프로젝트](../../ide/reference/media/projects_solutions_misc.gif)

폴더에 대한 옵션이 사용되는 경우 솔루션 탐색기에 **기타 파일** 폴더가 표시될 수 있습니다. [옵션 대화 상자, 환경, 문서](../../ide/reference/documents-environment-options-dialog-box.md)에서 옵션을 설정할 수 있습니다. 특정 솔루션이나 프로젝트에도 옵션을 사용하지 않을 경우 기타 파일을 닫으면 해당 솔루션이나 프로젝트와는 연결되지 않습니다.

**기타 파일** 폴더는 파일을 링크로 나타냅니다. 이 폴더는 솔루션에 포함되지 않지만 솔루션을 열 때 폴더에 대한 설정에 따라 솔루션을 마지막으로 닫을 때 열려 있던 기타 파일 중 일부 또는 모두가 다시 열립니다.

> [!NOTE]
> **기타 파일** 폴더에 나타나지 않는 일부 파일은 IDE 내에서 수정할 수 없는 파일(예: .zip 파일, .doc 파일)입니다. IDE는 외부 편집기를 통해서만 수정할 수 있는 파일을 추적하지 않습니다.

## <a name="commands-available-in-the-ide"></a>IDE에서 사용할 수 있는 명령

메뉴, 도구 모음 및 포함된 명령은 여는 파일의 형식에 따라 변경됩니다. 예를 들어 텍스트 파일을 여는 경우 텍스트 편집기 도구 모음이 나타나고 해당 명령을 사용할 수 있습니다. XML 스키마 파일을 여는 경우 XML 스키마 도구 모음이 나타납니다. XML 스키마를 편집하는 동안 텍스트 편집기 도구 모음의 명령(또는 도구 모음 자체)은 사용할 수 없습니다. XML 스키마는 활성 창이므로 현재 선택 영역 컨텍스트가 있습니다. 프로젝트 파일과 기타 파일 간에 전환하는 경우 모든 프로젝트 관련 명령이 사라지고 기타 파일과 직접 관련된 명령만 나타납니다.

## <a name="folder-display-options"></a>폴더 표시 옵션

기타 파일을 열지 않은 경우에도 폴더가 나타나도록 **기타 파일** 폴더에 대한 표시 옵션을 설정할 수 있습니다. 솔루션 파일은 기타 파일 목록을 영구적으로 관리하지 않습니다. 사용자 단위 MRU(가장 최근에 사용한) 파일 목록을 저장할 수 있는 선택적 기능을 사용합니다.

## <a name="see-also"></a>참고 항목

- [프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [솔루션 및 프로젝트](../../ide/solutions-and-projects-in-visual-studio.md)
- [옵션 대화 상자, 환경, 문서](../../ide/reference/documents-environment-options-dialog-box.md)

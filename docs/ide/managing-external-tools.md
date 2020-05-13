---
title: 외부 도구 관리
ms.date: 11/20/2017
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0f22c687f88c7736d5c088ebc28ff490c4c16b8f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591296"
---
# <a name="manage-external-tools"></a>외부 도구 관리

**도구** 메뉴를 사용하여 Visual Studio 내에서 외부 도구를 호출할 수 있습니다. 몇 가지 기본 도구는 **도구** 메뉴에서 사용할 수 있으며, 원하는 다른 실행 파일을 추가하여 메뉴를 사용자 지정할 수 있습니다.

## <a name="tools-available-on-the-tools-menu"></a>도구 메뉴에서 사용할 수 있는 도구

**도구** 메뉴에는 다음과 같은 몇 가지 기본 제공 명령이 포함되어 있습니다.

::: moniker range="vs-2017"

* [Visual Studio 확장 관리](finding-and-using-visual-studio-extensions.md)를 위한 **확장 및 업데이트**
* [코드 조각 구성을 위한](code-snippets.md)**코드 조각 관리자**
* [메뉴 및 도구 모음 사용자 지정](how-to-customize-menus-and-toolbars-in-visual-studio.md)을 위한 **사용자 지정**
* [Visual Studio IDE 및 기타 도구에 대한 다양한 옵션 설정](reference/options-dialog-box-visual-studio.md)을 위한 **옵션**

::: moniker-end

::: moniker range=">=vs-2019"

* [코드 조각 구성을 위한](code-snippets.md)**코드 조각 관리자**
* [메뉴 및 도구 모음 사용자 지정](how-to-customize-menus-and-toolbars-in-visual-studio.md)을 위한 **사용자 지정**
* [Visual Studio IDE 및 기타 도구에 대한 다양한 옵션 설정](reference/options-dialog-box-visual-studio.md)을 위한 **옵션**

::: moniker-end

## <a name="add-new-tools-to-the-tools-menu"></a>도구 메뉴에 새 도구 추가

**도구** 메뉴에 표시할 외부 도구를 추가할 수 있습니다.

1. **도구** > **외부 도구**를 선택하여 **외부 도구** 대화 상자를 엽니다.

1. **추가**를 클릭한 다음 정보를 입력합니다. 예를 들어 다음 항목은 현재 Visual Studio에서 열려 있는 파일의 디렉터리를 **Windows 탐색기**에서 엽니다.

   * 제목: `Open File Location`

   * 명령: `explorer.exe`

   * 인수: `/root, "$(ItemDir)"`

   ![외부 도구 대화 상자](media/external-tools-dialog.png)

다음은 외부 도구를 정의할 때 사용할 수 있는 전체 인수 목록입니다.

|이름|인수|설명|
|----------|--------------|-----------------|
|항목 경로|$(ItemPath)|현재 파일의 전체 파일 이름(드라이브 + 경로 + 파일 이름)입니다.|
|항목 디렉터리|$(ItemDir)|현재 파일의 디렉터리(드라이브 + 경로)입니다.|
|항목 파일 이름|$(ItemFilename)|현재 파일의 파일 이름(파일 이름)입니다.|
|항목 확장명|$(ItemExt)|현재 파일의 파일 이름 확장명입니다.|
|현재 줄|$(CurLine)|코드 창 커서의 현재 줄 위치입니다.|
|현재 열|$(CurCol)|코드 창 커서의 현재 열 위치입니다.|
|현재 텍스트|$(CurText)|선택한 텍스트입니다.|
|대상 경로|$(Targetpath)|빌드할 항목의 전체 파일 이름(드라이브 + 경로 + 파일 이름)입니다.|
|대상 디렉터리|$(Targetdir)|빌드할 항목의 디렉터리입니다.|
|대상 이름|$(Targetname)|빌드할 항목의 파일 이름입니다.|
|대상 확장명|$ (Targetext)|빌드할 항목의 파일 이름 확장명입니다.|
|이진 디렉터리|$(BinDir)|빌드 중인 이진의 최종 위치(드라이브 + 경로)입니다.|
|프로젝트 디렉터리|$(ProjectDir)|현재 프로젝트의 디렉터리(드라이브 + 경로)입니다.|
|프로젝트 파일 이름|$(ProjectFileName)|현재 프로젝트의 파일 이름(드라이브 + 경로 + 파일 이름)입니다.|
|솔루션 디렉터리|$(Solutiondir)|현재 솔루션의 디렉터리(드라이브 + 경로)입니다.|
|솔루션 파일 이름|$(SolutionFileName)|현재 솔루션의 파일 이름(드라이브 + 경로 + 파일 이름)입니다.|

> [!NOTE]
> IDE 상태 표시줄에는 활성 **코드 편집기**에서 삽입 지점 위치를 나타내기 위해 **현재 줄**과 **현재 열** 변수가 표시됩니다. **현재 텍스트** 변수는 해당 위치에서 선택한 코드 또는 텍스트를 반환합니다.

## <a name="see-also"></a>참조

- [C/C++ 빌드 도구](/cpp/build/reference/c-cpp-build-tools)

---
title: VSIX 프로젝트 템플릿 시작 하기 | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ca9672b22120718f63638d8668812d0e42e41f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905883"
---
# <a name="get-started-with-the-vsix-project-template"></a>VSIX 프로젝트 템플릿 시작

VSIX 프로젝트 템플릿을 사용 하 여 확장을 만들거나 배포를 위한 기존 확장을 패키지할 수 있습니다. VSIX 프로젝트 템플릿에는 Visual Basic 및 Visual c # 버전이 모두 있으며 Visual Studio SDK의 일부로 설치 됩니다.

 VSIX 프로젝트 템플릿은 제공 된 확장 및 자산에 대 한 정보를 포함 하는 *source.extension.vsixmanifest* 파일로 구성 됩니다.

 VSIX 프로젝트 템플릿을 찾으려면 Visual Studio SDK를 설치 해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>VSIX 프로젝트 템플릿을 사용 하 여 사용자 지정 프로젝트 템플릿 배포

 다음 단계에서는 VSIX 프로젝트를 사용 하 여 다른 개발자와 공유할 수 있는 프로젝트 템플릿을 패키지 하거나 Visual Studio 갤러리에 업로드 하는 방법을 보여 줍니다.

1. 프로젝트 템플릿을 만듭니다.

    1. 템플릿을 만들 프로젝트를 엽니다. 이 프로젝트는 모든 프로젝트 형식일 수 있습니다.

    2. **프로젝트** 메뉴에서 **템플릿 내보내기**를 클릭합니다. 마법사의 단계를 완료 합니다.

         *.Zip* 파일은 *%USERPROFILE%\My Documents\visual Studio {Version} \My 내보내진 템플릿에서 \\ *생성 됩니다.

2. 빈 VSIX 프로젝트를 만듭니다.

     **파일** > **새로 만들기** > **프로젝트**를 선택합니다. 검색 상자에 "vsix"를 입력 하 고 **c #** 또는 **Visual Basic** 버전의 **vsix 프로젝트**를 선택 합니다.

3. 프로젝트에 *.zip* 파일을 추가 합니다. **출력 디렉터리로 복사** 속성을로 설정 `Copy Always` 합니다.

4. **솔루션 탐색기**에서 *source.extension.vsixmanifest* 파일을 두 번 클릭 하 여 **VSIX 매니페스트 디자이너**에서 연 후 다음과 같이 변경 합니다.

    - **제품 이름** 필드를 **내 프로젝트 템플릿으로**설정 합니다.

    - **PRODUCT ID** 필드를 **myprojecttemplate-1**로 설정 합니다.

    - **Author** 필드를 **Fabrikam**으로 설정 합니다.

    - **설명** 필드를 **내 프로젝트 템플릿으로**설정 합니다.

    - **자산** 섹션에서 **VisualStudio** 형식을 추가 하 고 해당 경로를 *.zip* 파일의 이름으로 설정 합니다.

5. *Source.extension.vsixmanifest* 파일을 저장 하 고 닫습니다.

6. 프로젝트를 빌드합니다.

7. 출력 디렉터리에서 *.vsix* 파일을 두 번 클릭 합니다.

8. **VSIX 설치 관리자** 메시지 상자가 나타납니다. 지침에 따라 확장을 설치 합니다.

9. Visual Studio를 종료한 다음 다시 엽니다.

::: moniker range="vs-2017"

10. **도구** 메뉴에서 **확장 및 업데이트** 를 선택 하 고 **템플릿** 범주를 선택 합니다. 사용 가능한 확장 중 하나는 **내 프로젝트 템플릿**이어야 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

10. 확장 관리 **메뉴에서** **확장 관리** 를 선택 하 고 **템플릿** 범주를 선택 합니다. 사용 가능한 확장 중 하나는 **내 프로젝트 템플릿**이어야 합니다.

::: moniker-end

11. 새 프로젝트 템플릿이 원본 프로젝트 템플릿과 동일한 위치의 **새** 프로젝트 대화 상자에 나타납니다. 예를 들어 Visual Basic 콘솔 응용 프로그램에서 **Vb console** 이라는 템플릿을 만든 경우 **vb 콘솔** 은 Visual Basic **콘솔 응용 프로그램** 템플릿과 동일한 창에 표시 됩니다.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에서 템플릿의 위치를 지정 하려면

1. 템플릿 폴더는 *{Visual Studio 설치 경로} \Common7\IDE\ProjectTemplates* 및 *{Visual studio 설치 경로} \Common7\IDE\ItemTemplates* 디렉터리에 있습니다. **새 프로젝트** 대화 상자의 최상위 섹션 이름이 템플릿 폴더의 이름과 정확 하 게 일치 하지 않습니다. 서로 다른 위치에서 템플릿 폴더의 이름을 사용 합니다.

    *.Vsix* 파일 확장명을 *.zip*으로 변경한 다음 파일을 엽니다.

2. **새 프로젝트** 대화 상자의 섹션과 같은 이름으로 새 폴더를 만듭니다.

3. 템플릿이 하위 섹션에 표시 되는 경우 동일한 이름의 하위 폴더를 만듭니다.

4. 템플릿 *.zip* 파일을 새 폴더로 이동 합니다.

5. *.Zip* 확장명을 *.vsix*로 변경 합니다.

6. VSIX 매니페스트를 엽니다.

7. VSIX 매니페스트에서 템플릿 파일을 포함 하는 디렉터리 트리의 루트를 가리키도록 템플릿의 **자산** 경로를 업데이트 합니다. 예를 들어 템플릿이 *\CSharp\Windows*에 있는 경우 참조는 *\csharp*를 가리켜야 합니다.

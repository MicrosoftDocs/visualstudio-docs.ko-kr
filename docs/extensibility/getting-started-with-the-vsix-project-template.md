---
title: VSIX 프로젝트 템플릿 시작하기 | 마이크로 소프트 문서
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711242"
---
# <a name="get-started-with-the-vsix-project-template"></a>VSIX 프로젝트 템플릿 시작

VSIX 프로젝트 템플릿을 사용하여 확장을 만들거나 배포를 위해 기존 확장을 패키징할 수 있습니다. VSIX 프로젝트 템플릿에는 Visual Basic 및 Visual C# 버전이 모두 있으며 Visual Studio SDK의 일부로 설치됩니다.

 VSIX 프로젝트 템플릿은 제공 되는 확장및 자산에 대한 정보가 들어있는 *source.extension.vsixmanifest* 파일로 구성됩니다.

 VSIX 프로젝트 템플릿을 찾으려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>VSIX 프로젝트 템플릿을 사용하여 사용자 지정 프로젝트 템플릿 배포

 다음 단계에서는 VSIX 프로젝트를 사용하여 다른 개발자와 공유하거나 Visual Studio 갤러리에 업로드할 수 있는 프로젝트 템플릿을 패키징하는 방법을 보여 준다.

1. 프로젝트 템플릿을 만듭니다.

    1. 템플릿을 만들 프로젝트를 엽니다. 이 프로젝트는 모든 프로젝트 유형일 수 있습니다.

    2. **프로젝트** 메뉴에서 **템플릿 내보내기**를 클릭합니다. 마법사의 단계를 완료합니다.

         *.zip* 파일은 *%USERPROFILE%\내 문서\비주얼 스튜디오 {버전}\내보낸\\템플릿에서*만들어집니다.

2. 빈 VSIX 프로젝트를 만듭니다.

     **File** > **New**새 > **프로젝트**파일 선택 . 검색 상자에서 "vsix"를 입력하고 **VSIX 프로젝트의** **C#** 또는 **시각적 기본** 버전을 선택합니다.

3. 프로젝트에 *.zip* 파일을 추가합니다. 출력 **디렉터리 속성으로 복사를** 설정합니다. `Copy Always`

4. **솔루션 탐색기에서** *source.extension.vsixmanifest* 파일을 두 번 클릭하여 **VSIX 매니페스트 디자이너에서**열고 다음을 변경합니다.

    - 제품 **이름** 필드를 **내 프로젝트 템플릿으로**설정합니다.

    - 제품 **ID** 필드를 **MyProjectTemplate - 1로**설정합니다.

    - **작성자** 필드를 **Fabrikam으로**설정합니다.

    - **설명** 필드를 **내 프로젝트 템플릿으로**설정합니다.

    - **자산** 섹션에서 **Microsoft.VisualStudio.ProjectTemplate** 유형을 추가하고 *.zip* 파일의 이름으로 경로를 설정합니다.

5. *source.extension.vsixmanifest* 파일을 저장하고 닫습니다.

6. 프로젝트를 빌드합니다.

7. 출력 디렉토리에서 *.vsix* 파일을 두 번 클릭합니다.

8. **VSIX 설치 관리자** 메시지 상자가 나타납니다. 지침에 따라 확장을 설치합니다.

9. Visual Studio를 종료한 다음 다시 엽니다.

::: moniker range="vs-2017"

10. **도구** 메뉴에서 **확장 및 업데이트를** 선택하고 템플릿 **범주를 선택합니다.** 사용 가능한 확장 중 하나는 **내 프로젝트 템플릿이어야**합니다.

::: moniker-end

::: moniker range=">=vs-2019"

10. **확장(확장** **메뉴에서)에서 확장 관리를** 선택하고 **템플릿 범주를 선택합니다.** 사용 가능한 확장 중 하나는 **내 프로젝트 템플릿이어야**합니다.

::: moniker-end

11. 새 프로젝트 템플릿은 원래 프로젝트 템플릿과 동일한 위치에 **새 프로젝트** 대화 상자에 나타납니다. 예를 들어 Visual Basic 콘솔 응용 프로그램에서 **VB 콘솔이라는** 템플릿을 만든 경우 **VB 콘솔은** Visual Basic **Console 응용 프로그램** 템플릿과 동일한 창에 나타납니다.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>새 프로젝트 대화 상자에서 템플릿의 위치를 지정하려면

1. 템플릿 폴더는 *{Visual Studio 설치 경로}\Common7\IDE\프로젝트 템플릿* 및 *{시각적 스튜디오 설치 경로}\Common7\IDE\ItemTemplate디렉터리에* 있습니다. **새 프로젝트** 대화 상자의 최상위 섹션 이름이 템플릿 폴더의 이름과 정확히 일치하지 않습니다. 서로 다른 경우 템플릿 폴더의 이름을 사용합니다.

    *.vsix* 파일 확장문을 *.zip으로*변경한 다음 파일을 엽니다.

2. 템플릿이 표시되어야 하는 **새 프로젝트** 대화 상자의 섹션과 이름이 같은 새 폴더를 만듭니다.

3. 템플릿이 하위 섹션에 표시되는 경우 동일한 이름의 하위 폴더를 만듭니다.

4. 템플릿 *.zip* 파일을 새 폴더로 이동합니다.

5. *.zip* 확장을 *.v6로*변경합니다.

6. VSIX 매니페스트를 엽니다.

7. VSIX 매니페스트에서 템플릿의 **자산** 경로를 업데이트하여 템플릿 파일이 포함된 디렉터리 트리의 루트를 가리킵니다. 예를 들어 템플릿이 *\CSharp\Windows에*있는 경우 참조는 *\CSharp*를 가리킬 것입니다.

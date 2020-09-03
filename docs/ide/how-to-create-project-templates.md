---
title: 프로젝트 템플릿 만들기
ms.date: 01/02/2018
ms.topic: how-to
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e6f168244971a348cdb7938af463538d0fa2acaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284388"
---
# <a name="how-to-create-project-templates"></a>방법: 프로젝트 템플릿 만들기

이 항목에서는 템플릿을 *.zip* 파일로 패키징하는 **템플릿 내보내기 마법사**를 사용하여 템플릿을 만드는 방법을 보여줍니다.

## <a name="use-the-export-template-wizard"></a>템플릿 내보내기 마법사 사용

1. 프로젝트를 만듭니다.

    > [!NOTE]
    > 템플릿의 소스로 사용할 프로젝트의 이름을 지정할 때 유효한 식별자 문자만 사용하세요. 그렇지 않은 경우 템플릿에서 생성된 프로젝트에 컴파일 오류가 발생할 수 있습니다. 유효한 식별자 문자에 대한 자세한 내용은 [선언 요소 이름(Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) 또는 [식별자(C++)](/cpp/cpp/identifiers-cpp)를 참조하세요. 또는 [템플릿 매개 변수](../ide/template-parameters.md)를 사용하여 클래스 및 네임스페이스에 "안전한" 이름을 사용할 수 있습니다.

2. 템플릿으로 내보낼 준비가 될 때까지 프로젝트를 편집합니다. 예를 들어 매개 변수를 대체해야 하는 위치를 나타내도록 코드 파일을 편집할 수 있습니다. [방법: 템플릿 매개 변수 대체](../ide/how-to-substitute-parameters-in-a-template.md)를 참조하세요.

3. **프로젝트** 메뉴에서 **템플릿 내보내기**를 선택합니다.

   **템플릿 내보내기 마법사**가 열립니다.

4. **템플릿 형식 선택** 페이지에서 **프로젝트 템플릿**을 선택합니다. 템플릿으로 내보낼 프로젝트를 선택한 후 **다음**을 선택합니다.

::: moniker range="vs-2017"

5. **템플릿 옵션 선택** 페이지에서 템플릿의 이름 및 설명(옵션), 아이콘 및 미리 보기 이미지를 입력합니다. 이러한 항목은 **새 프로젝트** 대화 상자에 나타납니다. **마침**을 선택합니다.

   프로젝트는 *.zip* 파일로 내보내고 지정된 출력 위치에 배치되며 선택할 경우 Visual Studio로 가져옵니다.

**새 프로젝트** 대화 상자에서 템플릿을 찾고 **설치됨**을 확장한 후 *.vstemplate* 파일의 `ProjectType` 요소에 해당하는 범주를 확장합니다. 예를 들어 `<ProjectType>CSharp</ProjectType>`을 포함하는 *.vstemplate* 파일은 기본적으로 **설치됨** > **Visual C#** 아래에 나타납니다. 해당 디렉터리에 폴더를 만들고 그 안에 템플릿의 *.zip* 파일을 추가하여 프로젝트 형식의 하위 디렉터리에 템플릿을 구성할 수 있습니다. 자세한 내용은 [방법: 템플릿 찾기 및 구성](../ide/how-to-locate-and-organize-project-and-item-templates.md)을 참조하세요.

::: moniker-end

::: moniker range=">=vs-2019"

5. **템플릿 옵션 선택** 페이지에서 템플릿의 이름 및 설명(옵션), 아이콘 및 미리 보기 이미지를 입력합니다. 이러한 항목은 새 프로젝트를 만드는 대화 상자에 나타납니다. **마침**을 선택합니다.

   프로젝트는 *.zip* 파일로 내보내고 지정된 출력 위치에 배치되며 선택할 경우 Visual Studio로 가져옵니다.

새 프로젝트를 만드는 대화 상자에서 템플릿을 찾으려면 이름으로 검색하거나 목록을 스크롤합니다. (사용자 템플릿에서는 현재 언어 또는 프로젝트 형식에 따라 필터링할 수 없습니다.)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>프로젝트 템플릿을 만드는 다른 방법

프로젝트를 구성하는 파일을 폴더로 수집하고 적절한 메타데이터가 있는 *.vstemplate* XML 파일을 만들어 수동으로 프로젝트 템플릿을 만들 수 있습니다. 자세한 내용은 [방법: 수동으로 웹 템플릿 만들기](../ide/how-to-manually-create-web-templates.md)를 참조하세요.

Visual Studio SDK를 설치한 경우 **VSIX 프로젝트** 템플릿을 사용하여 완료된 템플릿을 .vsix 파일로 래핑하여 배포할 수 있습니다. 자세한 내용은 [VSIX 프로젝트 템플릿 시작](../extensibility/getting-started-with-the-vsix-project-template.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [방법: 항목 템플릿 만들기](../ide/how-to-create-item-templates.md)
- [VSIX 프로젝트 템플릿 시작](../extensibility/getting-started-with-the-vsix-project-template.md)

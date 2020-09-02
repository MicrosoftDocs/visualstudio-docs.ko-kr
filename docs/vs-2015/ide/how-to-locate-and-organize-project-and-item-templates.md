---
title: '방법: 프로젝트 템플릿과 항목 템플릿 찾기 및 구성 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5f55de910eb77ec7ccbd205b78d5c95039e6b39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651865"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>방법: 프로젝트 템플릿과 항목 템플릿 찾기 및 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 인식할 수 있는 위치에 템플릿 파일이 있어야 **새 프로젝트** 및 **새 항목 추가** 대화 상자에 템플릿이 나타납니다. 템플릿에 대한 사용자 지정 하위 범주를 만들어 이러한 하위 범주가 사용자 인터페이스에 나타나도록 할 수도 있습니다.

## <a name="locating-templates"></a>템플릿 찾기
 기본적으로 Visual Studio에서는 프로젝트 템플릿과 항목 템플릿을 찾기 위해 두 위치를 검색합니다. .vstemplate 파일을 포함하는 압축된 파일이 이러한 위치에 있는 경우 템플릿은 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 나타납니다.

### <a name="installed-templates"></a>설치된 템플릿
 기본적으로 제품과 함께 설치된 템플릿은 다음 위치에 있습니다.

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*Language*\\*Locale*\

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*Language*\\*Locale\\*

  예를 들어 다음 디렉터리에는 영어용 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 템플릿이 포함되어 있습니다.

  C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="custom-templates"></a>사용자 지정 템플릿
 기본적으로 사용자 지정 템플릿은 다음 위치에 있습니다.

- \My Documents\Visual Studio *Version*\Templates\ProjectTemplates\\*Language*\

- \My Documents\Visual Studio *Version*\Templates\ItemTemplates\\*Language*\

  예를 들어 다음 디렉터리에는 사용자 지정 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 프로젝트 템플릿이 포함되어 있습니다.

  C:\Documents and Settings\UserName\My Documents\\<Visual Studio version\>\Templates\ProjectTemplates\Visual C#\

  사용자 지정 템플릿은 지역화된 템플릿에 대한 하위 디렉터리를 포함하지 않습니다. **환경\프로젝트 및 솔루션**의 **옵션** 대화 상자에서 사용자 지정 템플릿의 기본 디렉터리를 변경할 수 있습니다.

## <a name="organizing-templates"></a>템플릿 구성
 **새 프로젝트** 및 **새 항목 추가** 대화 상자의 범주는 설치된 템플릿과 사용자 지정 템플릿 위치에 있는 디렉터리 구조를 반영합니다. 이러한 디렉터리 구조를 수정하여 이해할 수 있는 방식으로 템플릿을 구성할 수 있습니다.

> [!NOTE]
> 프로그래밍 언어 수준에서 새 범주를 만들 수 없습니다. 새 범주는 각 언어 내에서만 만들어질 수 있습니다.

 특정 언어의 설치된 템플릿과 사용자 지정 템플릿의 디렉터리 구조가 서로 같지 않은 경우(즉, 한 폴더에는 없는 디렉터리가 다른 폴더에 있는 경우) **새 프로젝트** 대화 상자에는 모든 범주가 병합되어 나타납니다.

### <a name="organizing-installed-templates"></a>설치된 템플릿 구성
 프로그래밍 언어 폴더에 하위 디렉터리를 만들어 설치된 템플릿을 구성할 수 있습니다. 이러한 하위 디렉터리는 **새 프로젝트** 및 **새 항목 추가** 대화 상자에 각 언어 내의 가상 폴더로 나타납니다.

##### <a name="to-create-new-installed-project-template-categories"></a>설치된 프로젝트 템플릿 범주를 새로 만들려면

1. 설치된 템플릿 디렉터리의 언어 폴더에 폴더를 만듭니다. 예를 들어 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 템플릿에 대해 Office 범주를 만들려면 다음 디렉터리를 만듭니다

    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\

2. 이 범주의 모든 템플릿을 새 폴더에 넣습니다.

3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 모든 인스턴스를 닫습니다.

4. **시작** 메뉴에서 **실행**을 클릭한 다음 **cmd**를 입력하고 **확인**을 클릭합니다.

5. 명령 프롬프트에서 devenv.exe가 있는 디렉터리를 찾고 **devenv /installvstemplates**를 입력합니다.

6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 실행합니다.

7. **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.

8. Office 범주가 **새 프로젝트** 대화 상자의 **프로젝트 형식** 창에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 아래에 나타나는지 확인합니다.

   프로젝트 항목 템플릿의 일부를 사용자 지정 폴더로 그룹화할 수도 있습니다.

##### <a name="to-create-new-installed-item-template-categories"></a>설치된 항목 템플릿 범주를 새로 만들려면

1. 설치된 템플릿 디렉터리의 언어 폴더에 폴더를 만듭니다. 예를 들어, [!INCLUDE[csprcs](../includes/csprcs-md.md)] 항목 템플릿에 대해 Web 범주를 만들려면 다음 디렉터리를 만듭니다.

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\

2. 이 범주의 모든 템플릿을 새 폴더에 넣습니다.

3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 모든 인스턴스를 닫습니다.

4. **시작** 메뉴에서 **실행**을 클릭한 다음 **cmd**를 입력하고 **확인**을 클릭합니다.

5. 명령 프롬프트에서 devenv.exe가 있는 디렉터리를 찾고 **devenv /setup**를 입력합니다.

6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 실행합니다.

7. 프로젝트를 만들거나 기존 프로젝트를 엽니다.

8. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

9. 웹 범주가 **새 항목 추가** 대화 상자의 **프로젝트 형식** 창에 나타나는지 확인합니다.

### <a name="organizing-custom-templates"></a>사용자 지정 템플릿 구성
 사용자 지정 템플릿 위치에 새 폴더를 추가하여 사용자 지정 템플릿을 독자적인 범주로 구성할 수 있습니다. **새 프로젝트** 대화 상자는 템플릿 범주에 수행된 모든 변경 내용을 반영합니다.

##### <a name="to-create-new-custom-project-template-categories"></a>사용자 지정 프로젝트 템플릿 범주를 새로 만들려면

1. 사용자 지정 프로젝트 템플릿 디렉터리의 언어 폴더에 폴더를 만듭니다. 예를 들어 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 템플릿에 대해 HelloWorld 범주를 만들려면 다음 디렉터리를 만듭니다.

    \My Documents\\<Visual Studio version\>\Templates\ProjectTemplates\CSharp\HelloWorld\

2. 이 범주의 모든 템플릿을 새 폴더에 넣습니다.

3. **파일** 메뉴에서 **새로 만들기**를 클릭한 다음 **프로젝트**를 클릭합니다.

4. HelloWorld 범주가 **새 프로젝트** 대화 상자의 **프로젝트 형식** 창에서 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 아래에 나타나는지 확인합니다.

   사용자 지정 항목 템플릿의 일부를 사용자 지정 폴더로 그룹화할 수도 있습니다.

##### <a name="to-create-new-custom-item-template-categories"></a>사용자 지정 항목 템플릿 범주를 새로 만들려면

1. 사용자 지정 항목 템플릿 디렉터리의 언어 폴더에 폴더를 만듭니다. 예를 들어 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 템플릿에 대해 HelloWorld 범주를 만들려면 다음 디렉터리를 만듭니다.

     \My Documents\\<Visual Studio version\>\Templates\ItemTemplates\CSharp\HelloWorld\

2. 이 범주의 모든 템플릿을 새 폴더에 넣습니다.

3. 프로젝트를 만들거나 기존 프로젝트를 엽니다.

4. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

5. HelloWorld 범주가 **새 항목 추가** 대화 상자의 **프로젝트 형식** 창에 나타나는지 확인합니다.

### <a name="displaying-templates-in-parent-categories"></a>부모 범주에 템플릿 표시
 .vstemplate 파일에서 `NumberOfParentCategoriesToRollUp` 요소를 사용하여 하위 범주의 템플릿이 부모 범주에 표시되도록 할 수 있습니다. 이 단계는 프로젝트 템플릿과 항목 템플릿 모두에 대해 동일합니다.

##### <a name="to-display-templates-in-parent-categories"></a>템플릿을 부모 범주에 표시하려면

1. 템플릿을 포함하는 .zip 파일을 찾습니다.

2. .zip 파일의 압축을 풉니다.

3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 .vstemplate 파일을 엽니다.

4. `TemplateData` 요소에서 `NumberOfParentCategoriesToRollUp` 요소를 추가합니다. 예를 들어 다음 코드에서는 템플릿이 부모 범주에 표시되고 더 높은 범주에는 표시되지 않도록 합니다.

    ```
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

5. .vstemplate 파일을 저장한 다음 닫습니다.

6. 템플릿에 있는 파일을 선택하고 선택 영역을 마우스 오른쪽 단추로 클릭한 다음 **보내기**를 클릭하고 **압축(ZIP) 폴더**를 클릭합니다. 파일이 .zip 파일로 압축됩니다.

7. 추출된 템플릿 파일과 이전 템플릿 .zip 파일을 삭제합니다.

8. 새 .zip 파일을 삭제된 .zip 파일이 있던 디렉터리에 넣습니다.

## <a name="see-also"></a>관련 항목
 [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md) [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md) [NumberOfParentCategoriesToRollUp (visual Studio 템플릿)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) [방법: 프로젝트 템플릿 만들기](../ide/how-to-create-project-templates.md) [방법: 항목 템플릿 만들기](../ide/how-to-create-item-templates.md)

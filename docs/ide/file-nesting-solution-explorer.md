---
title: 솔루션 탐색기의 파일 중첩 규칙
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jillfra
ms.openlocfilehash: a36ca2535785f72756ad66a69c2ebe4d7d5a373b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "67587021"
---
# <a name="file-nesting-in-solution-explorer"></a>솔루션 탐색기에서 파일 중첩

**솔루션 탐색기**는 관련 파일들을 중첩시켜 보다 쉽게 찾고 정리할 수 있도록 합니다. 예를 들어 Windows Forms 양식을 프로젝트에 추가하면 양식의 코드 파일이 **솔루션 탐색기**의 양식 아래에 중첩됩니다. ASP.NET Core 프로젝트에서는 파일 중첩을 한 단계 더 수행할 수 있습니다. 파일 중첩 미리 설정을 **끄기**, **기본값**, **웹** 중에서 선택할 수 있습니다. [새 파일의 중첩 방식을 사용자 지정](#customize-file-nesting)하거나 [솔루션별 설정 및 프로젝트별 설정을 만들 수도 있습니다](#create-project-specific-settings).

> [!NOTE]
> 이 기능은 현재 ASP.NET Core 프로젝트에만 지원됩니다.

## <a name="file-nesting-options"></a>파일 중첩 옵션

![파일 중첩 켜기/끄기 단추](media/filenesting_onoff.png)

사용자 지정되지 않은 파일 중첩에 사용할 수 있는 옵션은 다음과 같습니다.

* **끄기**: 이 옵션은 중첩이 없는 단순 파일 목록을 제공합니다.

* **기본값**: 이 옵션은 **솔루션 탐색기**에서 기본 파일 중첩 동작을 제공합니다. 지정된 프로젝트 형식에 대한 설정이 없으면 프로젝트의 파일이 중첩되지 않습니다. 예를 들어 웹 프로젝트에 대한 설정이 있는 경우, 중첩이 적용됩니다.

* **웹**: 이 옵션은 현재 솔루션의 모든 프로젝트에 **웹** 파일 중첩 동작을 적용합니다. 이는 많은 규칙을 가지고 있으며, 규칙을 확인하고 의견을 보내 주시기 바랍니다. 다음 스크린샷은 이 옵션으로 구현된 파일 중첩 동작의 몇 가지 예를 보여 줍니다.

   ![솔루션 탐색기에서 파일 중첩](media/filenesting.png)

## <a name="customize-file-nesting"></a>파일 중첩 사용자 지정

기본적으로 제공되는 항목이 마음에 들지 않으면, **솔루션 탐색기**에 파일 중첩 방법을 지시하는 사용자 지정 파일 중첩 설정을 직접 만들 수 있습니다. 원하는 만큼의 사용자 지정 파일 중첩 설정을 추가할 수 있으며, 원하는 대로 전환할 수 있습니다. 새 사용자 지정 설정을 만들려면 빈 파일로 시작하거나 **웹** 설정을 시작점으로 사용할 수 있습니다.

![사용자 지정 파일 중첩 규칙 추가](media/filenesting_addcustom.png)

이미 작동하는 것으로 작업하기가 쉽기 때문에 **웹** 설정을 시작점으로 사용하는 것이 좋습니다. **웹** 설정을 시작점으로 사용하는 경우 *.filenesting.json* 파일은 다음 파일과 유사합니다.

![기존 파일 중첩 규칙을 사용자 지정 설정의 기반으로 사용](media/filenesting_editcustom.png)

노드 **dependentFileProviders**와 그 자식 노드를 중점적으로 살펴보겠습니다. 각 자식 노드는 Visual Studio에서 파일을 중첩하는 데 사용할 수 있는 규칙 형식입니다. 예를 들어 **파일 이름은 동일하지만 확장명이 다름**은 하나의 규칙 형식입니다. 사용 가능한 규칙은 다음과 같습니다.

* **extensionToExtension**: *file.ts* 아래에 *file.js*를 중첩하려면 이 규칙 형식을 사용합니다.

* **fileSuffixToExtension**: *file.js* 아래에 *file-vsdoc.js*를 중첩하려면 이 규칙 형식을 사용합니다.

* **addedExtension**: *file.html* 아래에 *file.html.css*를 중첩하려면 이 규칙 형식을 사용합니다.

* **pathSegment**: *jquery.js* 아래에 *jquery.min.js*를 중첩하려면 이 규칙 형식을 사용합니다.

* **allExtensions**: *file.js* 아래에 *file.**를 중첩하려면 이 규칙 형식을 사용합니다.

* **fileToFile**: *.bowerrc* 아래에 *bower.json*을 중첩하려면 이 규칙 형식을 사용합니다.

### <a name="the-extensiontoextension-provider"></a>extensionToExtension 공급자

이 공급자를 사용하면 특정 파일 확장명을 사용하여 파일 중첩 규칙을 정의할 수 있습니다. 다음 예제를 참조하세요.

![extentionToExtension 예제 규칙](media/filenesting_extensiontoextension.png) ![extentionToExtension 예제 효과](media/filenesting_extensiontoextension_effect.png)

* *cart.js*는 첫 번째 **extensionToExtension** 규칙으로 인해 *cart.ts* 아래에 중첩됩니다.

* **.ts**가 규칙에서 **.tsx**보다 먼저 나오기 때문에 *cart.js*는 *cart.tsx* 아래에 중첩되지 않으며, 하나의 부모만 있을 수 있습니다.

* *light.css*는 두 번째 **extensionToExtension** 규칙 때문에 *light.sass* 아래에 중첩됩니다.

* *home.html*은 세 번째 **extensionToExtension** 규칙 때문에 *home.md* 아래에 중첩됩니다.

### <a name="the-filesuffixtoextension-provider"></a>fileSuffixToExtension 공급자

이 공급자는 **extensionToExtension** 공급자처럼 작동하지만 유일한 차이점은 규칙이 확장명 대신 파일의 접미사를 찾는다는 것입니다. 다음 예제를 참조하세요.

![fileSuffixToExtension 예제 규칙](media/filenesting_filesuffixtoextension.png) ![fileSuffixToExtension 예제 효과](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js*는 **fileSuffixToExtension** 규칙 때문에 *portal.js* 아래에 중첩됩니다.

* 규칙의 다른 모든 측면은 **extensionToExtension**과 같은 방식으로 작동합니다.

### <a name="the-addedextension-provider"></a>addedExtension 공급자

이 공급자는 추가 확장명 없이 파일 아래에 추가 확장명을 사용하여 파일을 중첩합니다. 추가 확장명은 전체 파일 이름 끝에만 나타날 수 있습니다.

다음 예제를 참조하세요.

![addedExtension 예제 규칙](media/filenesting_addedextension.png) ![addedExtension 예제 효과](media/filenesting_addedextension_effect.png)

* *file.html.css*는 **addedExtension** 규칙 때문에 *file.html* 아래에 중첩됩니다.

> [!NOTE]
> `addedExtension` 규칙에 대해 파일 확장명을 지정하지 않으면, 자동으로 모든 파일 확장명에 적용됩니다. 즉, 다른 파일과 동일한 이름 및 확장명과 끝에 추가 확장명이 붙은 파일은 모두 다른 파일 아래에 중첩됩니다. 이 공급자의 효과를 특정 파일 확장명만으로 제한할 수는 없습니다.

### <a name="the-pathsegment-provider"></a>pathSegment 공급자

이 공급자는 추가 확장명 없이 파일 아래에 추가 확장명을 사용하여 파일을 중첩합니다. 추가 확장명은 전체 파일 이름 중간에만 나타날 수 있습니다.

다음 예제를 참조하세요.

![pathSegment 예제 규칙](media/filenesting_pathsegment.png) ![pathSegment 예제 효과](media/filenesting_pathsegment_effect.png)

* *jquery.min.js*는 **pathSegment** 규칙 때문에 *jquery.js* 아래에 중첩됩니다.

> [!NOTE]
> - `pathSegment` 규칙에 대해 특정 파일 확장명을 지정하지 않으면, 모든 파일 확장명에 적용됩니다. 즉, 다른 파일과 동일한 이름 및 확장명과 중간에 추가 확장명이 붙은 파일은 모두 다른 파일 아래에 중첩됩니다.
> - 다음 방법으로 지정하면 `pathSegment` 규칙의 효과를 특정 파일 확장명으로 제한할 수 있습니다.
>
>    ```json
>    "pathSegment": {
>       "add": {
>         ".*": [
>           ".js",
>           ".css",
>           ".html",
>           ".htm"
>         ]
>       }
>    }
>    ```

### <a name="the-allextensions-provider"></a>allExtensions 공급자

이 공급자를 사용하면 확장명에 상관없이 기본 파일 이름이 같은 파일에 대한 파일 중첩 규칙을 정의할 수 있습니다. 다음 예제를 참조하세요.

![allExtensions 예제 규칙](media/filenesting_allextensions.png) ![allExtensions 예제 효과](media/filenesting_allextensions_effect.png)

* *template.cs* 및 *template.doc*는 **allExtensions** 규칙 때문에 *template.tt* 아래에 중첩됩니다.

### <a name="the-filetofile-provider"></a>fileToFile 공급자

이 공급자를 사용하면 전체 파일 이름을 기반으로 파일 중첩 규칙을 정의할 수 있습니다. 다음 예제를 참조하세요.

![fileToFile 예제 규칙](media/filenesting_filetofile.png) ![fileToFile 예제 효과](media/filenesting_filetofile_effect.png)

* *.bowerrc*는 **fileToFile** 규칙 때문에 *bower.json* 아래에 중첩됩니다.

### <a name="rule-order"></a>규칙 순서

사용자 지정 설정 파일의 모든 부분에서 순서 지정이 중요합니다. **dependentFileProvider** 노드 내에서 위 또는 아래로 이동하여 규칙이 실행되는 순서를 변경할 수 있습니다. 예를 들어, **file.js**가 **file.ts**의 부모가 되는 규칙과 **file.coffee**가 **file.ts**의 부모가 되는 다른 규칙이 있는 경우, 세 개의 파일이 모두 있을 때 파일에 나타나는 순서에 따라 중첩 동작을 지시합니다. **file.ts**는 하나의 부모만 가질 수 있으므로 처음으로 실행되는 규칙이 우선 적용됩니다.

섹션 내의 파일뿐만 아니라 규칙 섹션 자체에도 순서를 지정하는 것이 중요합니다. 한 쌍의 파일이 중첩 규칙과 일치하는 즉시 파일의 다른 하위 규칙은 무시되고, 다음 파일 쌍이 처리됩니다.

### <a name="file-nesting-button"></a>파일 중첩 단추

**솔루션 탐색기**의 동일한 단추를 통해 사용자 지정 설정을 포함한 모든 설정을 관리할 수 있습니다.

![사용자 지정 파일 중첩 규칙 활성화](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>프로젝트별 설정 만들기

각 솔루션 및 프로젝트의 오른쪽 클릭 메뉴(상황에 맞는 메뉴)를 통해 솔루션별 설정 및 프로젝트별 설정을 만들 수 있습니다.

![솔루션 및 프로젝트별 중첩 규칙](media/filenesting_solutionprojectspecific.png)

솔루션별 설정 및 프로젝트별 설정은 활성 Visual Studio 설정과 결합됩니다. 예를 들어 프로젝트별 설정 파일이 비어 있더라도 **솔루션 탐색기**는 파일을 중첩합니다. 중첩 동작은 솔루션별 설정 또는 Visual Studio 설정에서 발생합니다. 파일 중첩 설정 병합의 우선순위는 Visual Studio > 솔루션 > 프로젝트입니다.

**도구** > **옵션** > **ASP.NET Core** > **파일 중첩**에서 **솔루션 및 프로젝트 설정 무시** 옵션을 사용하도록 설정하면, 파일이 디스크에 있더라도 솔루션별 설정 및 프로젝트별 설정을 무시하도록 Visual Studio에 지시할 수 있습니다.

반대의 작업을 수행하고 **root** 노드를 **true**로 설정하여 Visual Studio에 솔루션별 설정 또는 프로젝트별 설정*만* 사용하도록 할 수 있습니다. Visual Studio는 해당 수준에서 파일 병합을 중지하고 상위 계층의 파일과 결합하지 않습니다.

솔루션별 설정 및 프로젝트별 설정을 소스 제어에 체크인할 수 있으며, 코드베이스를 작업하는 전체 팀이 이를 공유할 수 있습니다.

## <a name="disable-file-nesting-rules-for-a-project"></a>프로젝트에 파일 중첩 규칙 사용 안 함

공급자에 대해 **추가** 대신 **제거** 작업을 사용하여 특정 솔루션 또는 프로젝트에 대한 기존 전역 파일 중첩 규칙을 사용하지 않을 수 있습니다. 예를 들어, 다음 설정 코드를 프로젝트에 추가하면 이 특정 프로젝트에 대해 전역으로 존재할 수 있는 모든 **pathSegment** 규칙이 비활성화됩니다.

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>참조

- [IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio의 솔루션 및 프로젝트](solutions-and-projects-in-visual-studio.md)

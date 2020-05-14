---
title: 프로젝트 및 항목 템플릿 매개 변수
ms.date: 01/02/2018
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 7076e8f5718e44cc382eb0768e6456dbd6ee5664
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169367"
---
# <a name="template-parameters"></a>템플릿 매개 변수

템플릿이 인스턴스화될 때 템플릿에서 값을 바꿀 수 있습니다. 이 기능을 설정하려면 *템플릿 매개 변수*를 사용합니다. 템플릿 매개 변수는 템플릿에서 클래스 이름 및 네임 스페이스 같은 값을 바꾸는 데 사용할 수 있습니다. 사용자가 새 항목을 추가하거나 프로젝트가 이러한 매개 변수를 바꾸는 경우 백그라운드에서 실행되는 템플릿 마법사입니다.

## <a name="declare-and-enable-template-parameters"></a>템플릿 매개 변수 선언 및 사용

템플릿 매개 변수는 $*매개 변수*$ 형식으로 선언됩니다. 예를 들어:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="enable-parameter-substitution-in-templates"></a>템플릿에서 매개 변수 대체 사용

1. 템플릿의 *.vstemplate* 파일에서 매개 변수 대체를 활성화하려는 항목에 해당하는 `ProjectItem` 요소를 찾습니다.

1. `ReplaceParameters` 요소의 `ProjectItem` 특성을 `true`로 설정합니다.

1. 프로젝트 항목에 대한 코드 파일에서 적절한 경우 매개 변수를 포함합니다. 예를 들어 다음 매개 변수는 안전한 프로젝트 이름을 파일에서 네임스페이스에 사용할 수 있다고 지정합니다.

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>예약된 템플릿 매개 변수

다음 표에서는 템플릿에서 사용할 수 있는 예약된 템플릿 매개 변수를 나열합니다.

|매개 변수|설명|
|---------------|-----------------|
|clrversion|CLR(공용 언어 런타임)의 현재 버전입니다.|
|ext_*|부모 템플릿의 변수를 참조하는 매개 변수에 `ext_` 접두사를 추가합니다. 예: `ext_safeprojectname`.|
|guid[1-10]|프로젝트 파일에서 프로젝트 GUID를 대체하는 데 사용되는 GUID입니다. 최대 10개의 고유 GUID를 지정할 수 있습니다(예: `guid1`).|
|itemname|매개 변수가 사용되는 파일의 이름입니다.|
|machinename|현재 컴퓨터 이름(예: Computer01)입니다.|
|projectname|프로젝트를 만들 때 사용자가 제공한 이름입니다.|
|registeredorganization|HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization의 레지스트리 키 값입니다.|
|rootnamespace|현재 프로젝트의 루트 네임스페이스입니다. 이 매개 변수는 항목 템플릿에만 적용됩니다.|
|safeitemname|`itemname`과 동일하지만, 모든 안전하지 않은 문자와 공백이 밑줄 문자로 대체됩니다.|
|safeitemrootname|`safeitemname`와 동일합니다.|
|safeprojectname|프로젝트를 만들 때 사용자가 제공했지만 안전하지 않은 문자 및 공백을 모두 제거한 이름입니다.|
|Time|DD/MM/YYYY 00:00:00 형식인 현재 시간입니다.|
|specifiedsolutionname|솔루션의 기본 이름. "솔루션 디렉터리 만들기"를 선택한 경우 `specifiedsolutionname`에는 솔루션 이름이 있습니다. "솔루션 디렉터리 만들기"를 선택하지 않은 경우 `specifiedsolutionname`은 비어 있습니다.|
|userdomain|현재 사용자 도메인입니다.|
|사용자 이름|현재 사용자 이름입니다.|
|webnamespace|현재 웹 사이트의 이름입니다. 이 매개 변수는 고유한 클래스 이름을 보장하기 위해 웹 양식 템플릿에서 사용됩니다. 웹 사이트가 웹 서버의 루트 디렉터리에 있으면 이 템플릿 매개 변수는 웹 서버의 루트 디렉터리를 확인합니다.|
|년|YYYY 형식인 현재 연도입니다.|

> [!NOTE]
> 템플릿 매개 변수는 대/소문자를 구분합니다.

## <a name="custom-template-parameters"></a>사용자 지정 템플릿 매개 변수

매개 변수를 대체하는 동안 사용되는 예약된 기본 템플릿 매개 변수 외에 템플릿 매개 변수와 값을 직접 지정할 수 있습니다. 자세한 내용은 [CustomParameters 요소(Visual Studio 템플릿)](../extensibility/customparameters-element-visual-studio-templates.md)를 참조하세요.

## <a name="example-use-the-project-name-for-a-file-name"></a>예: 파일 이름에 프로젝트 이름 사용

`TargetFileName` 특성에 매개 변수를 사용하여 프로젝트 항목에 대한 변수 파일 이름을 지정할 수 있습니다.

다음 예제에서는 `$projectname$`으로 지정된 프로젝트 이름을 사용하는 실행 파일의 이름을 지정합니다.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>예: 네임스페이스 이름에 안전한 프로젝트 이름 사용

C# 클래스 파일에서 네임스페이스에 프로젝트 이름을 사용하려면 다음 구문을 사용합니다.

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

프로젝트 템플릿의 *.vstemplate* 파일에서 이 파일을 참조할 때 `ReplaceParameters="true"` 특성을 포함합니다.

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>참조

- [방법: 템플릿의 매개 변수 대체](how-to-substitute-parameters-in-a-template.md)
- [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md)
- [방법: 프로젝트 템플릿 만들기](../ide/how-to-create-project-templates.md)
- [템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)

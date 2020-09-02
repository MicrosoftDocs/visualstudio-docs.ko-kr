---
title: 템플릿 매개 변수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d7bb7e0f3dfee3dd1bf3e9b42afd5837a29f6ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646814"
---
# <a name="template-parameters"></a>템플릿 매개 변수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

템플릿에 매개 변수를 사용하여 템플릿이 인스턴스화될 때 클래스 이름 및 네임스페이스 등 템플릿의 주요 부분 값을 바꿀 수 있습니다. 사용자가 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에서 **확인**을 클릭하는 경우 이러한 매개 변수는 백그라운드에서 실행되는 템플릿 마법사로 바뀝니다.

## <a name="declaring-and-enabling-template-parameters"></a>템플릿 매개 변수 선언 및 사용
 템플릿 매개 변수는 $*매개 변수*$ 형식으로 선언됩니다. 예를 들면 다음과 같습니다.

- $safeprojectname$

- $guid1$

- $guid5$

#### <a name="to-enable-parameter-substitution-in-templates"></a>템플릿에서 매개 변수 대체를 사용하려면

1. 템플릿의 .vstemplate 파일에서 매개 변수 대체를 활성화하려는 항목에 해당하는 `ProjectItem` 요소를 찾습니다.

2. `ReplaceParameters` 요소의 `ProjectItem` 특성을 `true`로 설정합니다.

3. 프로젝트 항목에 대한 코드 파일에서 적절한 경우 매개 변수를 포함합니다. 예를 들어 다음 매개 변수는 안전한 프로젝트 이름을 파일에서 네임스페이스에 사용할 수 있다고 지정합니다.

    ```
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>예약된 템플릿 매개 변수
 다음 표에서는 템플릿에서 사용할 수 있는 예약된 템플릿 매개 변수를 나열합니다.

> [!NOTE]
> 템플릿 매개 변수는 대/소문자를 구분합니다.

|매개 변수|설명|
|---------------|-----------------|
|`clrversion`|CLR(공용 언어 런타임)의 현재 버전입니다.|
|`GUID [1-10]`|프로젝트 파일에서 프로젝트 GUID를 대체하는 데 사용되는 GUID입니다. 최대 10개의 고유 GUID를 지정할 수 있습니다(예: `guid1)`).|
|`itemname`|**새 항목 추가** 대화 상자에서 사용자가 제공한 이름입니다.|
|`machinename`|현재 컴퓨터 이름(예: Computer01)입니다.|
|`projectname`|**새 프로젝트** 대화 상자에서 사용자가 제공한 이름입니다.|
|`registeredorganization`|HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization의 레지스트리 키 값입니다.|
|`rootnamespace`|현재 프로젝트의 루트 네임스페이스입니다. 이 매개 변수는 항목 템플릿에만 적용됩니다.|
|`safeitemname`|**새 항목 추가** 대화 상자에서 사용자가 제공하고 모든 안전하지 않은 문자 및 공백을 제거한 이름입니다.|
|`safeprojectname`|**새 프로젝트** 대화 상자에서 사용자가 제공하고 모든 안전하지 않은 문자 및 공백을 제거한 이름입니다.|
|`time`|DD/MM/YYYY 00:00:00 형식인 현재 시간입니다.|
|`SpecificSolutionName`|솔루션의 기본 이름. "솔루션 디렉터리 만들기"를 선택한 경우 `SpecificSolutionName`에는 솔루션 이름이 있습니다. "솔루션 디렉터리 만들기"를 선택하지 않은 경우 `SpecificSolutionName`은 비어 있습니다.|
|`userdomain`|현재 사용자 도메인입니다.|
|`username`|현재 사용자 이름입니다.|
|`webnamespace`|현재 웹 사이트의 이름입니다. 이 매개 변수는 고유한 클래스 이름을 보장하기 위해 웹 양식 템플릿에서 사용됩니다. 웹 사이트가 웹 서버의 루트 디렉터리에 있으면 이 템플릿 매개 변수는 웹 서버의 루트 디렉터리를 확인합니다.|
|`year`|YYYY 형식인 현재 연도입니다.|

## <a name="custom-template-parameters"></a>템플릿 매개 변수 사용자 지정
 매개 변수를 대체하는 동안 사용되는 예약된 기본 템플릿 매개 변수 외에 템플릿 매개 변수와 값을 직접 지정할 수 있습니다. 자세한 내용은 [CustomParameters 요소(Visual Studio 템플릿)](../extensibility/customparameters-element-visual-studio-templates.md)를 참조하세요.

## <a name="example-replacing-files-names"></a>예: 파일 이름 바꾸기
 `TargetFileName` 특성을 포함한 매개 변수를 사용하여 프로젝트 항목에 대한 변수 파일 이름을 지정할 수 있습니다. .exe 파일에서 `$projectname$`에서 지정된 프로젝트 이름을 파일 이름으로 사용하도록 지정할 수 있습니다.

```
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-project-name-for-the-namespace-name"></a>예: 네임스페이스 이름에 프로젝트 이름 사용
 Visual C# 클래스 파일, Class1.cs에에서 네임스페이스에 프로젝트 이름을 사용하려면 다음 구문을 사용합니다.

```
#region Using directives

using System;
using System.Collections.Generic;
using System.Text;

#endregion

namespace $safeprojectname$
{
    public class Class1
        {
            public Class1()
                {

                }
         }
}
```

 프로젝트 템플릿의 .vstemplate 파일에서 Class1.cs 파일을 참조할 때 다음과 같은 XML을 포함합니다.

```
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>관련 항목
 [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md)

---
title: 사용자 지정 모델링 도구 상자 항목 정의 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a038150519ea7a40a52fb1be16ed93045c09eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851514"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>사용자 지정 모델링 도구 상자 항목 정의
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

자주 사용하는 패턴에 따라 요소 또는 요소 그룹을 쉽게 만들 수 있도록 Visual Studio의 모델링 다이어그램 도구 상자에 새로운 도구를 추가할 수 있습니다. 다른 Visual Studio 사용자에게 이러한 도구 상자 항목을 배포할 수 있습니다.

 이 기능을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

 사용자 지정 도구는 다이어그램에서 하나 이상의 새 요소를 만듭니다. 예를 들어 다음과 같은 요소를 만드는 사용자 지정 도구를 만들 수 있습니다.

- .NET 프로필 및 .NET 스테레오타입을 가진 클래스에 연결된 패키지

- 관찰자 패턴을 나타내기 위해 연결에 의해 연결된 클래스 쌍

> [!NOTE]
> 이 방법을 사용하여 요소 도구를 만들 수 있습니다. 즉, 도구 상자에서 다이어그램으로 끌어오는 도구를 만들 수 있습니다. 연결선 도구는 만들 수 없습니다.

## <a name="defining-a-custom-modeling-tool"></a><a name="DefineTool"></a> 사용자 지정 모델링 도구 정의

#### <a name="to-define-a-custom-modeling-tool"></a>사용자 지정 모델링 도구를 정의하려면

1. 요소 또는 요소 그룹을 포함하는 UML 다이어그램을 만듭니다.

    - 이러한 요소는 요소 간에 관계가 있을 수 있으며 포트, 특성, 작업 또는 핀과 같은 보조 요소를 포함할 수 있습니다.

2. 새 도구에 지정하려는 이름을 사용하여 다이어그램을 저장합니다. **파일** 메뉴에서 저장 ...을 사용 합니다. ** As**.

3. Windows 탐색기를 사용하여 다음 폴더나 하위 폴더에 두 개의 다이어그램 파일을 복사합니다.

     기타 *문서* **\Visual Studio\Architecture Tool사용자 지정 도구 상자 항목**

    - 이 폴더가 없는 경우 새로 만듭니다. **아키텍처 도구** 와 **사용자 지정 도구 상자 항목**을 모두 만들어야 할 수도 있습니다.

    - 이름이 "..." 인 다이어그램 파일을 모두 복사 합니다. **다이어그램**"과 이름이" ... "인 **다이어그램. 레이아웃**"

    - 사용자 지정 도구를 원하는 개수만큼 만들 수 있습니다. 각 도구에 대해 하나의 다이어그램을 사용합니다.

4. 필드 [사용자 지정 도구의 속성을 정의 하는 방법](#tbxinfo)에 설명 된 대로 **.tbxinfo** 파일을 만들고 동일한 디렉터리에 추가 합니다. 이렇게 하면 도구 상자 아이콘, 도구 설명 등을 정의할 수 있습니다.

    - **.Tbxinfo** 파일은 여러 도구를 정의 하는 데 사용할 수 있습니다. 하위 폴더에 있는 다이어그램 파일을 참조할 수 있습니다.

5. Visual Studio를 다시 시작합니다. 해당 다이어그램 형식의 도구 상자에 추가 도구가 나타납니다.

### <a name="what-the-custom-tool-will-replicate"></a>사용자 지정 도구에 의해 복제되는 항목
 사용자 지정 도구는 소스 다이어그램의 기능을 대부분 복제합니다.

- 이름. 도구 상자에서 항목을 만들 때 동일한 네임스페이스에서 중복된 이름을 방지하기 위해 필요한 경우 이름의 끝에 번호가 추가됩니다.

- 색, 크기 및 모양

- 스테레오타입 및 패키지 프로필

- 추상과 같은 속성 값

- 연결된 작업 항목

- 복합성 및 관계의 기타 속성

- 모양의 상대 위치

  다음 기능은 사용자 지정 도구에서 유지되지 않습니다.

- 단순 도형. 모델 요소와 관련이 없으며 일부 종류의 다이어그램에서 그릴 수 있는 모양입니다.

- 연결선 경로 지정. 연결선 경로를 수동으로 지정하는 경우 도구를 사용할 때 경로 지정이 유지되지 않습니다. 포트와 같은 일부 중첩된 모양의 위치는 소유자를 기준으로 유지되지 않습니다.

## <a name="how-to-define-the-properties-of-custom-tools"></a><a name="tbxinfo"></a> 사용자 지정 도구의 속성을 정의 하는 방법
 도구 상자 정보 (**. .tbxinfo**) 파일을 사용 하면 하나 이상의 사용자 지정 도구에 대해 도구 상자 이름, 아이콘, 도구 설명, 탭 및 도움말 키워드를 지정할 수 있습니다. **MyTools. .tbxinfo**와 같은 이름을 지정 합니다.

 일반적인 파일 형식은 다음과 같습니다.

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 각 항목의 값은 다음 중 하나일 수 있습니다.

- 예제와 같이 도구 상자 아이콘은 `<bmp fileName="…"/>`이고, 다른 항목은 `<value>string</value>`입니다.

  \- 또는 -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   이 경우 문자열 값이 리소스로 컴파일된, 컴파일된 어셈블리를 제공합니다.

  정의할 각 도구 상자 항목에 대한 `<customToolboxItem>` 노드를 추가합니다.

  **.Tbxinfo** 파일의 노드는 다음과 같습니다. 각 노드에 대한 기본값이 있습니다.

|노드 이름|정의|
|---------------|-------------|
|displayName|도구 상자 항목의 이름입니다.|
|tabName|항목이 표시되어야 하는 도구 상자 탭입니다. 이 다이어그램 형식에 대한 일반 탭의 이름이나 별도 이름을 지정할 수 있습니다.|
|이미지|높이와 너비가 16이 고 색 깊이가 24 비트인 비트맵 (**.bmp**) 파일의 위치입니다.|
|f1Keyword|도움말 항목을 찾는 키워드입니다.|
|도구 설명|이 도구에 대한 도구 설명입니다.|

 Visual Studio에서 비트맵 파일을 편집하고 속성 창에서 해당 높이와 너비를 16으로 설정할 수 있습니다.

> [!NOTE]
> 자체적으로 다이어그램 파일을 사용하여 실험한 후 .tbxinfo 파일 사용을 시작하는 경우 도구 상자에 기존 및 새 버전의 도구 상자 항목이 모두 포함될 수도 있습니다. 이 문제는 .tbxinfo 파일에 다이어그램 파일의 이름을 잘못 입력한 경우에도 발생할 수 있습니다. 이 문제가 발생 하는 경우 도구 상자의 바로 가기 메뉴에서 **도구 상자 다시 설정**을 선택 합니다. 사용자 지정 도구 상자 항목이 사라집니다. Visual Studio를 다시 시작하면 올바른 사용자 지정 항목이 나타납니다.

## <a name="how-to-distribute-toolbox-items-in-a-visual-studio-extension"></a><a name="Extension"></a> Visual Studio 확장에서 도구 상자 항목을 배포 하는 방법
 도구 상자 항목을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX (Visual Studio Extension)로 패키지 하 여 다른 사용자에 게 배포할 수 있습니다. 동일한 VSIX 파일에 명령, 프로필 및 기타 확장을 패키징할 수 있습니다. 자세한 내용은 [Visual Studio 확장 배포](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)를 참조 하세요.

 Visual Studio 확장을 빌드하는 일반적인 방법은 VSIX 프로젝트 템플릿을 사용하는 것입니다. 이렇게 하려면 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]가 설치되어 있어야 합니다.

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Visual Studio 확장에 도구 상자 항목을 추가하려면

1. [하나 이상의 사용자 지정 도구를 만들고 테스트](#DefineTool)합니다.

2. 도구를 참조 하는 [.tbxinfo 파일을 만듭니다](#tbxinfo) .

3. 기존 Visual Studio 확장 프로젝트를 엽니다.

     \- 또는 -

     새 Visual Studio 확장 프로젝트를 정의합니다.

    1. **파일** 메뉴에서 **새로 만들기**, **프로젝트**를 차례로 선택합니다.

    2. **새 프로젝트** 대화 상자의 **설치 된 템플릿**에서 **Visual c #**, **확장성**, **VSIX 프로젝트**를 선택 합니다.

4. 프로젝트에 도구 상자 정의를 추가합니다. .Tbxinfo 파일, 다이어그램 파일, 비트맵 파일 및 모든 리소스 파일을 포함 하 고 VSIX에 포함 되는지 확인 **합니다** .

    - 솔루션 탐색기의 VSIX 프로젝트 바로 가기 메뉴에서 **추가**, **기존 항목**을 선택 합니다. 대화 상자에서 **모든 파일 형식의 개체**를 설정 합니다. 파일을 찾아 모두 선택한 다음 **추가**를 선택 합니다.

        > [!NOTE]
        > 이 프로젝트에서는 모델 편집기에서 다이어그램 파일을 열 수 없습니다.

5. 방금 추가한 모든 파일의 다음 속성을 설정합니다. 솔루션 탐색기에서 모두 선택하여 동시에 해당 속성을 설정할 수 있습니다. 프로젝트에 있는 다른 파일의 속성을 변경하지 않도록 주의하세요.

     **출력 디렉터리**  =  에 복사 **항상 복사**

     **빌드 작업**  =  **콘텐츠**

     **VSIX**  =  에 포함 **true**

6. **source.extension.vsixmanifest**를 엽니다. 확장 매니페스트 편집기에서 열립니다.

7. **메타 데이터**에서 사용자 지정 도구에 대 한 설명을 추가 합니다.

     **자산**에서 **새로 만들기** 를 선택 하 고 대화 상자의 필드를 다음과 같이 설정 합니다.

    - **유형**  =  **사용자 지정 확장 프로그램 유형**

    - 형식 = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > 이는 드롭다운 목록의 옵션 중 하나가 아닙니다. 키보드를 사용하여 입력해야 합니다.

    - **원본**  =  **파일 시스템의 파일**입니다.

    - **Path** = **.tbxinfo** 파일 (예: **MyTools. .tbxinfo**

8. 프로젝트를 빌드합니다.

9. **확장이 작동 하는지 확인 하려면**f5 키를 누릅니다. Visual Studio의 실험적 인스턴스가 시작됩니다.

     실험적 인스턴스에서 관련 형식의 UML 다이어그램을 만들거나 엽니다. 도구 상자에 새 도구가 나타나고 요소를 제대로 만드는지 확인합니다.

10. **배포용 VSIX 파일을 가져오려면 다음을 수행 합니다.** Windows 탐색기에서 **.\bin\Release** **폴더를** 열고 **.vsix** 파일을 찾습니다. 이 파일은 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 확장 파일입니다. 사용자 컴퓨터에 설치할 수 있으며 다른 Visual Studio 사용자에게 전송할 수도 있습니다.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Visual Studio 확장에서 사용자 지정 도구를 설치하려면

1. Windows 탐색기 또는 Visual Studio에서 `.vsix` 파일을 엽니다.

2. 표시 되는 대화 상자에서 **설치** 를 선택 합니다.

3. 확장을 제거 하거나 일시적으로 사용 하지 않도록 설정 하려면 **도구** 메뉴에서 **확장 및 업데이트** 를 엽니다.

## <a name="localization"></a>지역화
 다른 컴퓨터에 설치될 때 대상 컴퓨터의 언어로 도구 이름 및 도구 설명을 표시하는 확장을 만들 수 있습니다.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>두 개 이상의 언어로 도구 버전을 제공하려면

1. 사용자 지정 도구를 하나 이상 포함하는 Visual Studio 확장 프로젝트를 만듭니다.

    **.Tbxinfo** 파일에서 리소스 파일 메서드를 사용 하 여 도구의 `displayName` , 도구 상자 및 도구 설명을 정의 합니다 `tabName` . 이러한 문자열이 정의된 리소스 파일을 만들고 어셈블리로 컴파일한 다음 tbxinfo 파일에서 참조합니다.

2. 다른 언어의 문자열이 있는 리소스 파일을 포함하는 추가 어셈블리를 만듭니다.

3. 이름이 언어의 문화권 코드인 폴더에 각 추가 어셈블리를 배치합니다. 예를 들어 이름이 **fr**인 폴더 안에 프랑스어 버전의 어셈블리를 저장 합니다.

4. `fr-CA`와 같은 특정 문화권이 아니라 일반적으로 두 문자로 이루어진 중립 문화권 코드를 사용해야 합니다. 문화권 코드에 대 한 자세한 내용은 전체 문화권 코드 목록을 제공 하는 [CultureInfo. GetCultures 메서드](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx)를 참조 하세요.

5. Visual Studio 확장을 빌드하고 배포합니다.

6. 다른 컴퓨터에 확장을 설치하면 사용자의 로컬 문화권에 대한 리소스 파일 버전이 자동으로 로드됩니다. 사용자 문화권에 대한 버전을 제공하지 않은 경우 기본 리소스가 사용됩니다.

   이 방법을 사용하여 여러 버전의 프로토타입 다이어그램을 설치할 수 없습니다. 요소 및 연결선의 이름이 모든 설치에서 동일합니다.

## <a name="other-toolbox-operations"></a>기타 도구 상자 작업
 일반적으로 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서 도구 이름을 바꾸고, 다른 도구 상자 탭으로 이동하고, 삭제하여 도구 상자를 개인 설정할 수 있습니다. 그러나 이 항목에서 설명한 절차에 따라 만든 사용자 지정 모델링 도구에 대해서는 이러한 변경 내용이 유지되지 않습니다. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 다시 시작하면 사용자 지정 도구가 정의된 이름 및 도구 상자 위치로 다시 나타납니다.

 또한 **도구 상자 다시 설정** 명령을 수행 하는 경우 사용자 지정 도구는 사라집니다. 그러나 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 다시 시작하면 다시 나타납니다.

## <a name="see-also"></a>관련 항목
 [Uml 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md) uml [확장을 위한 프로필 정의](../modeling/define-a-profile-to-extend-uml.md) [모델링 다이어그램의 메뉴 명령 정의](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [uml 모델에 대 한 유효성 검사 제약 조건 정의](../modeling/define-validation-constraints-for-uml-models.md)

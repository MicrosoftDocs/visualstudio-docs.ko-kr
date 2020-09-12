---
title: Visual Studio 확장에 대 한 규칙 기반 UI 컨텍스트 사용
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: fc24fe3f5b27b3c92f0629ed378c1a97c820cd0a
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037109"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>방법: Visual Studio 확장에 대 한 규칙 기반 UI 컨텍스트 사용

Visual Studio에서는 잘 알려진 특정를 활성화할 때 Vspackage를 로드할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.UIContext> . 그러나 이러한 UI 컨텍스트는 미세 하 게 세분화 되지 않으므로 확장 작성자는 선택 하지 않고 VSPackage 로드 하기 전에 활성화 되는 사용 가능한 UI 컨텍스트를 선택 합니다. 잘 알려진 UI 컨텍스트의 목록은를 참조 하십시오 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts> .

패키지를 로드 하면 성능에 영향을 줄 수 있으며 필요한 것 보다 빨리 로드할 수 있습니다. Visual Studio 2015에는 확장 작성자가 UI 컨텍스트가 활성화 되 고 관련 Vspackage 로드 되는 정확한 조건을 정의 하는 데 사용할 수 있는 메커니즘인 규칙 기반 UI 컨텍스트의 개념이 도입 되었습니다.

## <a name="rule-based-ui-context"></a>규칙 기반 UI 컨텍스트

"규칙"은 새 UI 컨텍스트 (GUID)와 논리적 "and", "or" 및 "not" 작업과 함께 사용 되는 하나 이상의 "용어"를 참조 하는 부울 식으로 구성 됩니다. "용어"는 런타임에 동적으로 계산 되며 조건이 변경 될 때마다 식이 다시 평가 됩니다. 식이 true로 평가 되 면 연결 된 UI 컨텍스트가 활성화 됩니다. 그렇지 않으면 UI 컨텍스트가 활성화 해제 됩니다.

규칙 기반 UI 컨텍스트는 다음과 같은 다양 한 방법으로 사용할 수 있습니다.

1. 명령 및 도구 창에 대 한 표시 유형 제약 조건을 지정 합니다. UI 컨텍스트 규칙이 충족 될 때까지 명령/도구 창을 숨길 수 있습니다.

2. 자동 로드 제약 조건: 규칙이 충족 되는 경우에만 패키지를 자동으로 로드 합니다.

3. 지연 된 작업 인 경우 지정 된 간격이 경과할 때까지 로드를 지연 하 고 규칙이 계속 충족 됩니다.

   모든 Visual Studio 확장에서이 메커니즘을 사용할 수 있습니다.

## <a name="create-a-rule-based-ui-context"></a>규칙 기반 UI 컨텍스트 만들기
 확장명이 *.config* 인 파일에만 적용 되는 메뉴 명령을 제공 하는 testpackage 라는 확장 프로그램이 있다고 가정 합니다. VS2015 하기 전에 UI 컨텍스트가 활성화 될 때 TestPackage를 로드 하는 것이 가장 좋습니다 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> . 이러한 방식으로 TestPackage를 로드 하는 것은 효율적이 지 않습니다. 로드 된 솔루션에 *.config* 파일이 포함 되지 않을 수 있기 때문입니다. 이러한 단계에서는 *.config* 확장명을 가진 파일을 선택한 경우에만 규칙 기반 ui 컨텍스트를 사용 하 여 ui 컨텍스트를 활성화 하 고 해당 ui 컨텍스트가 활성화 될 때 testpackage를 로드 하는 방법을 보여 줍니다.

1. 새 UIContext GUID를 정의 하 고 VSPackage 클래스 및에 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 추가 <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute> 합니다.

    예를 들어 새 UIContext "UIContextGuid"를 추가 한다고 가정해 보겠습니다. 만든 guid ( **도구**guid 만들기를 클릭 하 여 guid를 만들 수 있음  >  **Create GUID**)는 "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"입니다. 그런 다음 패키지 클래스 내부에 다음 선언을 추가 합니다.

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    특성의 경우 다음 값을 추가 합니다. (이러한 특성에 대 한 자세한 내용은 뒷부분에서 설명 합니다.)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    이러한 메타 데이터는 새 UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) 및 단일 용어 "DotConfig"를 참조 하는 식을 정의 합니다. "DotConfig" 용어는 활성 계층의 현재 선택 영역이 정규식 패턴 ".config $"와 일치 하는 이름을 가질 때마다 true로 평가 \\ 됩니다 ( *.config*로 끝남). (기본값) 값은 디버깅에 유용한 규칙의 선택적 이름을 정의 합니다.

    이 특성의 값은 빌드 시 나중에 생성 된 .pkgdef에 추가 됩니다.

2. TestPackage 명령의 VSCT 파일에서 "DynamicVisibility" 플래그를 적절 한 명령에 추가 합니다.

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT의 표시 유형 재정의 섹션에서 적절 한 명령을 #1에 정의 된 새 UIContext GUID에 연결 합니다.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. 기호 섹션에서 UIContext의 정의를 추가 합니다.

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    이제 * \* .config* 파일에 대 한 상황에 맞는 메뉴 명령은 솔루션 탐색기에서 선택한 항목이 *.config* 파일 일 때만 표시 되 고 패키지는 해당 명령 중 하나를 선택할 때까지 로드 되지 않습니다.

   그런 다음 디버거를 사용 하 여 패키지가 정상적으로 로드 되는지 확인 합니다. TestPackage를 디버그 하려면:

5. 메서드에 중단점을 설정 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 합니다.

6. TestPackage를 빌드하고 디버깅을 시작 합니다.

7. 프로젝트를 만들거나 하나를 엽니다.

8. *.Config*이외의 확장명을 가진 파일을 선택 합니다. 중단점이 적중 되어서는 안 됩니다.

9. *App.Config* 파일을 선택 합니다.

   TestPackage가 중단점에서 로드 되 고 중지 됩니다.

## <a name="add-more-rules-for-ui-context"></a>UI 컨텍스트에 대 한 규칙 추가
 UI 컨텍스트 규칙은 부울 식 이므로 UI 컨텍스트에 대해 제한 된 규칙을 추가할 수 있습니다. 예를 들어 위의 UI 컨텍스트에서는 프로젝트가 포함 된 솔루션이 로드 될 때만 규칙이 적용 되도록 지정할 수 있습니다. 이러한 방식으로 프로젝트의 일부가 아닌 독립 실행형 파일로 *.config* 파일을 열면 명령이 표시 되지 않습니다.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT.SolutionHasSingleProject_string , VSConstants.UICONTEXT.SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 이제 식이 3 개의 용어를 참조 합니다. 처음 두 용어 "SingleProject" 및 "MultipleProjects"는 해당 Guid로 잘 알려진 다른 UI 컨텍스트를 참조 합니다. 세 번째 용어 "DotConfig"은이 문서의 앞부분에서 정의한 규칙 기반 UI 컨텍스트입니다.

## <a name="delayed-activation"></a>지연 된 활성화
 규칙에는 선택적 "Delay"가 있을 수 있습니다. 지연은 밀리초 단위로 지정 됩니다. 이 경우 지연으로 인해 해당 시간 간격에 따라 규칙의 UI 컨텍스트 활성화 또는 비활성화가 지연 됩니다. 규칙이 지연 간격 이전에 다시 변경 되 면 아무 일도 발생 하지 않습니다. 이 메커니즘을 사용 하 여 초기화 단계를 "스 태거" 할 수 있습니다. 특히 타이머에 의존 하거나 유휴 알림에 등록 하지 않고 일회성 초기화를 수행 합니다.

 예를 들어 100 밀리초의 지연 시간을 갖도록 테스트 로드 규칙을 지정할 수 있습니다.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>용어 유형

지원 되는 다양 한 유형의 용어는 다음과 같습니다.

|용어|Description|
|-|-|
|{nnnnnnnn-nnnn-nnnn-nnnnnnnnnnnn}|GUID는 UI 컨텍스트를 참조 합니다. 용어는 UI 컨텍스트가 활성화 될 때마다 true이 고, 그렇지 않으면 false입니다.|
|HierSingleSelectionName:\<pattern>|활성 계층의 선택 항목이 단일 항목이 고 선택한 항목의 이름이 "pattern"으로 지정 된 .Net 정규식과 일치 하는 경우에는 용어가 true가 됩니다.|
|UserSettingsStoreQuery:\<query>|"query"는 0이 아닌 값으로 평가 되어야 하는 사용자 설정 저장소의 전체 경로를 나타냅니다. 쿼리가 마지막 슬래시에서 "collection" 및 "propertyName"으로 분할 됩니다.|
|ConfigSettingsStoreQuery:\<query>|"query"는 0이 아닌 값으로 계산 되어야 하는 구성 설정 저장소의 전체 경로를 나타냅니다. 쿼리가 마지막 슬래시에서 "collection" 및 "propertyName"으로 분할 됩니다.|
|ActiveProjectFlavor:\<projectTypeGuid>|용어는 현재 선택 된 프로젝트가 flavored (집계) 되 고 지정 된 프로젝트 형식 GUID와 일치 하는 버전이 있는 경우에도 마찬가지입니다.|
|ActiveEditorContentType:\<contentType>|선택한 문서가 지정 된 콘텐츠 형식의 텍스트 편집기 인 경우 용어는 true가 됩니다. 참고: 선택한 문서의 이름이 변경 되 면 파일을 닫았다가 다시 열 때까지이 용어는 새로 고쳐지지 않습니다.|
|ActiveProjectCapability:\<Expression>|용어는 활성 프로젝트 기능이 제공 된 식과 일치 하는 경우 true입니다. 식에는 VB &#124; CSharp와 같은 요소가 있을 수 있습니다.|
|솔루션 Hasproject역량:\<Expression>|위와 비슷하지만, 식과 일치 하는 로드 된 프로젝트가 솔루션에 있는 경우 용어는 true입니다.|
|솔루션 Hasproject특색:\<projectTypeGuid>|솔루션에 flavored (집계) 된 프로젝트가 있고 지정 된 프로젝트 형식 GUID와 일치 하는 버전이 있는 경우에는 해당 용어가 항상 true가 됩니다.|
|Projectad이상 항목:\<pattern>| 용어는 "pattern"과 일치 하는 파일이 열려 있는 프로젝트에 추가 되는 경우 true입니다.|
|ActiveProjectOutputType:\<outputType>|활성 프로젝트에 대 한 출력 형식이 정확 하 게 일치 하는 경우 용어는 true입니다.  OutputType은 정수 또는 형식일 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> .|
|ActiveProjectBuildProperty:\<buildProperty>=\<regex>|활성 프로젝트에 지정 된 빌드 속성 및 속성 값이 제공 된 regex 필터와 일치 하는 경우 true입니다. 빌드 속성에 대 한 자세한 내용은 [MSBuild 프로젝트 파일의 데이터 유지](internals/persisting-data-in-the-msbuild-project-file.md) 를 참조 하세요.|
|솔루션 Hasprojectbuildproperty:\<buildProperty>=\<regex>|솔루션에 지정 된 빌드 속성 및 속성 값이 제공 된 regex 필터와 일치 하는 로드 된 프로젝트가 있는 경우 용어는 true입니다.|

## <a name="compatibility-with-cross-version-extension"></a>버전 간 확장과의 호환성

규칙 기반 UI 컨텍스트는 Visual Studio 2015의 새로운 기능이 며 이전 버전으로 이식할 수 없습니다. 이전 버전으로 이식 하지 않으면 여러 버전의 Visual Studio를 대상으로 하는 확장명/패키지와 관련 된 문제가 발생 합니다. 이러한 버전은 Visual Studio 2013 및 이전 버전에서 자동으로 로드 되어야 하지만, Visual Studio 2015에서 자동으로 로드 되지 않도록 규칙 기반 UI 컨텍스트의 이점을 누릴 수 있습니다.

이러한 패키지를 지원 하기 위해 레지스트리의 AutoLoadPackages 항목은 이제 값 필드에 플래그를 제공 하 여 Visual Studio 2015 이상에서 항목을 건너뛰어야 함을 나타낼 수 있습니다. 플래그 옵션을에 추가 하 여이 작업을 수행할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> . Vspackage는 이제 **SkipWhenUIContextRulesActive** 옵션을 해당 특성에 추가 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 하 여 Visual Studio 2015 이상에서 항목을 무시 하도록 지정할 수 있습니다.
## <a name="extensible-ui-context-rules"></a>확장 가능한 UI 컨텍스트 규칙

경우에 따라 패키지에서 정적 UI 컨텍스트 규칙을 사용할 수 없습니다. 예를 들어, 가져온 MEF 공급자가 지 원하는 편집기 유형을 기반으로 명령 상태를 지 원하는 확장성을 지 원하는 패키지가 있다고 가정 합니다. 현재 편집 유형을 지 원하는 확장이 있는 경우이 명령을 사용할 수 있습니다. 이러한 경우 사용 가능한 MEF 확장에 따라 용어는 변경 되므로 패키지 자체는 정적 UI 컨텍스트 규칙을 사용할 수 없습니다.

이러한 패키지를 지원 하기 위해 규칙 기반 UI 컨텍스트는 아래의 모든 용어를 또는에 조인할 수 있는 하드 코딩 된 식 "*"를 지원 합니다. 이를 통해 마스터 패키지는 알려진 규칙 기반 UI 컨텍스트를 정의 하 고 해당 명령 상태를이 컨텍스트에 연결할 수 있습니다. 그런 다음 마스터 패키지를 대상으로 하는 모든 MEF 확장은 다른 용어 또는 마스터 식에 영향을 주지 않고 지원 되는 편집기에 해당 용어를 추가할 수 있습니다.

생성자 <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> 설명서는 확장 가능한 UI 컨텍스트 규칙의 구문을 보여 줍니다.

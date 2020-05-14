---
title: '방법: 비주얼 스튜디오 확장에 규칙 기반 UI 컨텍스트 사용 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710590"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>방법: Visual Studio 확장에 규칙 기반 UI 컨텍스트 사용

Visual Studio를 사용하면 잘 알려진 <xref:Microsoft.VisualStudio.Shell.UIContext>특정 s가 활성화되면 VSPackage를 로드할 수 있습니다. 그러나 이러한 UI 컨텍스트는 세분화되지 않으므로 확장 작성자는 VSPackage를 실제로 로드하기를 원하는 지점 이전에 활성화되는 사용 가능한 UI 컨텍스트를 선택할 수 없습니다. 잘 알려진 UI 컨텍스트 목록은 을 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>참조하십시오.

패키지를 로드하는 것은 성능에 영향을 미칠 수 있으며 필요한 것보다 빨리 로드하는 것이 좋습니다. Visual Studio 2015에서는 확장 작성자가 UI 컨텍스트가 활성화되고 연결된 VSPackage가 로드되는 정확한 조건을 정의할 수 있는 메커니즘인 규칙 기반 UI 컨텍스트의 개념을 도입했습니다.

## <a name="rule-based-ui-context"></a>규칙 기반 UI 컨텍스트

"규칙"은 새 UI 컨텍스트(GUID)와 논리적 "및", "또는", "not" 작업과 결합된 하나 이상의 "용어"를 참조하는 부울 표현식으로 구성됩니다. "용어"는 런타임에 동적으로 평가되며 용어가 변경될 때마다 표현식이 다시 평가됩니다. 식이 true로 평가되면 연결된 UI 컨텍스트가 활성화됩니다. 그렇지 않으면 UI 컨텍스트가 비활성화됩니다.

규칙 기반 UI 컨텍스트는 다음과 같은 다양한 방법으로 사용할 수 있습니다.

1. 명령 및 도구 창에 대한 가시성 제약 조건을 지정합니다. UI 컨텍스트 규칙이 충족될 때까지 명령/도구 창을 숨길 수 있습니다.

2. 자동 로드 제약 조건: 규칙이 충족될 때만 자동 로드 패키지입니다.

3. 지연된 작업: 지정된 간격이 경과하고 규칙이 계속 충족될 때까지 로드를 지연합니다.

   메커니즘은 모든 Visual Studio 확장에서 사용할 수 있습니다.

## <a name="create-a-rule-based-ui-context"></a>규칙 기반 UI 컨텍스트 만들기
 *.config* 확장자를 가진 파일에만 적용되는 메뉴 명령을 제공하는 TestPackage라는 확장명이 있다고 가정합니다. VS2015 이전에는 UI 컨텍스트가 활성화되었을 <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> 때 TestPackage를 로드하는 것이 가장 좋습니다. 로드된 솔루션에 *.config* 파일이 없을 수도 있기 때문에 이러한 방식으로 TestPackage를 로드하는 것은 효율적이지 않습니다. 다음 단계에서는 *.config* 확장자를 가진 파일이 선택된 경우에만 규칙 기반 UI 컨텍스트를 사용하여 UI 컨텍스트를 활성화하고 해당 UI 컨텍스트가 활성화될 때 TestPackage를 로드하는 방법을 보여 준다.

1. 새 UIContext GUID를 정의하고 VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>클래스 및 에 추가합니다.

    예를 들어 새 UIContext "UIContextGuid"를 추가한다고 가정해 보겠습니다. 생성된 **GUID(도구** > **만들기 GUID를**클릭하여 GUID를 만들 수 있음)는 "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B"입니다. 그런 다음 패키지 클래스 에 다음 선언을 추가합니다.

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    특성의 경우 다음 값을 추가합니다(이러한 특성의 세부 정보는 나중에 설명합니다).

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    이러한 메타데이터는 새 UIContext GUID(8B40D5E2-5626-92AE-99EF-3DD1EFF46E7B)와 단일 용어인 "DotConfig"를 참조하는 식을 정의합니다. "DotConfig" 용어는 활성 계층 구조의 현재 선택 영역에 정규식 패턴 ".config$"(.config$)와\\일치하는 이름이 있는 경우 *true로*평가됩니다. (기본값) 값은 디버깅에 유용한 규칙에 대한 선택적 이름을 정의합니다.

    특성의 값은 나중에 빌드 시간 동안 생성된 pkgdef에 추가됩니다.

2. TestPackage 의 명령에 대한 VSCT 파일에서 적절한 명령에 "DynamicVisibility" 플래그를 추가합니다.

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. VSCT의 가시성 섹션에서 적절한 명령을 #1 정의된 새 UIContext GUID에 연결합니다.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. 기호 섹션에서 UIContext의 정의를 추가합니다.

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    이제 * \*.config* 파일에 대한 컨텍스트 메뉴 명령은 솔루션 탐색기에서 선택한 항목이 *.config* 파일이고 해당 명령 중 하나가 선택될 때까지 패키지가 로드되지 않는 경우에만 표시됩니다.

   그런 다음 디버거를 사용하여 패키지가 예상할 때만 로드되는지 확인합니다. 테스트 패키지를 디버깅하려면 다음을 수행하십시오.

5. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드에서 중단점을 설정합니다.

6. 테스트 패키지를 빌드하고 디버깅을 시작합니다.

7. 프로젝트를 만들거나 프로젝트를 엽니다.

8. *.config*. 이외의 확장자가 있는 파일을 선택합니다. 중단점은 적중해서는 안 됩니다.

9. *App.Config 파일을 선택합니다.*

   테스트 패키지는 중단점에서 로드되고 중지됩니다.

## <a name="add-more-rules-for-ui-context"></a>UI 컨텍스트에 대한 규칙 추가
 UI 컨텍스트 규칙은 부울 식이므로 UI 컨텍스트에 대해 더 제한된 규칙을 추가할 수 있습니다. 예를 들어 위의 UI 컨텍스트에서 프로젝트가 있는 솔루션이 로드된 경우에만 규칙이 적용되도록 지정할 수 있습니다. 이러한 방식으로 *.config* 파일을 프로젝트의 일부가 아닌 독립 실행형 파일로 열면 명령이 표시되지 않습니다.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 이제 식은 세 가지 용어를 참조합니다. 처음 두 용어인 "SingleProject" 및 "MultipleProject"는 GUID에서 잘 알려진 다른 UI 컨텍스트를 참조합니다. 세 번째 용어인 "DotConfig"는 이 문서의 앞에서 정의된 규칙 기반 UI 컨텍스트입니다.

## <a name="delayed-activation"></a>지연된 활성화
 규칙에는 선택적 "지연"이 있을 수 있습니다. 지연은 밀리초 단위로 지정됩니다. 이 지연으로 인해 규칙의 UI 컨텍스트의 활성화 또는 비활성화가 해당 시간 간격으로 지연됩니다. 지연 간격 전에 규칙이 다시 변경되면 아무 일도 일어나지 않습니다. 이 메커니즘은 타이머에 의존하거나 유휴 알림을 등록하지 않고 특히 일회성 초기화와 같은 초기화 단계를 "엇갈림"으로 지정하는 데 사용할 수 있습니다.

 예를 들어 테스트 부하 규칙을 100밀리초 지연하도록 지정할 수 있습니다.

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

지원되는 다양한 유형의 용어는 다음과 같습니다.

|용어|설명|
|-|-|
|{nnnnnn-nnnn-nnnn-nnnnnnnnnnnnnnnnnn}|GUID는 UI 컨텍스트를 참조합니다. UI 컨텍스트가 활성 상태이고 그렇지 않으면 false가 있을 때마다 이 용어는 true가 됩니다.|
|HierSingle선택 이름:\<패턴>|활성 계층 구조의 선택이 단일 항목이고 선택한 항목의 이름이 "pattern"에 의해 지정된 .Net 정규식과 일치할 때마다 이 용어는 true가 됩니다.|
|사용자 설정스토어쿼리:\<쿼리>|"쿼리"는 0이 아닌 값으로 평가해야 하는 사용자 설정 저장소에 대한 전체 경로를 나타냅니다. 쿼리는 마지막 슬래시에서 "컬렉션" 및 "propertyName"로 분할됩니다.|
|ConfigSettingsStoreQuery:\<쿼리>|"쿼리"는 구성 설정 저장소에 대한 전체 경로를 나타내며, 이 경로는 0이 아닌 값으로 평가해야 합니다. 쿼리는 마지막 슬래시에서 "컬렉션" 및 "propertyName"로 분할됩니다.|
|액티브 프로젝트\<맛 : 프로젝트유형>|이 용어는 현재 선택된 프로젝트가 맛을 내고(집계) 지정된 프로젝트 유형 GUID와 일치하는 맛을 가지면 사실입니다.|
|액티브에디터콘텐츠유형:\<컨텐스타입>|선택한 문서가 지정된 콘텐츠 형식의 텍스트 편집기인 경우 이 용어는 true가 됩니다. 참고: 선택한 문서의 이름이 바뀌면 파일이 닫혀 다시 열릴 때까지 이 용어가 새로 고쳐지지 않습니다.|
|활성 프로젝트\<기능: 표현식>|활성 프로젝트 기능이 제공된 식과 일치하는 경우 이 용어는 true입니다. 표현식은 VB &#124; CSharp와 같은 것일 수 있습니다.|
|솔루션HasProject기능:\<표현식>|위의 용어와 유사하지만 솔루션에 식과 일치하는 로드된 프로젝트가 있는 경우 해당 용어가 해당됩니다.|
|솔루션해시프로젝트맛:\<프로젝트타이드>|이 용어는 솔루션에 풍미(집계)되고 지정된 프로젝트 유형 GUID와 일치하는 맛이 있는 프로젝트가 있을 때마다 사실입니다.|
|프로젝트 추가항목:\<패턴>| "패턴"과 일치하는 파일이 열리는 soluion의 프로젝트에 추가될 때 이 용어는 마찬가지입니다.|
|액티브 프로젝트 출력\<유형: 출력 유형>|활성 프로젝트에 대한 출력 유형이 정확히 일치하는 경우 이 용어는 true입니다.  outputType은 정수 또는 형식일 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> 수 있습니다.|
|ActiveProjectBuildProperty:\<빌드속성\<>= 정규식>|활성 프로젝트에 지정된 빌드 속성 및 속성 값이 제공된 정규식 필터와 일치하는 경우 이 용어가 true입니다. 빌드 속성에 대한 자세한 내용은 [MSBuild 프로젝트 파일의 데이터 유지를](internals/persisting-data-in-the-msbuild-project-file.md) 참조하십시오.|
|솔루션HasProjectBuild속성:\<빌드속성\<>= 정규식>|이 용어는 솔루션에 지정된 빌드 속성 및 속성 값이 제공된 정규식 필터와 일치하는 로드된 프로젝트가 있는 경우 true입니다.|

## <a name="compatibility-with-cross-version-extension"></a>크로스 버전 확장과의 호환성

규칙 기반 UI 컨텍스트는 Visual Studio 2015의 새로운 기능이며 이전 버전으로 이식되지 않습니다. 이전 버전으로 이식하지 않는 경우 여러 버전의 Visual Studio를 대상으로 하는 확장/패키지에 문제가 발생합니다. 이러한 버전은 Visual Studio 2013 이전 버전에서 자동 로드되어야 하지만 Visual Studio 2015에서 자동 로드되지 않도록 규칙 기반 UI 컨텍스트의 이점을 활용할 수 있습니다.

이러한 패키지를 지원하기 위해 레지스트리의 AutoLoadPackage 항목은 이제 해당 값 필드에 플래그를 제공하여 Visual Studio 2015 이상에서 항목을 건너뛰도록 표시할 수 있습니다. 이 작업은 에 플래그 옵션을 <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>추가하여 수행할 수 있습니다. VSPackage이제 **건너뛰기UiContextRulesActive** 옵션을 해당 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 특성에 추가하여 Visual Studio 2015 이상에서 항목을 무시해야 함을 나타낼 수 있습니다.
## <a name="extensible-ui-context-rules"></a>확장 가능한 UI 컨텍스트 규칙

경우에 따라 패키지는 정적 UI 컨텍스트 규칙을 사용할 수 없습니다. 예를 들어 명령 상태가 가져온 MEF 공급자가 지원하는 편집기 형식을 기반으로 하는 확장성을 지원하는 패키지가 있다고 가정합니다. 현재 편집 유형을 지원하는 확장이 있는 경우 명령을 사용할 수 있습니다. 이러한 경우 패키지 자체는 사용 가능한 MEF 확장에 따라 용어가 변경되므로 정적 UI 컨텍스트 규칙을 사용할 수 없습니다.

이러한 패키지를 지원하기 위해 규칙 기반 UI 컨텍스트는 OR와 결합될 아래의 모든 용어를 나타내는 하드 코딩된 표현식 "*"을 지원합니다. 이렇게 하면 마스터 패키지가 알려진 규칙 기반 UI 컨텍스트를 정의하고 명령 상태를 이 컨텍스트에 연결할 수 있습니다. 이후에 마스터 패키지를 대상으로 하는 MEF 확장은 다른 용어나 마스터 표현식에 영향을 주지 않고 지원하는 편집자에 대한 용어를 추가할 수 있습니다.

생성자 <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> 설명서 확장 UI 컨텍스트 규칙에 대 한 구문을 보여 합니다.

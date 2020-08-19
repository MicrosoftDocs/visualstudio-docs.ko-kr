---
title: C++ 개체의 사용자 지정 뷰 만들기
description: Natvis 프레임워크를 사용하여 Visual Studio에서 디버거의 네이티브 형식이 표시되는 방식 사용자 지정
ms.date: 03/02/2020
ms.topic: how-to
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 37bfd1ab57fd0e37f32a55d5bfc3787cb0c0cbd2
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248059"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Natvis 프레임워크를 사용하여 디버거에서 C++ 개체의 사용자 지정 뷰 만들기

Visual Studio *Natvis* 프레임워크는 네이티브 형식이 디버거 변수 창(예: **지역** 및 **조사식** 창) 및 **DataTips**에 표시되는 방식을 사용자 지정합니다. Natvis 시각화를 사용하면 디버그하는 동안 만드는 형식을 더 잘 표시할 수 있습니다.

Natvis는 이전 버전 Visual Studio의 *autoexp.dat* 파일을 향상된 진단, 버전 관리 및 다중 파일 지원을 제공하는 XML 구문으로 대체합니다.

> [!NOTE]
> Natvis 사용자 지정은 클래스 및 구조체에서 작동하지만 typedef에는 적용되지 않습니다.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Natvis 시각화

만든 형식에 대한 시각화 규칙을 Natvis 프레임워크를 사용하여 만들면 개발자가 디버그 중 형식을 보다 쉽게 확인할 수 있습니다.

예를 들어 다음 그림에서는 [Windows::UI::Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) 형식의 변수를 사용자 지정 시각화가 적용되지 않은 디버거 창에서 보여 줍니다.

![TextBox 기본 시각화](../debugger/media/dbg_natvis_textbox_default.png "TextBox 기본 시각화")

강조 표시된 행은 `Text` 클래스의 `TextBox` 속성을 보여 줍니다. 복합 클래스 계층 구조를 사용하면 이 속성을 찾기가 어려워집니다. 디버거는 사용자 지정 문자열 형식을 해석하는 방법을 인식하지 않으므로 텍스트 상자에 들어 있는 문자열을 볼 수 없습니다.

Natvis 사용자 지정 시각화 도우미 규칙이 적용될 때 동일한 `TextBox`가 변수 창에서 훨씬 더 간단하게 보입니다. 클래스의 중요한 멤버가 함께 표시되며 디버거에서는 사용자 지정 문자열 형식의 기본 문자열 값을 표시합니다.

![시각화 도우미를 사용하는 TextBox 데이터](../debugger/media/dbg_natvis_textbox_visualizer.png "시각화 도우미를 사용하는 TextBox 데이터")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>C++ 프로젝트에서 .natvis 파일 사용

Natvis는 *.natvis* 파일을 사용하여 시각화 규칙을 지정합니다. *.natvis* 파일은 *.natvis* 확장을 포함하는 XML 파일입니다. Natvis 스키마는 *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*에 정의됩니다.

*.natvis* 파일의 기본 구조체는 시각화 항목을 나타내는 하나 이상의 `Type` 요소입니다. 각 `Type` 요소의 정규화된 이름은 해당 `Name` 특성에 지정됩니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio의 경우 몇 개의 *.natvis* 파일이 *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* 폴더에 제공됩니다. 이러한 파일은 많은 공통 형식에 대한 시각화 규칙을 포함하고, 새 형식에 대한 시각화를 작성하기 위한 예제로 활용할 수 있습니다.

### <a name="add-a-natvis-file-to-a-c-project"></a>C++ 프로젝트에 .natvis 파일 추가

모든 C++ 프로젝트에 *.natvis* 파일을 추가할 수 있습니다.

**새 *.natvis* 파일을 추가하려면**

1. **솔루션 탐색기**에서 C++ 프로젝트 노드를 선택하고 **프로젝트** > **새 항목 추가**를 선택하거나 프로젝트를 마우스 오른쪽 단추로 클릭하고 **새 항목** > **추가**를 선택합니다.

1. **새 항목 추가** 대화 상자에서 **Visual C++**  > **유틸리티** > **디버거 시각화 파일(.natvis)** 을 선택합니다.

1. 파일 이름을 지정하고 **추가**를 선택합니다.

   새 파일은 **솔루션 탐색기**에 추가되고 Visual Studio 문서 창에서 열립니다.

Visual Studio 디버거는 C++ 프로젝트에서 *.natvis* 파일을 자동으로 로드하며, 프로젝트를 빌드할 때에도 기본적으로 이 파일을 *.pdb* 파일에 포함시킵니다. 빌드된 앱을 디버그하는 경우 디버거는 프로젝트가 열려 있지 않은 경우에도 *.pdb* 파일에서 *.natvis* 파일을 로드합니다. *.natvis* 파일이 *.pdb*에 포함되지 않게 하려면 빌드된 *.pdb* 파일에서 제외할 수 있습니다.

***.pdb* 에서 *.natvis* 파일을 제외하려면**

1. **솔루션 탐색기**에서 *.natvis* 파일을 선택하고 **속성** 아이콘을 선택하거나 파일을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.

1. **빌드에서 제외** 옆의 화살표를 드롭다운하고 **예**를 선택한 후 **확인**을 선택합니다.

>[!NOTE]
>실행 가능 프로젝트를 디버그하는 경우에는 사용할 수 있는 C++ 프로젝트가 없으므로 솔루션 항목을 사용하여 *.pdb* 파일에 없는 *.natvis* 파일을 추가합니다.

>[!NOTE]
>*.pdb*에서 로드되는 Natvis 규칙은 *.pdb*가 참조하는 모듈의 형식에만 적용됩니다. 예를 들어 *Module1.pdb*에 `Test`라는 형식에 대한 Natvis 항목이 있는 경우 *Module1.dll*의 `Test` 클래스에만 이 항목이 적용됩니다. 다른 모듈에도 `Test`라는 클래스가 정의된 경우 *Module1.pdb* Natvis 항목은 이 클래스에 적용되지 않습니다.

**VSIX 패키지를 통해 *.natvis* 파일을 설치 및 등록하려면**

VSIX 패키지는 *.natvis* 파일을 설치하고 등록할 수 있습니다. 설치된 위치에 관계없이 등록된 모든 *.natvis* 파일은 디버깅 중에 자동으로 선택됩니다.

1. VSIX 패키지에 *.natvis* 파일을 포함합니다. 예를 들어 다음 프로젝트 파일의 경우

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. *source.extension.vsixmanifest* 파일에 *.natvis* 파일을 등록합니다.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a> Natvis 파일 위치

*.natvis* 파일을 여러 프로젝트에 적용하려는 경우에는 사용자 디렉터리 또는 시스템 디렉터리에 해당 파일을 추가합니다.

*.natvis* 파일은 다음 순서로 평가됩니다.

1. 로드된 프로젝트에 동일한 이름의 파일이 존재하지 않는 경우 디버그하는 *.pdb*에 포함된 *.natvis* 모든 파일.

2. 로드된 C++ 프로젝트 또는 최상위 솔루션에 있는 모든 *.natvis* 파일. 이 그룹에는 C++ 클래스 라이브러리를 비롯하여 로드된 모든 프로젝트가 포함되지만 다른 언어의 프로젝트는 포함되지 않습니다.

3. VSIX 패키지를 통해 설치 및 등록된 모든 *.natvis* 파일.

::: moniker range="vs-2017"

4. 사용자별 natvis 디렉터리(예: *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. 사용자별 Natvis 디렉터리(예: *%USERPROFILE%\Documents\Visual Studio 2019\Visualizers*).

::: moniker-end

5. 시스템 차원 Natvis 디렉터리( *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). 이 디렉터리에는 Visual Studio와 함께 설치되는 *.natvis* 파일이 있습니다. 관리자 권한이 있는 경우 이 디렉터리에 파일을 추가할 수 있습니다.

## <a name="modify-natvis-files-while-debugging"></a>디버그하는 동안 .natvis 파일 수정

프로젝트를 디버그하는 동안 IDE에서 *.natvis* 파일을 수정할 수 있습니다. 디버그 중인 동일한 Visual Studio 인스턴스에서 파일을 열고 수정하고 저장합니다. 파일이 저장되는 즉시 **조사식** 및 **지역** 창이 업데이트되어 변경 내용을 반영합니다.

디버그 중인 솔루션에서 *.natvis* 파일을 추가하거나 삭제할 수도 있습니다. 그러면 Visual Studio에서 관련 시각화를 추가하거나 제거합니다.

디버그하는 동안 *.pdb* 파일에 포함된 *.natvis* 파일을 업데이트할 수는 없습니다.

Visual Studio 외부에서 *.natvis* 파일을 수정하면 변경 내용이 자동으로 적용되지 않습니다. 디버거 창을 업데이트하려면 **직접 실행** 창에서 **.natvisreload** 명령을 다시 실행하면 됩니다. 그러면 디버깅 세션을 다시 시작하지 않아도 변경 내용이 적용됩니다.

또한 **.natvisreload** 명령을 사용하여 *.natvis* 파일을 최신 버전으로 업그레이드할 수 있습니다. 예를 들어 *.natvis* 파일이 소스 제어에 체크 인되었는데 다른 사용자가 수행한 최근 변경 내용을 선택하려고 할 수 있습니다.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> 식 및 형식 지정
Natvis 시각화에서는 C++ 식을 사용하여 표시할 데이터 항목을 지정합니다. 디버거에서 C++ 식의 기능 향상 및 제한 사항([컨텍스트 연산자(C++)](../debugger/context-operator-cpp.md)에 설명되어 있음) 외에도 다음 사항에 주의해야 합니다.

- Natvis 식은 현재 스택 프레임이 아닌 시각화되는 개체의 컨텍스트에서 평가됩니다. 예를 들어 Natvis 식의 `x`는 현재 함수의 **x**라는 지역 변수가 아니라 시각화되는 개체의 **x**라는 필드를 참조합니다. Natvis 식 내의 지역 변수에는 액세스할 수 없지만 전역 변수에는 액세스할 수 있습니다.

- Natvis 식에서는 함수 계산 또는 부작용이 허용되지 않습니다. 함수 호출 및 할당 연산자가 무시됩니다. [디버거 내장 함수](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) 는 부작용이 발생하지 않기 때문에 다른 함수 호출이 금지되어 있더라도 어떤 Natvis 식에서든 자유롭게 호출할 수 있습니다.

- 식이 표시되는 방식을 제어하기 위해 [C++의 형식 지정자](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers)에 설명된 모든 형식 지정자를 사용할 수 있습니다. [ArrayItems 확장](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)의 `Size` 식 같이 항목이 Natvis 내부에서 사용되는 경우에는 형식 지정자가 무시됩니다.

## <a name="natvis-views"></a>Natvis 뷰

여러 가지 방법으로 형식을 표시하는 다양한 Natvis 뷰를 정의할 수 있습니다. 예를 들어 다음은 `simple`이라는 간단한 뷰를 정의하는 `std::vector`의 시각화입니다. `DisplayString` 및 `ArrayItems` 요소는 기본 뷰와 `simple` 뷰에 표시되는 반면 `[size]` 및 `[capacity]` 항목은 `simple` 뷰에 표시되지 않습니다.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

**조사식** 창에서는 **,view** 형식 지정자를 사용하여 대체 뷰를 지정할 수 있습니다. 단순 보기는 **vec,view(simple)** 로 표시됩니다.

![단순 보기의 조사식 창](../debugger/media/watch-simpleview.png "단순 뷰의 조사식 창")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a> Natvis 오류

디버거는 시각화 항목에서 오류를 발견하면 이를 무시하고 형식을 원시 형식으로 표시하거나 다른 적합한 시각화를 선택합니다. Natvis 진단을 사용하여 디버거가 시각화 항목을 무시한 이유를 파악하고 기본 구문 및 구문 분석 오류를 확인할 수 있습니다.

**Natvis 진단을 켜려면**

- **도구** > **옵션**(또는 **디버그** > **옵션**) > **디버깅** > **출력 창**에서 **Natvis 진단 메시지(C++만 해당)** 를 **오류**, **경고** 또는 **자세한 정보**로 설정하고 **확인**을 선택합니다.

**출력** 창에 오류가 표시됩니다.

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Natvis 구문 참조

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> AutoVisualizer 요소
`AutoVisualizer` 요소는 *.natvis* 파일의 루트 노드이며 네임스페이스 `xmlns:` 특성을 포함합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

`AutoVisualizer` 요소는 [Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer) 및 [CustomVisualizer](#BKMK_CustomVisualizer) 자식을 포함할 수 있습니다.

### <a name="type-element"></a><a name="BKMK_Type"></a> Type 요소

기본 `Type`은 다음과 비슷합니다.

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 `Type` 요소는 다음을 지정합니다.

1. 시각화가 사용되는 대상 형식(`Name` 특성)

2. 이 형식의 개체 값이 표시되는 모양( `DisplayString` 요소)

3. 사용자가 변수 창에서 형식을 확장할 경우 형식 멤버가 표시되는 모양(`Expand` 노드)

#### <a name="templated-classes"></a>템플릿 기반 클래스
`Type` 요소의 `Name` 특성은 별표(`*`)를 템플릿 기반 클래스 이름에 사용할 수 있는 와일드카드 문자로 허용합니다.

다음 예제에서는 개체가 `CAtlArray<int>` 또는 `CAtlArray<float>`인지 관계없이 동일한 시각화가 사용됩니다. `CAtlArray<float>`에 대한 특정 시각화 항목이 있으면 일반적인 시각화 항목보다 우선 적용됩니다.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

매크로 $T1, $T2 등을 사용하여 시각화 항목에서 템플릿 매개 변수를 참조할 수 있습니다. 이러한 매크로의 예를 살펴보려면 Visual Studio와 함께 제공되는 *.natvis* 파일을 참조하세요.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> 시각화 도우미 형식 일치
시각화 항목이 유효성 검사에 실패하면 다음으로 사용 가능한 시각화가 사용됩니다.

#### <a name="inheritable-attribute"></a>상속 가능한 특성
선택적 `Inheritable` 특성은 시각화가 기본 형식에만 적용되는지 또는 기본 형식 및 모든 파생 형식에 적용되는지 여부를 지정합니다. `Inheritable` 의 기본값은 `true`입니다.

다음 예제에서 시각화는 `BaseClass` 형식에만 적용됩니다.

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Priority 특성

선택적 `Priority` 특성은 정의를 구문 분석하지 못하는 경우 대체 정의를 사용하는 순서를 지정합니다. `Priority`의 가능한 값은 `Low`, `MediumLow`,`Medium`, `MediumHigh`, `High`입니다. 기본값은 `Medium`입니다. `Priority` 특성은 동일한 *.natvis* 파일 내에서의 우선 순위만 구분합니다.

다음 예제에서는 먼저 2015 STL과 일치하는 항목을 구문 분석합니다. 구문 분석에 실패하는 경우 STL의 2013 버전용 대체 항목을 사용합니다.

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Optional 특성
모든 노드에 `Optional` 특성을 넣을 수 있습니다. 선택적 노드 내부의 하위 식이 구문 분석에 실패하는 경우 디버거는 해당 노드를 무시하지만 나머지 `Type` 규칙을 적용합니다. 다음 형식에서 `[State]` 는 필수이지만 `[Exception]` 은 선택적입니다.  `MyNamespace::MyClass`에 _`M_exceptionHolder`라는 필드가 있는 경우 `[State]` 노드와 `[Exception]` 노드가 모두 표시되지만 `_M_exceptionHolder` 필드가 없는 경우에는 `[State]` 노드만 표시됩니다.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> 조건 특성

선택적 `Condition` 특성은 많은 시각화 요소에 사용할 수 있으며 시각화 규칙을 사용할 시기를 지정합니다. 조건 특성 내부의 식이 `false`로 확인되면 시각화 규칙이 적용되지 않습니다. `true`로 계산되거나 `Condition` 특성이 없으면 시각화가 적용됩니다. 시각화 항목에서 if-else 논리에 대해 이 특성을 사용할 수 있습니다.

예를 들어 다음 시각화에는 스마트 포인터 형식에 대해 두 개의 `DisplayString` 요소가 있습니다. `_Myptr` 멤버가 비어 있으면 첫 번째 `DisplayString` 요소의 조건이 `true`로 확인되어 해당 양식이 표시됩니다. `_Myptr` 멤버가 비어 있지 않으면 조건이 `false`로 계산되고 두 번째 `DisplayString` 요소가 표시됩니다.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>IncludeView 및 ExcludeView 특성

`IncludeView` 및 `ExcludeView` 특성은 특정 뷰에 표시되거나 표시되지 않는 요소를 지정합니다. 예를 들어 다음 Natvis 사양 `std::vector`에서 `simple` 뷰에 `[size]` 및 `[capacity]` 항목이 표시되지 않습니다.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

`IncludeView` 및 `ExcludeView` 특성은 개별 멤버 및 형식에 사용할 수 있습니다.

### <a name="version-element"></a><a name="BKMK_Versioning"></a> Version 요소
`Version` 요소는 시각화 항목의 범위를 특정 모듈 및 버전으로 지정합니다. `Version` 요소를 사용하면 이름 충돌을 방지하고 실수로 인한 불일치를 줄이고 형식 버전마다 다른 시각화를 사용할 수 있습니다.

다른 모듈에서 사용되는 공통 헤더 파일에서 형식을 정의하는 경우 버전이 지정된 시각화는 지정된 모듈 버전에 형식이 있는 경우에만 표시됩니다.

이 예제에서는 버전 1.0부터 1.5 사이의 `Windows.UI.Xaml.dll`에서 확인할 수 있는 `DirectUI::Border` 형식에만 시각화를 적용할 수 있습니다.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

`Min` 및 `Max`가 모두 필요하지는 않습니다. 이들은 선택적 특성입니다. 와일드카드 문자가 지원되지 않습니다.

`Name` 특성은 *filename. ext* 형식으로 되어 있습니다(예: *hello.exe* 또는 *some.dll*). 경로 이름이 허용되지 않습니다.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a> DisplayString 요소
`DisplayString` 요소는 변수의 값으로 표시할 문자열을 지정합니다. 또한 식과 혼합된 임의의 문자열을 허용합니다. 중괄호 내의 모든 항목은 식으로 해석됩니다. 예를 들어, 다음 `DisplayString` 항목은

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

`CPoint` 형식의 변수가 다음 그림과 같이 표시됨을 의미합니다.

 ![DisplayString 요소 사용](../debugger/media/dbg_natvis_cpoint_displaystring.png "DisplayString 요소 사용")

`DisplayString` 식에서 `CPoint`의 멤버인 `x` 및 `y`는 중괄호 내에 있으므로 해당 값이 계산됩니다. 또한 이 예제에서 이중 중괄호(`{{` 또는 `}}` )를 사용하여 중괄호를 이스케이프하는 방법을 확인할 수 있습니다.

> [!NOTE]
> `DisplayString` 요소는 임의 문자열 및 중괄호 구문을 허용하는 유일한 요소입니다. 다른 모든 시각화 요소는 디버거가 계산할 수 있는 식만 허용합니다.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a> StringView 요소

`StringView` 요소는 디버거가 기본 제공 텍스트 시각화 도우미에 보낼 수 있는 값을 정의합니다. 예를 들어 `ATL::CStringT` 형식에 다음 시각화가 제공될 경우

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

`CStringT` 개체는 변수 창에 다음 예제와 같이 표시됩니다.

![CStringT DisplayString 요소](../debugger/media/dbg_natvis_displaystring_cstringt.png "CStringT DisplayString 요소")

`StringView` 요소는 디버거에게 값을 텍스트 시각화로 표시하도록 지시합니다.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

디버그하는 동안 변수 옆에 있는 돋보기 아이콘을 선택하고 **텍스트 시각화 도우미**를 선택하여 **m_pszData**가 가리키는 문자열을 표시할 수 있습니다.

 ![StringView 시각화 도우미가 있는 CStringT 데이터](../debugger/media/dbg_natvis_stringview_cstringt.png "StringView 시각화 도우미가 있는 CStringT 데이터")

`{m_pszData,su}` 식에는 값을 유니코드 문자열로 표시하기 위한 C++ 형식 지정자 **su**가 포함되어 있습니다. 자세한 내용은 [C++의 형식 지정자](../debugger/format-specifiers-in-cpp.md) 를 참조하세요.

### <a name="expand-element"></a><a name="BKMK_Expand"></a> Expand 요소

선택적 `Expand` 노드는 변수 창에서 형식을 확장할 때 시각화된 형식의 자식을 사용자 지정합니다. `Expand` 노드는 자식 요소를 정의하는 자식 노드의 목록을 허용합니다.

- 시각화 항목에 `Expand` 노드가 지정되지 않은 경우 자식은 기본 확장 규칙을 사용합니다.

- `Expand` 노드가 아래에 자식 노드 없이 지정된 경우 형식을 디버거 창에서 확장할 수 없습니다.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> 항목 확장

 `Item` 요소는 `Expand` 노드의 가장 기본적이고 공통적인 요소입니다. `Item` 은 단일 자식 요소를 정의합니다. 예를 들어 `top`, `left`, `right`및 `bottom` 필드가 있는 `CRect` 클래스에는 다음 시각화 항목이 있습니다.

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

디버거 창에서 `CRect` 형식은 다음 예제와 같이 표시됩니다.

![Item 요소 확장이 있는 CRect](../debugger/media/dbg_natvis_expand_item_crect1.png "Item 요소 확장이 있는 CRect")

디버거는 `Width` 및 `Height` 요소에 지정된 식을 계산하고 변수 창의 **값** 열에 값을 표시합니다.

디버거는 모든 사용자 지정 확장에 **[Raw 뷰]** 노드를 자동으로 만듭니다. 위의 스크린샷은 개체의 기본 Raw 뷰가 Natvis 시각화와 어떻게 다른지를 보여 주기 위해 확장된 **[Raw 뷰]** 노드를 표시합니다. 기본 확장은 기본 클래스의 하위 트리를 생성하고 기본 클래스의 모든 데이터 멤버를 자식으로 나열합니다.

> [!NOTE]
> 항목 요소의 식이 복합 형식을 가리키는 경우 **항목** 노드 자체를 확장할 수 있습니다.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> Size
`ArrayItems` 노드를 사용하면 Visual Studio 디버거가 형식을 배열로 해석하고 해당 개별 요소를 표시하도록 할 수 있습니다. `std::vector` 에 대한 시각화는 좋은 예입니다.

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

`std::vector` 는 변수 창에서 확장되는 경우 개별 요소를 표시합니다.

![ArrayItems 확장을 사용하는 std::vector](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "ArrayItems 확장을 사용하는 std::vector")

`ArrayItems` 노드에는 다음 항목이 있어야 합니다.

- 디버거에서 배열의 길이를 파악하기 위한 `Size` 식(정수로 계산되어야 함)입니다.
- 첫 번째 요소를 가리키는 `ValuePointer` 식(`void*`가 아닌 요소 형식의 포인터여야 함).

배열 하한의 기본값은 0입니다. 값을 재정의하려면 `LowerBound` 요소를 사용합니다. Visual Studio와 함께 제공되는 *.natvis* 파일에는 예제가 있습니다.

>[!NOTE]
>형식 자체(예: `CATLArray`)가 이 연산자를 허용하지 않더라도 `ArrayItems`를 사용하는 모든 단차원 배열 시각화에서 `[]` 연산자(예: `vector[i]`)를 사용할 수 있습니다.

다차원 배열도 지정할 수 있습니다. 이 경우 디버거는 자식 요소를 올바르게 표시하는 데 약간의 정보가 필요합니다.

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction`은 배열이 행 중심 순서인지 열 중심 순서인지를 지정합니다.
- `Rank` 는 배열의 차수를 지정합니다.
- `Size` 요소는 해당 차원에서 배열의 길이를 확인하기 위해 차원 인덱스로 대체되는 암시적 `$i` 매개 변수를 허용합니다. 예를 들어 이전 예제에서 `_M_extent.M_base[0]` 식에는 0차원의 길이를 지정하고, `_M_extent._M_base[1]` 식에는 1차원의 길이를 지정해야 합니다.

다음은 2차원 `Concurrency::array` 개체가 디버거 창에서 어떻게 나타나는지를 보여 줍니다.

![ArrayItems 확장이 있는 2차원 배열](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "ArrayItems 확장이 있는 2차원 배열")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> IndexListItems 확장

메모리에 배열 요소가 연속적으로 배치된 경우에만 `ArrayItems` 확장을 사용할 수 있습니다. 디버거는 단순히 포인터를 늘리는 방식으로 다음 요소로 이동합니다. 값 노드에 대한 인덱스를 조작해야 하는 경우 `IndexListItems` 노드를 사용합니다. `IndexListItems` 노드를 사용하는 시각화는 다음과 같습니다.

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

`ArrayItems`와 `IndexListItems` 간의 유일한 차이점은 암시적 `$i` 매개 변수와 함께 i<sup></sup>번째 요소에 대한 전체 식이 필요한 `ValueNode`입니다.

>[!NOTE]
>형식 자체(예: `CATLArray`)가 이 연산자를 허용하지 않더라도 `IndexListItems`를 사용하는 모든 단차원 배열 시각화에서 `[]` 연산자(예: `vector[i]`)를 사용할 수 있습니다.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> LinkedListItems 확장

시각화된 형식이 링크된 목록을 나타내는 경우 디버거에서는 `LinkedListItems` 노드를 사용하여 해당 자식을 표시할 수 있습니다. `CAtlList` 형식에 대한 다음 시각화는 `LinkedListItems`를 사용합니다.

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

`Size` 요소는 목록의 길이를 참조합니다. `HeadPointer` 는 첫 번째 요소를 가리키고, `NextPointer` 는 다음 요소를 참조하며, `ValueNode` 는 항목의 값을 참조합니다.

디버거는 `NextPointer` 및 `ValueNode` 식을 부모 목록 형식이 아닌 `LinkedListItems` 노드 요소의 컨텍스트에서 계산합니다. 앞의 예제에서 `CAtlList`에는 연결된 목록의 노드인 `CNode` 클래스(`atlcoll.h`에 있음)가 있습니다. `m_pNext` 및 `m_element`는 `CAtlList` 클래스가 아니라 해당 `CNode` 클래스의 필드입니다.

`ValueNode`는 비어 있거나 `this`를 사용하여 `LinkedListItems` 노드 자체를 참조할 수 있습니다.

#### <a name="customlistitems-expansion"></a>CustomListItems 확장

`CustomListItems` 확장을 사용하여 해시 테이블 같은 데이터 구조 전송에 대한 사용자 지정 논리를 작성할 수 있습니다. `CustomListItems`를 사용하면 계산해야 하는 모든 항목에 C++ 식을 사용할 수 있는 데이터 구조체를 시각할 수 있지만, `ArrayItems`, `IndexListItems` 또는 `LinkedListItems`에는 적합하지 않습니다.

`Exec`를 사용하여 확장에 정의된 변수 및 개체를 사용하여 `CustomListItems` 확장 내에서 코드를 실행할 수 있습니다. `Exec`에서 논리 연산자, 산술 연산자 및 대입 연산자를 사용할 수 있습니다. C++ 식 계산기에서 지원되는 [디버거 내장 함수](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state)를 제외하고 `Exec`를 사용하여 함수를 계산할 수 없습니다.

`CAtlMap`에 대한 다음 시각화 도우미는 `CustomListItems`가 적합한 좋은 예입니다.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> TreeItems 확장
 시각화된 형식이 트리를 나타내는 경우 디버거에서는 `TreeItems` 노드를 사용하여 트리를 단계별로 진행하면서 해당 자식을 표시할 수 있습니다. 다음은 `TreeItems` 노드를 사용하는 `std::map` 형식에 대한 시각화입니다.

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

이 구문은 `LinkedListItems` 노드와 비슷합니다. `LeftPointer`, `RightPointer` 및 `ValueNode`는 트리 노드 클래스의 컨텍스트에서 평가됩니다. `ValueNode`는 비어 있거나 `this`를 사용하여 `TreeItems` 노드 자체를 참조할 수 있습니다.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> ExpandedItem 확장
 `ExpandedItem` 요소는 기본 클래스 또는 데이터 멤버를 시각화된 형식의 자식이었던 것처럼 표시하는 방식으로 집계된 자식 뷰를 생성합니다. 디버거는 지정된 식을 계산하고 결과의 자식 노드를 시각화된 형식의 자식 목록에 추가합니다.

예를 들어, 스마트 포인터 `auto_ptr<vector<int>>` 형식은 일반적으로 다음과 같이 표시됩니다.

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; 기본 확장](../debugger/media/dbg_natvis_expand_expandeditem_default.png "기본 확장")

 벡터 값을 확인하려면 변수 창에서 두 개의 수준을 드릴다운하여 `_Myptr` 멤버를 통과해야 합니다. `ExpandedItem` 요소를 추가하면 계층 구조에서 `_Myptr` 변수를 제거하고 벡터 요소를 바로 확인할 수 있습니다.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;vector&#60;int&#62;&#62; ExpandedItem 확장](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "ExpandedItem 확장")

다음 예제에서는 파생 클래스에서 기본 클래스의 속성을 집계하는 방법을 보여 줍니다. `CPanel` 클래스가 `CFrameworkElement`에서 파생된다고 가정해 보겠습니다. `ExpandedItem` 노드 시각화는 기본 `CFrameworkElement` 클래스에서 가져온 속성을 반복하는 대신, 이러한 속성을 `CPanel` 클래스의 자식 목록에 추가합니다.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

이때 파생된 클래스에 대해 시각화 일치를 해제하는 **nd** 형식 지정자가 필요합니다. 이 형식 지정자가 없으면 `*(CFrameworkElement*)this` 식으로 인해 `CPanel` 시각화가 다시 적용되는데, 이는 기본 시각화 형식 일치 규칙에서 이를 가장 적합한 것으로 인식하기 때문입니다. **nd** 형식 지정자를 사용하여 디버거가 기본 클래스 시각화를 사용하거나 기본 클래스에 시각화가 없는 경우 기본 확장을 사용하도록 지시합니다.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a> 가상 항목 확장
 `ExpandedItem` 요소는 계층 구조를 제거하여 데이터를 보다 평면적으로 표시하지만 `Synthetic` 노드는 그 반대입니다. 이를 통해 식의 결과가 아닌 인위적 자식 요소를 만들 수 있습니다. 인위적 요소에는 자체 자식 요소가 있을 수 있습니다. 다음 예의 `Concurrency::array` 형식에 대한 시각화에서는 사용자에게 진단 메시지를 표시하기 위해 `Synthetic` 노드를 사용합니다.

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![가상 요소 확장이 있는 Concurrency::Array](../debugger/media/dbg_natvis_expand_synthetic.png "가상 요소 확장이 있는 Concurrency::Array")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a> HResult 요소
 `HResult` 요소를 사용하면 디버거 창에서 **HRESULT**에 대해 표시되는 정보를 사용자 지정할 수 있습니다. `HRValue` 요소에는 사용자 지정할 **HRESULT**의 32비트 값이 포함되어 있어야 합니다. `HRDescription` 요소에는 디버거 창에 표시할 정보가 포함되어 있습니다.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a> UIVisualizer 요소
`UIVisualizer` 요소는 디버거에 그래픽 시각화 도우미 플러그 인을 등록합니다. 그래픽 시각화 도우미는 해당 데이터 형식과 일치하는 방식으로 변수 또는 개체를 표시하는 대화 상자 또는 다른 인터페이스를 만듭니다. 시각화 도우미 플러그 인은 [VSPackage](../extensibility/internals/vspackages.md)로 작성해야 하며 디버거에서 사용할 수 있는 서비스를 노출해야 합니다. *.natvis* 파일에는 플러그 인의 이름, 노출된 서비스의 GUID, 시각화할 수 있는 형식 같은 플러그 인 등록 정보가 포함되어 있습니다.

UIVisualizer 요소의 예는 다음과 같습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- `ServiceId` - `Id` 특성 쌍은 `UIVisualizer`를 식별합니다. `ServiceId`는 시각화 도우미 패키지에서 노출하는 서비스의 GUID입니다. `Id`는 서비스에서 두 개 이상 제공하는 경우 시각화 도우미를 구분하는 고유 식별자입니다. 위의 예제에서는 동일한 시각화 도우미 서비스에서 두 개의 시각화 도우미를 제공합니다.

- `MenuName` 특성은 디버거의 돋보기 아이콘 옆에 있는 드롭다운에 표시되는 시각화 도우미 이름을 정의합니다. 예를 들어:

  ![UIVisualizer 메뉴 바로 가기 메뉴](../debugger/media/dbg_natvis_vectorvisualizer.png "UIVisualizer 메뉴 바로 가기 메뉴")

*.natvis* 파일에 정의된 각 형식에는 해당 형식을 표시할 수 있는 모든 UI 시각화 도우미가 명시적으로 나열되어야 합니다. 디버거는 형식 항목의 시각화 도우미 참조를 등록된 시각화 도우미와 일치시킵니다. 예를 들어 `std::vector`에 대한 다음 형식 항목은 앞의 예제에서 `UIVisualizer`를 참조합니다.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 메모리 내 비트맵을 보는 데 사용되는 [이미지 조사식](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) 확장의 `UIVisualizer` 예시를 볼 수 있습니다.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>CustomVisualizer 요소
 `CustomVisualizer`는 Visual Studio 코드에서 시각화를 제어하기 위해 작성하는 VSIX 확장을 지정하는 확장 지점입니다. VSIX 확장 작성 방법에 대한 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하세요.

사용자 지정 시각화 도우미를 작성하는 데에는 XML Natvis 정의보다 많은 작업이 필요하지만 Natvis에서 지원하거나 지원하지 않는 사항을 신경쓰지 않아도 됩니다. 사용자 지정 시각화 도우미는 디버거 프로세스를 쿼리하고 수정하거나 Visual Studio의 다른 부분과 통신할 수 있는 전체 디버거 확장 API에 액세스할 수 있습니다.

 `CustomVisualizer` 요소에 `Condition`, `IncludeView` 및 `ExcludeView` 특성을 사용할 수 있습니다.

## <a name="limitations"></a>제한 사항

Natvis 사용자 지정은 클래스 및 구조체에서 작동하지만 typedef에는 적용되지 않습니다.

Natvis는 기본 형식(예: `int`, `bool`) 또는 기본 형식 포인터에 대한 시각화 도우미를 지원하지 않습니다. 이 시나리오에서 한 가지 옵션은 사용 사례에 적합한 [형식 지정자](../debugger/format-specifiers-in-cpp.md)를 사용하는 것입니다. 예를 들어 코드에서 `double* mydoublearray`를 사용하는 경우 디버거의 **조사식** 창에서 처음 100개 요소를 표시하는 `mydoublearray, [100]` 식과 같은 배열 형식 지정자를 사용할 수 있습니다.

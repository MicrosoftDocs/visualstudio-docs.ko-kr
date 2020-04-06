---
title: VSIX 컬러 에디터 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa3ed1f1a2a761a6602ac891eb78b5a5436abf92
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704037"
---
# <a name="vsix-color-editor"></a>VSIX 색 편집기
비주얼 스튜디오 확장 색상 편집기 도구를 만들고 Visual Studio에 대 한 사용자 지정 색상을 편집할 수 있습니다. 이 도구는 색상이 코드에서 사용할 수 있도록 테마 리소스 키를 생성할 수도 있습니다. 이 도구는 테마를 지원하는 Visual Studio 확장의 색상을 만드는 데 유용합니다. 이 도구는 .pkgdef 및 .xml 파일을 열 수 있습니다. 비주얼 스튜디오 테마 (.vstheme 파일)는 .xml파일 확장을 변경하여 비주얼 스튜디오 확장 색상 편집기와 함께 사용할 수 있습니다. 또한 .vstheme 파일을 현재 .xml 파일로 가져올 수 있습니다.

 ![VSIX 색 편집기 Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX 색 편집기 Hero")

 **패키지 정의 파일**

 패키지 정의(.pkgdef) 파일은 테마를 정의하는 파일입니다. 색상 자체는 .pkgdef 파일로 컴파일되는 테마 색상 .xml 파일에 저장됩니다. .pkgdef 파일은 Visual Studio 검색 가능한 위치에 배포되고 런타임에 처리되며 함께 병합되어 테마를 정의합니다.

 **색상 토큰**

 색상 토큰은 다음 네 가지 요소로 구성됩니다.

- **범주 이름:** 색상 집합에 대한 논리적 그룹입니다. 원하는 UI 요소 또는 UI 요소 그룹에 특정한 색상이 이미 있는 경우 기존 범주 이름을 사용합니다.

- **토큰 이름:** 색상 토큰 및 토큰 집합에 대한 설명이 있는 이름입니다. 집합에는 배경 및 전경(텍스트) 토큰 이름과 모든 상태가 포함되며, 해당 상태와 쌍을 쉽게 식별할 수 있도록 이름을 지정해야 합니다.

- **색상 값(또는 색조):** 각 컬러 테마에 필요합니다. 항상 배경 및 텍스트 색상 값을 쌍으로 만듭니다. 색상은 배경/전경에 대해 쌍을 이루므로 텍스트(전경) 색상은 항상 그려지는 배경 색에 대해 읽을 수 있습니다. 이러한 색상은 연결되며 UI에서 함께 사용됩니다. 배경이 텍스트와 함께 사용하기 위한 것이 아닌 경우 전경 색상을 정의하지 마십시오.

- **시스템 색상 이름:** 고대비 디스플레이에 사용하십시오.

## <a name="how-to-use-the-tool"></a>이 도구를 사용 하는 방법
 가능한 한 적절한 경우 기존 Visual Studio 색상을 새 색상을 만드는 대신 다시 사용해야 합니다. 그러나 적절한 색상이 정의되지 않은 경우 확장 테마를 호환 상태로 유지하려면 사용자 지정 색상을 만들어야 합니다.

 **새 색상 토큰 만들기**

 Visual Studio 확장 색상 편집기를 사용하여 사용자 지정 색상을 만들려면 다음 단계를 따르십시오.

1. 새 색상 토큰의 범주 및 토큰 이름을 결정합니다.

2. UI 요소가 각 테마에 사용할 색조와 고대비의 시스템 색상을 선택합니다.

3. 색상 편집기를 사용하여 새 색상 토큰을 만듭니다.

4. Visual Studio 확장의 색상을 사용합니다.

5. Visual Studio에서 변경 내용을 테스트합니다.

   **1단계: 새 색상 토큰의 범주 및 토큰 이름을 결정합니다.**

   VSColor에 대 한 기본 명명 체계는 **[범주] [UI 형식] [상태]** 입니다. VSColor 이름에 "color"라는 단어는 중복되어 있으므로 사용하지 마십시오.

   범주 이름은 논리적 그룹을 제공하며 가능한 한 좁게 정의해야 합니다. 예를 들어 단일 도구 창의 이름은 범주 이름이 될 수 있지만 전체 사업부 또는 프로젝트 팀의 이름은 그렇지 않습니다. 항목을 범주로 그룹화하면 이름이 같은 색상 간의 혼동을 방지할 수 있습니다.

   토큰 이름은 색상이 적용되는 요소 유형과 상황 또는 "상태"를 명확하게 나타내야 합니다. 예를 들어 활성 데이터 팁의 **[UI 형식]의** 이름을 **"DataTip"** 및 **[상태]의** 이름을 **"활성"으로**지정하여 **"DataTipActive"의**색상 이름을 지정할 수 있습니다. 데이터 팁에는 텍스트가 있기 때문에 전경과 배경 색을 모두 정의해야 합니다. 배경/전경 페어링을 사용하면 색상 편집기에서 배경에 대한 **"DataTipActive"** 및 전경에 대한 **"DataTipActiveText"** 색을 자동으로 만듭니다.

   UI에 상태가 하나만 있는 경우 이름의 **[State]** 부분을 생략할 수 있습니다. 예를 들어 검색 상자에 테두리가 있고 테두리의 색상에 영향을 주는 상태 변경이 없는 경우 테두리의 색상 토큰 이름을 **"SearchBoxBorder"라고**간단히 호출할 수 있습니다.

   몇 가지 일반적인 상태 이름은 다음과 같습니다.

- Active

- 비활성

- MouseOver

- Mousedown

- 선택

- 포커스 있음

  목록 항목 컨트롤의 일부에 대한 몇 가지 토큰 이름의 예:

- ListItem

- 목록항목경계

- 목록항목마우스오버

- 목록항목마우스오버보더보더

- 목록항목 선택됨

- 목록항목선택국경

- 목록항목 사용 안 함

- 목록항목장애인국경

  **2단계: UI 요소가 각 테마에 사용할 색조와 고대비의 시스템 색상을 선택합니다.**

  UI에 대한 사용자 지정 색상을 선택할 때 유사한 기존 UI 요소를 선택하고 해당 색상을 기본으로 사용합니다. 즉시 사용 가능한 UI 요소의 색상은 검토 및 테스트를 거쳤기 때문에 모든 테마에서 적절히 보이고 올바르게 행동합니다.

  **3 단계 : 색상 편집기를 사용하여 새 색상 토큰을 만듭니다.**

  색상 편집기를 실행하고 새 사용자 지정 테마 색상 .xml 파일을 열거나 만듭니다. 메뉴에서 **새 색상 > 편집을** 선택합니다. 이렇게 하면 범주를 지정하기 위한 대화 상자와 해당 범주 내의 색상 항목에 대한 하나 이상의 이름이 열립니다.

  ![VSIX 색 편집기 새 색](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX 색 편집기 새 색")

  기존 범주를 선택하거나 **새 범주를** 선택하여 새 범주를 만듭니다. 다른 대화 상자가 열리고 새 범주 이름이 생성됩니다.

  ![VSIX 색 편집기 새 범주](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX 색 편집기 새 범주")

  그러면 새 색상 범주 드롭다운 메뉴에서 **새 범주를** 사용할 수 있습니다. 범주를 선택한 후 각 새 색상 토큰에 대해 줄당 하나의 이름을 입력하고 완료되면 "만들기"를 선택합니다.

  ![VSIX 색 편집기 새 색 채워짐](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX 색 편집기 새 색 채워짐")

  색상 값은 배경/전경 쌍으로 표시되며 색상이 정의되지 않음을 나타내는 "없음"이 표시됩니다. 참고: 색상에 텍스트 색상/배경 색 쌍이 없는 경우 배경만 정의하면 됩니다.

  ![VSIX 색 편집기 색 값](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX 색 편집기 색 값")

  색상 토큰을 편집하려면 해당 토큰의 테마(열)에 대한 색상 항목을 선택합니다. 8자리 ARGB 형식으로 육수 색상 값을 입력하거나, 셀에 시스템 색상 이름을 입력하거나, 드롭다운 메뉴를 사용하여 색상 슬라이더 세트 또는 시스템 색상 목록을 통해 원하는 색상을 선택하여 색상 값을 추가합니다.

  ![VSIX 색 편집기 색 편집](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX 색 편집기 색 편집")

  ![VSIX 색 편집기 배경](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX 색 편집기 배경")

  텍스트를 표시할 필요가 없는 구성요소의 경우 하나의 색상 값인 배경색만 입력합니다. 그렇지 않으면 앞으로 슬래시로 구분된 배경 색과 텍스트 색상 모두에 대한 값을 입력합니다.

  고대비 값을 입력할 때 유효한 Windows 시스템 색상 이름을 입력합니다. 하드 코딩된 ARGB 값을 입력하지 마십시오. 색상 값 드롭다운 메뉴에서 "배경: 시스템" 또는 "전경: 시스템"을 선택하여 유효한 시스템 색상 이름 목록을 볼 수 있습니다. 텍스트 구성 요소가 있는 요소를 만들 때 올바른 배경/텍스트 시스템 색상 쌍을 사용하거나 텍스트를 읽을 수 없습니다.

  색상 토큰 만들기, 설정 및 편집을 마치면 원하는 .xml 또는 .pkgdef 형식으로 저장합니다. 배경이나 전경 세트가 없는 색상 토큰은 .xml 형식으로 빈 색상으로 저장되지만 .pkgdef 형식으로 삭제됩니다. .pkgdef 파일에 빈 색상을 저장하려고 하면 대화 상자에서 색상 손실이 발생할 수 있습니다.

  **4단계: Visual Studio 확장의 색상을 사용합니다.**

  새 색상 토큰을 정의한 후 프로젝트 파일에 .pkgdef를 "콘텐츠 빌드"로 설정하고 "VSIX에 포함"을 "True"로 설정합니다.

  ![VSIX 색 편집기 pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX 색 편집기 pkgdef")

  Visual Studio 확장 색상 편집기에서 파일 > 보기 리소스 코드를 선택하여 WPF 기반 UI의 사용자 지정 색상에 액세스하는 데 사용되는 코드를 봅니다.

  ![VSIX 색 편집기 리소스 코드 뷰어](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX 색 편집기 리소스 코드 뷰어")

  이 코드를 프로젝트의 정적 클래스에 포함합니다. **마이크로소프트.비주얼 스튜디오.쉘에 대\< 한 참조. VSVersion>.0.dll** **테마리소스키** 유형을 사용하려면 프로젝트에 추가해야 합니다.

```csharp
namespace MyCustomColors
{
    public static class MyCategory
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.
        public static readonly Guid Category = new Guid("faf7f3f9-9fe5-4dd3-9350-59679617dfbe");

        private static ThemeResourceKey _MyColor1ColorKey;
        private static ThemeResourceKey _MyColor1BrushKey;
        private static ThemeResourceKey _MyColor1TextColorKey;
        private static ThemeResourceKey _MyColor1TextBrushKey;
        public static ThemeResourceKey MyColor1ColorKey { get { return _MyColor1ColorKey ?? (_MyColor1ColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundColor)); } }
        public static ThemeResourceKey MyColor1BrushKey { get { return _MyColor1BrushKey ?? (_MyColor1BrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.BackgroundBrush)); } }
        public static ThemeResourceKey MyColor1TextColorKey { get { return _MyColor1TextColorKey ?? (_MyColor1TextColorKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundColor)); } }
        public static ThemeResourceKey MyColor1TextBrushKey { get { return _MyColor1TextBrushKey ?? (_MyColor1TextBrushKey = new ThemeResourceKey(Category, "MyColor1", ThemeResourceKeyType.ForegroundBrush)); } }
        #endregion
    }
}
```

 이렇게 하면 XAML 코드의 색상에 액세스할 수 있으며 UI가 테마 변경 사항에 응답할 수 있습니다.

```xaml
<UserControl x:Class="NewTestProject.TestPackageControl" Name="MyToolWindow"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:ns="clr-namespace:MyCustomColors">
  <Grid>
    <TextBlock Background="{DynamicResource {x:Static ns:MyCategory.MyColor1BrushKey}}"
               Foreground="{DynamicResource {x:Static ns:MyCategory.MyColor1TextBrushKey}}"
      >Sample Text</TextBlock>

  </Grid>
</UserControl>
```

 **5단계: Visual Studio의 변경 내용을 테스트합니다.**

 색상 편집기는 확장 패키지를 다시 빌드하지 않고 Visual Studio의 실행 중인 인스턴스에 색상 토큰을 일시적으로 적용하여 색상에 대한 실시간 변경 내용을 볼 수 있습니다. 이렇게 하려면 각 테마 열의 헤더에 있는 "이 테마 적용" 단추를 클릭합니다. 이 임시 테마는 VSIX 컬러 편집기닫을 때 사라집니다.

 ![VSIX 색 편집기 적용](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX 색 편집기 적용")

 변경 내용을 영구적으로 만들려면 .pkgdef 파일에 새 색상을 추가하고 해당 색상을 사용하는 코드를 작성한 후 Visual Studio 확장을 다시 빌드하고 다시 배포합니다. Visual Studio 확장을 다시 빌드하면 새 색상의 레지스트리 값이 나머지 테마에 병합됩니다. 그런 다음 Visual Studio를 다시 실행하고 UI를 보고 새 색상이 예상대로 나타나는지 확인합니다.

## <a name="notes"></a>메모
 이 도구는 기존 Visual Studio 테마에 대한 사용자 지정 색상을 만들거나 사용자 지정 Visual Studio 테마의 색상을 편집하는 데 사용됩니다. 완벽한 사용자 지정 Visual Studio 테마를 만들려면 Visual Studio 확장 갤러리에서 [Visual Studio 색상 테마 편집기 확장을](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) 다운로드합니다.

## <a name="sample-output"></a>샘플 출력
 **XML 색상 출력**

 도구에서 생성된 .xml 파일은 다음과 유사합니다.

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="CategoryName" GUID="{eee9d521-dac2-48d9-9a5e-5c625ba2040c}">
      <Color Name="ColorName1">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
      <Color Name="ColorName2">
        <Background Type="CT_RAW" Source="FFFFFFFF" />
        <Foreground Type="CT_RAW" Source="FF000000" />
      </Color>
      <Color Name="ColorName3">
        <Background Type="CT_RAW" Source="FFFF0000" />
      </Color>
      <Color Name="ColorName4">
        <Background Type="CT_RAW" Source="FF000088" />
        <Foreground Type="CT_RAW" Source="FFFFFFFF" />
      </Color>
    </Category>
  </Theme>
  <Theme Name="Dark" GUID="{1ded0138-47ce-435e-84ef-9ec1f439b749}">...</Theme>
  <Theme Name="Blue" GUID="{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}">...</Theme>
  <Theme Name="HighContrast" GUID="{a5c004b4-2d4b-494e-bf01-45fc492522c7}">...</Theme>
</Themes>

```

 **PKGDEF 컬러 출력**

 도구에서 생성된 .pkgdef 파일은 다음과 유사합니다.

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\CategoryName]
"Data"=hex:78,00,00,00,0b,00,00,00,01,00,00,00,21,d5,e9,ee,c2,da,d9,48,9a,5e,5c,62,5b,a2,04,0c,04,00,00,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,31,01,ff,ff,ff,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,32,01,ff,ff,ff,ff,01,00,00,00,ff,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,33,01,ff,00,00,ff,00,0a,00,00,00,43,6f,6c,6f,72,4e,61,6d,65,34,01,00,00,88,ff,01,ff,ff,ff,ff
[$RootKey$\Themes\{1ded0138-47ce-435e-84ef-9ec1f439b749}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}\CategoryName]
"Data"=hex:...
[$RootKey$\Themes\{a5c004b4-2d4b-494e-bf01-45fc492522c7}\CategoryName]
"Data"=hex:...

```

 **C# 리소스 키 래퍼**

 도구에서 생성되는 색상 리소스 키는 다음과 유사합니다.

```csharp
namespace MyNamespace
{
    public static class MyColors
    {
        #region Autogenerated resource keys
        // These resource keys are generated by Visual Studio Extension Color Editor, and should be replaced when new colors are added to this category.

        public static string ColorName1ColorKey { get { return "ColorName1ColorKey"; } }
        public static string ColorName1BrushKey { get { return "ColorName1BrushKey"; } }

        public static string ColorName2ColorKey { get { return "ColorName2ColorKey"; } }
        public static string ColorName2BrushKey { get { return "ColorName2BrushKey"; } }
        public static string ColorName2TextColorKey { get { return "ColorName2TextColorKey"; } }
        public static string ColorName2TextBrushKey { get { return "ColorName2TextBrushKey"; } }

        public static string ColorName3ColorKey { get { return "ColorName4ColorKey"; } }
        public static string ColorName3BrushKey { get { return "ColorName4BrushKey"; } }
        public static string ColorName3TextColorKey { get { return "ColorName4TextColorKey"; } }
        public static string ColorName3TextBrushKey { get { return "ColorName4TextBrushKey"; } }
        #endregion
    }
}
```

 **WPF 리소스 사전 래퍼**

 도구에서 생성된 색상 **ResourceDictionary** 키는 다음과 유사합니다.

```xaml
<ResourceDictionary xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:colors="clr-namespace:MyNamespace">

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName1BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName1ColorKey}" A="255" R="255" G="255" B="255" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2BrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2ColorKey}" A="255" R="255" G="255" B="255" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName2TextBrushKey}" Color="#FF000000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName2TextColorKey}" A="255" R="0" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName3BrushKey}" Color="#FFFF0000" />
  <Color x:Key="{x:Static colors:MyColors.ColorName3ColorKey}" A="255" R="255" G="0" B="0" />

  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4BrushKey}" Color="#FF000088" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4ColorKey}" A="255" R="0" G="0" B="136" />
  <SolidColorBrush x:Key="{x:Static colors:MyColors.ColorName4TextBrushKey}" Color="#FFFFFFFF" />
  <Color x:Key="{x:Static colors:MyColors.ColorName4TextColorKey}" A="255" R="255" G="255" B="255" />
</ResourceDictionary>
```

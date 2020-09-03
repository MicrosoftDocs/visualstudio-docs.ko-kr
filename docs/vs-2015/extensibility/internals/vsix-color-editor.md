---
title: VSIX 색 편집기 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 70879c5d-e0f0-4845-993c-2f4229869706
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea5695c41b19cbd77c56a63f22b52fca5ee6f1eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295439"
---
# <a name="vsix-color-editor"></a>VSIX 색 편집기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 확장 색 편집기 도구를 통해 Visual Studio에 대 한 사용자 지정 색을 만들고 편집할 수 있습니다. 이 도구는 코드에서 색을 사용할 수 있도록 테마 리소스 키를 생성할 수도 있습니다. 이 도구는 테마를 지 원하는 Visual Studio 확장에 대 한 색을 만드는 데 유용 합니다. 이 도구는 .pkgdef 및 .xml 파일을 열 수 있습니다. Visual studio 테마 (vstheme 파일)는 파일 확장명을 .xml로 변경 하 여 Visual Studio 확장 색 편집기에서 사용할 수 있습니다. 또한 vstheme 파일을 현재 .xml 파일로 가져올 수 있습니다.  
  
 ![VSIX 색 편집기 Hero](../../extensibility/internals/media/vsix-color-editor-hero.png "VSIX 색 편집기 Hero")  
  
 **패키지 정의 파일**  
  
 패키지 정의 파일 (.pkgdef)은 테마를 정의 하는 파일입니다. 색 자체는 .pkgdef 파일로 컴파일되는 테마 색 .xml 파일에 저장 됩니다. .Pkgdef 파일은 Visual Studio에서 검색할 수 있는 위치에 배포 되 고 런타임에 처리 되며 함께 병합 되어 테마를 정의 합니다.  
  
 **색 토큰**  
  
 색 토큰은 4 개의 요소로 구성 됩니다.  
  
- **범주 이름:** 색 집합에 대 한 논리적 그룹화입니다. 원하는 UI 요소 또는 UI 요소 그룹과 관련 된 색이 이미 있는 경우 기존 범주 이름을 사용 합니다.  
  
- **토큰 이름:** 색 토큰 및 토큰 집합에 대 한 설명이 포함 된 이름입니다. 설정에는 배경 및 전경 (텍스트) 토큰 이름과 모든 상태를 포함 하며, 이러한 이름과 해당 쌍이 적용 되는 상태를 쉽게 식별할 수 있도록 이름이 지정 되어야 합니다.  
  
- **색 값 (또는 색조):** 색이 지정 된 각 테마에 필요 합니다. 항상 배경색과 텍스트 색 값을 쌍으로 만듭니다. 색은 배경/전경에 대해 쌍을 이룹니다. 따라서 텍스트 (전경) 색은 그리는 배경색을 기준으로 항상 읽을 수 있습니다. 이러한 색은 연결 되어 있으며 UI에서 함께 사용 됩니다. 배경에 텍스트를 사용할 수 없는 경우 전경색을 정의 하지 마십시오.  
  
- **시스템 색 이름:** 고대비 디스플레이에서 사용 합니다.  
  
## <a name="how-to-use-the-tool"></a>이 도구를 사용 하는 방법  
 가능 하면 기존 Visual Studio 색을 새로 만드는 대신 다시 사용 해야 합니다. 그러나 적절 한 색이 정의 되지 않은 경우에는 확장 테마를 호환 가능 하 게 유지 하기 위해 사용자 지정 색을 만들어야 합니다.  
  
 **새 색 토큰 만들기**  
  
 Visual Studio 확장 색 편집기를 사용 하 여 사용자 지정 색을 만들려면 다음 단계를 수행 합니다.  
  
1. 새 색 토큰의 범주 및 토큰 이름을 결정 합니다.  
  
2. UI 요소가 각 테마에 사용할 색 및 고대비에 대 한 시스템 색을 선택 합니다.  
  
3. 색 편집기를 사용 하 여 새 색 토큰을 만듭니다.  
  
4. Visual Studio 확장에서 색을 사용 합니다.  
  
5. Visual Studio에서 변경 내용을 테스트 합니다.  
  
   **1 단계: 새 색 토큰의 범주 및 토큰 이름을 결정 합니다.**  
  
   VSColor의 기본 이름 지정 체계는 **[Category] [UI 유형] [상태]** 입니다. VSColor 이름에 "color" 라는 단어는 중복 되므로 사용 하지 마십시오.  
  
   범주 이름은 논리적 그룹화를 제공 하며 가능한 한 좁은 것으로 정의 되어야 합니다. 예를 들어 단일 도구 창의 이름은 범주 이름일 수 있지만 전체 사업부 또는 프로젝트 팀의 이름은 그렇지 않습니다. 항목을 범주로 그룹화 하면 이름이 같은 색 간의 혼동을 방지할 수 있습니다.  
  
   토큰 이름은 요소 유형과 색이 적용 되는 상황 또는 "상태"를 명확 하 게 나타내야 합니다. 예를 들어 활성 데이터 팁의 **[UI 종류]** 의 이름을 "**DataTip**"으로 지정 하 고 **[State]** 이름을 "**active**"로 지정 하 여 색 이름을 "**DataTipActive**"로 지정할 수 있습니다. 데이터 팁에 텍스트가 있으므로 전경 색과 배경색을 모두 정의 해야 합니다. 배경색 편집기는 배경/전경 쌍을 사용 하 여 배경에 "**DataTipActive**" 색을 자동으로 만들며 전경의 경우 "**DataTipActiveText**"을 만듭니다.  
  
   UI 부분에 상태가 하나뿐인 경우 이름의 **[state]** 부분을 생략할 수 있습니다. 예를 들어 검색 상자에 테두리가 있고 테두리 색에 영향을 주는 상태 변화가 없는 경우 테두리 색 토큰의 이름을 "**Searchboxborder**"로 간단히 호출할 수 있습니다.  
  
   일반적인 상태 이름에는 다음이 포함 됩니다.  
  
- 활성  
  
- 비활성  
  
- MouseOver  
  
- MouseDown  
  
- 선택됨  
  
- 포커스 있음  
  
  목록 항목 컨트롤의 일부에 대 한 몇 가지 토큰 이름 예:  
  
- ListItem  
  
- ListItemBorder  
  
- ListItemMouseOver  
  
- Listitemmouse과잉 테두리  
  
- ListItemSelected  
  
- ListItemSelectedBorder  
  
- ListItemDisabled  
  
- ListItemDisabledBorder  
  
  **2 단계: UI 요소에서 각 테마에 사용할 색 및 고대비에 대 한 시스템 색을 선택 합니다.**  
  
  UI에 대 한 사용자 지정 색을 선택 하는 경우 유사한 기존 UI 요소를 선택 하 고 색을 기준으로 사용 합니다. 기본 UI 요소의 색은 검토 및 테스트를 거쳤습니다. 따라서 모든 테마에서 적절 하 게 표시 되 고 올바르게 동작 합니다.  
  
  **3 단계: 색 편집기를 사용 하 여 새 색 토큰을 만듭니다.**  
  
  색 편집기를 시작 하 고 새 사용자 지정 테마 색 .xml 파일을 열거나 만듭니다. 메뉴에서 **편집 > 새 색** 을 선택 합니다. 그러면 범주와 해당 범주 내의 색 항목에 대 한 하나 이상의 이름을 지정 하는 대화 상자가 열립니다.  
  
  ![VSIX 색 편집기 새 색](../../extensibility/internals/media/vsix-color-editor-new-color.png "VSIX 색 편집기 새 색")  
  
  기존 범주를 선택 하거나 **새 범주** 를 선택 하 여 새 범주를 만듭니다. 다른 대화 상자가 열리고 새 범주 이름이 생성 됩니다.  
  
  ![VSIX 색 편집기 새 범주](../../extensibility/internals/media/vsix-color-editor-new-category.png "VSIX 색 편집기 새 범주")  
  
  새 범주는 **새 색** 범주 드롭다운 메뉴에서 사용할 수 있게 됩니다. 범주를 선택한 후 각 새 색 토큰에 대해 줄당 하나의 이름을 입력 하 고 완료 되 면 "만들기"를 선택 합니다.  
  
  ![VSIX 색 편집기 새 색 채워짐](../../extensibility/internals/media/vsix-color-editor-new-color-filled.png "VSIX 색 편집기 새 색 채워짐")  
  
  색 값은 배경/전경 쌍으로 표시 되 고, "없음"은 색이 정의 되지 않았음을 나타냅니다. 참고: 색에 텍스트 색/배경 색 쌍이 없으면 배경만 정의 해야 합니다.  
  
  ![VSIX 색 편집기 색 값](../../extensibility/internals/media/vsix-color-editor-color-values.png "VSIX 색 편집기 색 값")  
  
  색 토큰을 편집 하려면 해당 토큰의 테마 (열)에 대 한 색 항목을 선택 합니다. 16 진수 색 값을 8 자리 ARGB 형식으로 입력 하거나, 셀에 시스템 색 이름을 입력 하거나, 드롭다운 메뉴를 사용 하 여 색 슬라이더 집합 또는 시스템 색 목록을 통해 원하는 색을 선택 하 여 색 값을 추가 합니다.  
  
  ![VSIX 색 편집기 색 편집](../../extensibility/internals/media/vsix-color-editor-edit-color.png "VSIX 색 편집기 색 편집")  
  
  ![VSIX 색 편집기 배경](../../extensibility/internals/media/vsix-color-editor-background.png "VSIX 색 편집기 배경")  
  
  텍스트를 표시 하지 않아도 되는 구성 요소의 경우 배경색을 한 색 값으로 입력 합니다. 그렇지 않으면 배경색과 텍스트 색 모두에 대 한 값을 슬래시로 구분 하 여 입력 합니다.  
  
  고대비에 대 한 값을 입력 하는 경우 올바른 Windows 시스템 색 이름을 입력 합니다. 하드 코드 되는 ARGB 값을 입력 하지 마세요. 색 값 드롭다운 메뉴에서 "Background: System" 또는 "포그라운드: System"을 선택 하 여 유효한 시스템 색 이름 목록을 볼 수 있습니다. 텍스트 구성 요소가 있는 요소를 만드는 경우 올바른 배경/텍스트 시스템 색 쌍을 사용 하거나 텍스트를 읽을 수 없습니다.  
  
  색 토큰 만들기, 설정 및 편집을 마치면 원하는 .xml 또는. .pkgdef 형식으로 저장 합니다. 배경 또는 전경 집합이 아닌 색 토큰은 .xml 형식의 빈 색으로 저장 되지만 .pkgdef 형식에서 삭제 됩니다. .Pkgdef 파일에 빈 색을 저장 하려고 하면 대화 상자에서 잠재적 색 손실을 경고 합니다.  
  
  **4 단계: Visual Studio 확장에서 색을 사용 합니다.**  
  
  새 색 토큰을 정의한 후에는 프로젝트 파일의 "빌드 작업"을 "내용"으로 설정 하 고 "VSIX에 포함"을 "True"로 설정 하 여 .pkgdef를 포함 합니다.  
  
  ![VSIX 색 편집기 pkgdef](../../extensibility/internals/media/vsix-color-editor-pkgdef.png "VSIX 색 편집기 pkgdef")  
  
  Visual Studio 확장 색 편집기에서 파일 > 리소스 코드 보기를 선택 하 여 WPF 기반 UI의 사용자 지정 색에 액세스 하는 데 사용 되는 코드를 봅니다.  
  
  ![VSIX 색 편집기 리소스 코드 뷰어](../../extensibility/internals/media/vsix-color-editor-resource-code-viewer.png "VSIX 색 편집기 리소스 코드 뷰어")  
  
  프로젝트의 정적 클래스에이 코드를 포함 합니다. **ThemeResourceKey** 형식을 사용 하려면 ** \<VSVersion>.0.dllVisualStudio** 에 대 한 참조를 프로젝트에 추가 해야 합니다.  
  
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
  
 이렇게 하면 XAML 코드의 색에 액세스할 수 있으며 UI가 테마 변경 내용에 응답할 수 있습니다.  
  
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
  
 **5 단계: Visual Studio에서 변경 내용을 테스트 합니다.**  
  
 색 편집기는 확장 패키지를 다시 빌드하지 않고도 색의 라이브 변경 내용을 볼 수 있도록 Visual Studio의 실행 중인 인스턴스에 색 토큰을 일시적으로 적용할 수 있습니다. 이렇게 하려면 각 테마 열의 헤더에 있는 "이 테마를 실행 하 여 Visual Studio 창 실행" 단추를 클릭 합니다. 이 임시 테마는 VSIX 색 편집기를 닫을 때 사라집니다.  
  
 ![VSIX 색 편집기 적용](../../extensibility/internals/media/vsix-color-editor-apply.png "VSIX 색 편집기 적용")  
  
 변경 내용을 영구적으로 적용 하려면 .pkgdef 파일에 새 색을 추가 하 고 해당 색을 사용 하는 코드를 작성 한 후 Visual Studio 확장을 다시 빌드하고 다시 배포 합니다. Visual Studio 확장을 다시 빌드하면 새 색의 레지스트리 값을 나머지 테마에 병합 합니다. 그런 다음 Visual Studio를 다시 시작한 다음 UI를 확인 하 고 새 색상이 예상 대로 표시 되는지 확인 합니다.  
  
## <a name="notes"></a>참고  
 이 도구는 기존 Visual Studio 테마에 대 한 사용자 지정 색을 만들거나 사용자 지정 Visual Studio 테마의 색을 편집 하는 데 사용 됩니다. 전체 사용자 지정 Visual Studio 테마를 만들려면 visual studio 확장 갤러리에서 [Visual Studio 색 테마 편집기 확장](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2015ColorThemeEditor) 을 다운로드 합니다.  
  
## <a name="sample-output"></a>샘플 출력  
 **XML 색 출력**  
  
 도구에서 생성 된 .xml 파일은 다음과 유사 합니다.  
  
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
  
 **.PKGDEF 색 출력**  
  
 도구에서 생성 하는 .pkgdef 파일은 다음과 유사 합니다.  
  
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
  
 **C # 리소스 키 래퍼**  
  
 도구에서 생성 되는 색 리소스 키는 다음과 유사 합니다.  
  
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
  
 도구에서 생성 된 색 **ResourceDictionary** 키는 다음과 유사 합니다.  
  
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

---
title: Visual Studio에서 XAML 디자이너와 함께 디자인 타임 데이터 사용
description: XAML에서 디자인 타임 데이터를 사용하는 방법에 대해 알아봅니다.
ms.date: 11/10/2020
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 1dd0b4df440f6addd474ef08e7bf0b2958a58076
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94492897"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Visual Studio에서 XAML 디자이너와 함께 디자인 타임 데이터 사용

일부 레이아웃은 데이터 없이 시각화하기가 어렵습니다. 이 문서에서는 데스크톱 프로젝트를 작업하는 개발자가 XAML 디자이너에서 데이터 모의에 사용할 수 있는 접근 방식 중 하나를 알아보겠습니다. 이 접근 방식에서는 무시할 수 있는 기존 “d:” 네임스페이스를 사용합니다. 이 접근 방식을 사용하면 전체 모의 ViewModel을 만들지 않고도 신속하게 페이지나 컨트롤에 디자인 타임 데이터를 추가할 수 있으며 속성 변경이 릴리스 빌드에 영향을 미칠 것을 걱정할 필요 없이 속성 변경이 애플리케이션에 미칠 수 있는 영향을 테스트할 수 있습니다. 모든 d: 데이터는 XAML 디자이너에서만 사용되고, 무시할 수 있는 네임스페이스 값은 애플리케이션에 컴파일되지 않습니다.

> [!NOTE]
> Xamarin.Forms를 사용하는 경우 [Xamarin.Forms 디자인 타임 데이터](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)를 참조하세요.

## <a name="design-time-data-basics"></a>디자인 타임 데이터 기본 사항

디자인 타임 데이터는 XAML 디자이너에서 컨트롤을 더 쉽게 시각화할 수 있도록 설정하는 모의 데이터입니다. 시작하려면 XAML 문서 헤더에 다음 코드 줄이 아직 없는 경우 추가합니다.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

네임스페이스를 추가한 후에는 특성 또는 컨트롤 앞에 `d:`를 배치하여 XAML 디자이너에서만 표시하고 런타임에는 표시하지 않을 수 있습니다.

예를 들어 일반적으로 데이터가 바인딩된 TextBlock에 텍스트를 추가할 수 있습니다.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![TextBlock에 텍스트가 포함된 디자인 타임 데이터](media\xaml-design-time-textblock.png "텍스트 레이블이 있는 디자인 타임 데이터")](media\xaml-design-time-textblock.png#lightbox)

이 예제에서 `d:Text` 없이는 XAML 디자이너가 TextBlock에 대해 아무것도 표시하지 않습니다. 대신 “Name!”이 표시됩니다. 여기서 TextBlock은 런타임에 실제 데이터를 가집니다.

색, 글꼴 크기, 간격 같은 UWP 또는 WPF .NET Core 컨트롤 특성과 함께 `d:`를 사용할 수 있습니다. 컨트롤 자체에도 추가할 수 있습니다.

```xml
<d:Button Content="Design Time Button" />
```

[![단추 컨트롤이 있는 디자인 타임 데이터](media\xaml-design-time-button.png "단추 컨트롤이 있는 디자인 타임 데이터")](media\xaml-design-time-button.png#lightbox)

이 예제에서 단추는 디자인 타임에만 표시됩니다. 이 메서드를 사용하여 사용자 지정 컨트롤의 자리 표시자를 입력하거나 다른 컨트롤을 사용해 볼 수 있습니다. 모든 `d:` 특성과 컨트롤은 런타임 중에 무시됩니다.

## <a name="preview-images-at-design-time"></a>디자인 타임의 미리 보기 이미지

페이지에 바인딩되거나 동적으로 로드되는 이미지에 디자인 타임 소스를 설정할 수 있습니다. XAML 디자이너에 표시하려는 이미지를 프로젝트에 추가합니다. 그런 다음, 디자인 타임에 XAML 디자이너에서 해당 이미지를 표시할 수 있습니다.

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> 이 예제의 이미지는 솔루션에 존재해야 합니다.

## <a name="design-time-data-for-listviews"></a>Listview의 디자인 타임 데이터

ListView는 데스크톱 앱에 데이터를 표시하는 데 많이 사용되는 방법입니다. 그러나 데이터 없이는 시각화하기 어렵습니다. 이 기능을 사용하여 인라인 디자인 타임 데이터 ItemSource를 만들 수 있습니다. XAML 디자이너는 디자인 타임에 해당 배열에 있는 항목을 ListView에 표시합니다. WPF .NET Core의 예제입니다. system:String 형식을 사용하려면 XAML 헤더에 `xmlns:system="clr-namespace:System;assembly=mscorlib`를 포함해야 합니다.

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![ListView가 있는 디자인 타임 데이터](media\xaml-design-time-listview-strings.png "ListView가 있는 디자인 타임 데이터")](media\xaml-design-time-listview-strings.png#lightbox)

앞의 예제에서는 XAML 디자이너에 세 개의 TextBlock이 있는 ListView를 보여 줍니다.

데이터 개체의 배열을 만들 수도 있습니다. 예를 들어 `City` 데이터 개체의 퍼블릭 속성을 디자인 타임 데이터로 생성할 수 있습니다.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

XAML에서 클래스를 사용하려면 루트 노드의 네임스페이스를 가져와야 합니다.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![ListView가 있는 디자인 타임 데이터의 실제 모델](media\xaml-design-time-listview-models.png "ListView가 있는 디자인 타임 데이터의 실제 모델")](media\xaml-design-time-listview-models.png#lightbox)

이 경우 이점은 디자인 타임 정적 버전의 모델에 컨트롤을 바인딩할 수 있다는 점입니다.

## <a name="use-design-time-data-with-custom-types-and-properties"></a>사용자 지정 형식 및 속성으로 디자인 타임 데이터 사용

기본적으로 이 기능은 플랫폼 컨트롤 및 속성에서만 작동합니다. 이 섹션에서는 고유한 사용자 지정 컨트롤을 디자인 타임 컨트롤로 사용하도록 설정하는 데 필요한 단계를 설명합니다. Visual Studio 2019 버전 [16.8](/visualstudio/releases/2019/release-notes/) 이상을 사용 중인 고객에게 제공되는 새로운 기능입니다. 사용하도록 설정하는 데는 세 가지 요구 사항이 있습니다.

- 사용자 지정 xmlns 네임스페이스

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- 네임스페이스의 디자인 타임 버전입니다. 간단히 끝에 /design을 추가하여 수행할 수 있습니다.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- mc:Ignorable에 디자인 타임 접두사 추가

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

이러한 모든 단계를 수행한 후 `myDesignTimeControls` 접두사를 사용하여 디자인 타임 컨트롤을 만들 수 있습니다.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>사용자 지정 xmlns 네임스페이스 만들기

WPF .NET Core에서 사용자 지정 xmlns 네임스페이스를 만들려면 사용자 지정 XML 네임스페이스를 컨트롤이 있는 CLR 네임스페이스에 매핑해야 합니다. `AssemblyInfo.cs` 파일에 `XmlnsDefinition` 어셈블리 수준 특성을 추가하면 됩니다. 파일은 프로젝트의 루트 계층 구조에 있습니다.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>문제 해결

이 섹션에 나열되지 않은 문제가 발생하는 경우 [문제 신고](../ide/how-to-report-a-problem-with-visual-studio.md) 도구를 통해 알려주세요.

### <a name="requirements"></a>요구 사항

- 디자인 타임 데이터에는 Visual Studio 2019 버전 [16.7](/visualstudio/releases/2019/release-notes) 이상이 필요합니다.

- .NET Core 및 UWP에서 WPF(Windows Presentation Foundation)를 대상으로 하는 Windows 데스크톱 프로젝트를 지원합니다. “.NET Framework용 새 WPF XAML 디자이너” 미리 보기 기능을 사용하도록 설정한 경우 이 기능을 .NET Framework에도 사용할 수 있습니다.

- Visual Studio 2019 버전 16.7부터는 이 기능이 WPF 및 UWP 프레임워크의 모든 기본 제공 컨트롤에서 작동합니다. 타사 컨트롤 지원은 16.8 미리 보기 릴리스에서 사용할 수 있습니다.

### <a name="the-xaml-designer-stopped-working"></a>XAML 디자이너의 작동이 중지됨

XAML 파일을 닫았다가 다시 열어 프로젝트를 정리하고 다시 빌드해 보세요.

## <a name="see-also"></a>참고 항목

- [Xamarin.Forms Previewer를 사용한 디자인 타임 데이터](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [WPF 앱의 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 앱의 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 앱의 XAML](/xamarin/xamarin-forms/xaml/)
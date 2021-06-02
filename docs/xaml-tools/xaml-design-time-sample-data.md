---
title: Visual Studio XAML 디자이너 디자인 타임 샘플 데이터 사용
description: XAML에서 디자인 타임 샘플 데이터를 사용하는 방법을 알아봅니다.
ms.date: 05/28/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: a987435d454771bdecf078e78af089405718d261
ms.sourcegitcommit: 5366c6bca3fb217a2fbf847998387578f51ec45c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748046"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Visual Studio XAML 디자이너 디자인 타임 샘플 데이터 사용

ListView, ListBox 또는 DataGrid와 같은 일부 데이터 의존 컨트롤은 데이터 없이 시각화하기 어렵습니다. 이 문서에서는 **WPF .NET Core** 프로젝트 또는 **WPF .NET Framework** 프로젝트에서 작업하는 개발자가 새 디자이너를 사용하여 이러한 컨트롤에서 샘플 데이터를 사용하도록 설정하는 새로운 방법을 검토합니다. 

## <a name="sample-data-feature-basics"></a>샘플 데이터 기능 기본 사항

샘플 데이터는 디자인 타임 시각화 전용입니다. 즉, 실행 중인 앱이 아닌 XAML 디자이너에만 나타납니다. 따라서 ItemsSource 속성 의 디자인 타임 버전에 `d:ItemsSource` 적용됩니다. 샘플 데이터에는 디자인 타임 네임스페이스가 작동해야 합니다. 시작하려면 XAML 문서 헤더에 다음 코드 줄이 아직 없는 경우 추가합니다.

> [!NOTE]
> [XAML의 디자인 타임 속성에](/xaml/xaml-tools/xaml/xaml-designtime-data.md) 대한 자세한 내용은 XAML 디자인 타임 속성을 방문합니다.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

네임스페이스를 추가한 후 를 사용하여 `d:ItemsSource="{d:SampleData}"` ListView, Listbox 또는 DataGrid에서 샘플 데이터를 사용하도록 설정할 수 있습니다. 예를 들어:

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![DataGrid를 통해 데이터 샘플링](media\xaml-sample-data-empty-datagrid.png "DataGrid에서 사용하도록 설정된 샘플 데이터")](media\xaml-sample-data-empty-datagrid.png#lightbox)

이 예제에서 `d:ItemsSource="{d:SampleData}"` XAML 디자이너 없으면 빈 DataGrid가 표시됩니다. 대신, `d:SampleData` 이제 생성된 기본 샘플 데이터가 표시됩니다.

기본적으로 5개 항목이 표시됩니다. 그러나 **ItemCount** 속성을 사용하여 표시할 항목 수를 지정할 수 있습니다. 예를 들어: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>샘플 데이터는 datatemplates와 함께 작동합니다.

샘플 데이터는 데이터 템플릿을 사용할 때 ListBox, ListView 또는 DataGrid 컨트롤에 대해 작동합니다. 샘플 데이터 기능은 DataTemplate을 분석하고 적절한 데이터를 생성하려고 시도합니다. 샘플 데이터는 바인딩을 사용하는 DataTemplates의 요소에 대해서만 생성됩니다. 바인딩에 아직 소스가 없는 경우에도 샘플 데이터가 생성됩니다.
예를 들어:

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![DataTemplate이 있는 샘플 데이터 ListView](media\xaml-sample-data-templated-listview.png "DataTemplate을 사용하여 ListView에서 사용되는 샘플 데이터")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>제안된 작업을 사용하여 샘플 데이터 사용

디자이너에서 컨트롤에 대해 샘플 데이터를 쉽게 사용하거나 사용하지 않도록 설정하려면 제안된 작업 기능을 사용할 수 있습니다. 제안된 작업은 컨트롤을 선택할 때 오른쪽 위에 표시되는 디자이너의 전구입니다. 컨트롤을 선택하고 전구를 클릭한 다음 를 클릭하여 샘플 데이터를 사용하도록 설정할 수 `Show Sample Data` 있습니다. 예를 들어:

[![샘플 데이터 제안된 작업](media\xaml-sample-data-suggested-actions.png "제안된 작업을 사용하여 샘플 데이터 사용")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>IValueConverters를 이용한 샘플 데이터 

변환기는 샘플 데이터 기능에서 완전히 지원되지 않습니다. 그러나 다음 중 하나 또는 둘 모두를 수행하여 작업을 수행할 수 있습니다.
- `Convert`함수가 값이 이미 targetType인 시나리오를 처리할 수 있는지 확인합니다.

- 값을 `ConvertBack` 원래 형식으로 다시 변환하는 함수를 구현합니다. 

## <a name="troubleshooting"></a>문제 해결

샘플 데이터가 아무것도 표시되지 않거나 올바른 형식을 표시하지 못하는 경우 디자이너를 새로 고치거나 페이지를 닫았다 다시 열 수 있습니다.

이 섹션에 나열되지 않은 문제가 발생하거나 페이지를 새로 고쳐 해결할 수 없는 경우 문제 [보고](../ide/how-to-report-a-problem-with-visual-studio.md) 도구를 사용하여 알려주세요.

### <a name="requirements"></a>요구 사항

- 샘플 데이터에는 Visual Studio 2019 버전 [16.10](/visualstudio/releases/2019/release-notes-v16.10) 이상이 필요합니다.

- 새 디자이너를 사용할 때 .NET Core 또는 .NET Framework 대한 WPF(Windows Presentation Foundation)를 대상으로 하는 Windows 데스크톱 프로젝트를 지원합니다. 새 디자이너를 .NET Framework 사용하도록 설정하려면 도구 > 옵션 > 환경 > 미리 보기 기능으로 이동하여 .NET Framework 새 WPF XAML 디자이너 선택한 다음, Visual Studio 다시 시작합니다.

## <a name="see-also"></a>참고 항목

- [XAML 디자인 타임 속성](/xaml/xaml-tools/xaml/xaml-designtime-data)
- [WPF 앱의 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 앱의 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 앱의 XAML](/xamarin/xamarin-forms/xaml/)
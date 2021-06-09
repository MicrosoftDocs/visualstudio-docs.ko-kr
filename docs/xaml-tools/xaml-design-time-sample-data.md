---
title: Visual Studio에서 XAML 디자이너를 사용 하 여 디자인 타임 샘플 데이터 사용
description: XAML에서 디자인 타임 샘플 데이터를 사용 하는 방법에 대해 알아봅니다.
ms.date: 06/01/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: 66418d351280a0c067327716766725d22488131b
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760915"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Visual Studio에서 XAML 디자이너를 사용 하 여 디자인 타임 샘플 데이터 사용

ListView, ListBox 또는 DataGrid와 같은 일부 데이터 기반 컨트롤은 데이터 없이 시각화 하기가 어렵습니다. 이 문서에서는 새 디자이너를 사용 하 여 **wpf .Net Core** 프로젝트 또는 **.NET Framework wpf** 에서 작업 하는 개발자가 이러한 컨트롤에서 샘플 데이터를 사용 하도록 설정할 수 있도록 하는 새로운 접근 방식을 검토 합니다. 

## <a name="sample-data-feature-basics"></a>샘플 데이터 기능 기본 사항

샘플 데이터는 디자인 타임 시각화에만 해당 됩니다. 즉, 실행 중인 앱이 아니라 XAML 디자이너에만 표시 됩니다. 이와 같이 System.windows.controls.itemscontrol.itemssource 속성의 디자인 타임 버전에 적용 됩니다 `d:ItemsSource` . 샘플 데이터를 사용 하려면 디자인 타임 네임 스페이스가 필요 합니다. 시작하려면 XAML 문서 헤더에 다음 코드 줄이 아직 없는 경우 추가합니다.

> [!NOTE]
> Xaml 디자인 타임 속성에 대 한 자세한 내용은 xaml [디자인 타임 속성](../xaml-tools/xaml-designtime-data.md) 을 참조 하세요.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

네임 스페이스를 추가한 후를 사용 `d:ItemsSource="{d:SampleData}"` 하 여 ListView, Listbox 또는 DataGrid에서 샘플 데이터를 사용 하도록 설정할 수 있습니다. 예를 들면 다음과 같습니다.

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![DataGrid를 사용 하는 샘플 데이터](media\xaml-sample-data-empty-datagrid.png "DataGrid에서 사용 되는 샘플 데이터")](media\xaml-sample-data-empty-datagrid.png#lightbox)

이 예제에서는 XAML 디자이너 없이 `d:ItemsSource="{d:SampleData}"` 빈 DataGrid를 표시 합니다. 대신, `d:SampleData` 이제 생성 된 기본 샘플 데이터가 표시 됩니다.

기본적으로 5 개의 항목이 표시 됩니다. 그러나 **ItemCount** 속성을 사용 하 여 표시할 항목 수를 지정할 수 있습니다. 예를 들어: `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>Datatemplates와 함께 작동 하는 샘플 데이터

데이터 템플릿을 사용 하는 경우 샘플 데이터는 ListBox, ListView 또는 DataGrid 컨트롤에 대해 작동 합니다. 샘플 데이터 기능은 DataTemplate를 분석 하 고 해당 데이터에 대 한 적절 한 데이터를 생성 합니다. 예제 데이터는 바인딩을 사용 하는 DataTemplates의 요소에 대해서만 생성 됩니다. 바인딩에 소스가 아직 없는 경우에도 샘플 데이터가 생성 됩니다.
예를 들면 다음과 같습니다.

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

[![DataTemplate를 사용 하는 샘플 데이터 ListView](media\xaml-sample-data-templated-listview.png "DataTemplate를 사용 하 여 ListView에서 사용 되는 샘플 데이터")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>제안 된 작업으로 샘플 데이터 사용

디자이너에서 컨트롤에 대 한 샘플 데이터를 쉽게 사용 하거나 사용 하지 않도록 설정 하려면 제안 된 작업 기능을 사용할 수 있습니다. 제안 된 작업은 디자이너에서 컨트롤을 선택할 때 오른쪽 위에 표시 되는 전구입니다. 컨트롤을 선택 하 고 전구를 클릭 한 다음 켜기를 클릭 하 여 샘플 데이터를 사용 하도록 설정할 수 있습니다 `Show Sample Data` . 예를 들면 다음과 같습니다.

[![샘플 데이터 제안 된 작업](media\xaml-sample-data-suggested-actions.png "제안 된 작업으로 샘플 데이터 사용")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>IValueConverters를 사용 하는 샘플 데이터 

변환기는 샘플 데이터 기능에서 완전히 지원 되지 않습니다. 그러나 다음 중 하나 또는 모두를 수행 하 여 작업을 수행할 수 있습니다.
- `Convert`함수에서 값이 이미 targetType 인 시나리오를 처리할 수 있는지 확인 합니다.

- 값을 `ConvertBack` 원래 형식으로 다시 변환 하는 함수를 구현 합니다. 

## <a name="troubleshooting"></a>문제 해결

샘플 데이터에 아무것도 표시 되지 않거나 올바른 유형을 표시 하지 못하는 경우 디자이너를 새로 고치거 나 페이지를 닫았다가 다시 열 수 있습니다.

이 섹션에 나열 되지 않은 문제가 발생 하거나 페이지를 새로 고쳐 수정할 수 없는 경우 [문제 보고](../ide/how-to-report-a-problem-with-visual-studio.md) 도구를 사용 하 여 알려주세요.

### <a name="requirements"></a>요구 사항

- 샘플 데이터에는 Visual Studio 2019 버전 [16.10](/visualstudio/releases/2019/release-notes-v16.10) 이상이 필요 합니다.

- 는 새 디자이너를 사용할 때 .NET Core 또는 .NET Framework에 대 한 Windows Presentation Foundation (WPF)를 대상으로 하는 Windows 데스크톱 프로젝트를 지원 합니다. .NET Framework에 대 한 새 디자이너를 사용 하도록 설정 하려면 도구 > 옵션 > 환경 > 미리 보기 기능으로 이동 하 고, XAML 디자이너에 대해 새 WPF .NET Framework을 선택한 후 Visual Studio를 다시 시작 합니다.

## <a name="see-also"></a>참조

- [XAML 디자인 타임 속성](../xaml-tools/xaml-designtime-data.md)
- [WPF 앱의 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 앱의 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 앱의 XAML](/xamarin/xamarin-forms/xaml/)
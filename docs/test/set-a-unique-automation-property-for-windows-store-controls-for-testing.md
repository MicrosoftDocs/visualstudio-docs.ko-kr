---
title: 테스트를 위해 UWP 컨트롤에 대한 고유 자동화 속성 설정
ms.date: 05/31/2018
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 62409dc4aac8f640c7b58b112f7f86215ba2043b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286715"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>테스트를 위해 UWP 컨트롤에 대한 고유 자동화 속성 설정

XAML 기반 UWP 애플리케이션에 대한 코딩된 UI 테스트를 실행하려는 경우, 각 컨트롤을 고유한 자동화 속성으로 식별해야 합니다. 애플리케이션에서 XAML 컨트롤의 형식에 따라 고유한 자동화 속성을 할당할 수 있습니다.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>정적 XAML 정의

XAML 파일에 정의된 컨트롤에 대한 고유 자동화 속성을 지정하려면 **AutomationProperties.AutomationId** 또는 **AutomationProperties.Name**을 다음 예제와 같이 암시적 또는 명시적으로 설정할 수 있습니다. 이러한 값 중 하나를 설정하면 코딩된 UI 테스트 또는 작업 기록을 만들 때 컨트롤을 식별하는 데 사용할 수 있는 고유한 자동화 속성을 컨트롤에 부여하게 됩니다.

### <a name="set-the-property-implicitly"></a>속성을 암시적으로 설정

XAML에서 컨트롤에 대한 **이름** 속성을 사용하여 **AutomationProperties.AutomationId**를 **ButtonX**로 설정합니다.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

XAML에서 **컨트롤**에 대한 콘텐츠 속성을 사용하여 **AutomationProperties.Name**을 **ButtonY**로 설정합니다.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>속성을 명시적으로 설정

XAML에서 컨트롤에 대해 명시적으로 **AutomationProperties.AutomationId**를 **ButtonX**로 설정합니다.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

XAML에서 컨트롤에 대해 명시적으로 **AutomationProperties.Name**을 **ButtonY**로 설정합니다.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>고유한 이름 할당

Blend for Visual Studio에서 단추, 목록 상자, 콤보 상자 및 텍스트 상자와 같은 대화형 요소에 고유한 이름을 할당하는 옵션을 선택할 수 있습니다. 그러면 **AutomationProperties.Name**에 대해 고유한 값을 제어할 수 있습니다.

기존 컨트롤에 고유한 이름을 할당하려면 **도구** > **대화형 요소 이름 지정**을 선택합니다.

![Blend for Visual Studio에서 대화형 요소 이름 지정](../test/media/cuit_windowsstoreproperty_blend_1.png)

추가한 새 컨트롤에 고유한 이름을 자동으로 지정하려면 **도구** > **옵션**을 선택하여 **옵션** 대화 상자를 엽니다. **XAML 디자이너**를 선택한 다음, **생성 시 대화형 요소에 자동으로 이름 지정**을 선택합니다. **확인**을 선택하여 대화 상자를 닫습니다.

## <a name="use-a-data-template"></a>데이터 템플릿 사용

**ItemTemplate**을 사용하여 간단한 템플릿을 정의하고 목록 상자의 값을 변수에 바인딩할 수 있습니다.

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

또한 템플릿을 **ItemContainerStyle**과 함께 사용하여 값을 변수에 바인딩할 수도 있습니다.

```xaml
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemContainerStyle>
      <Style TargetType="ListBoxItem">
         <Setter Property="Template">
            <Setter.Value>
               <ControlTemplate TargetType="ListBoxItem">
                  <Grid>
                     <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                  </Grid>
               </ControlTemplate>
            </Setter.Value>
         </Setter>
      </Style>
   </ListBox.ItemContainerStyle>
</ListBox>
```

그런 다음, 이 예제 모두에 대해 다음 코드를 사용하여 **ItemSource**의 **ToString()** 메서드를 재정의해야 합니다. 이 코드는 **AutomationProperties.Name** 값이 설정되었고 고유한 값임을 확인합니다. 이는 바인딩을 사용하여 각 데이터가 바인딩된 목록 항목에 대해서는 고유한 자동화 속성을 설정할 수 없기 때문입니다. 이 경우에는 **Automation Properties.Name**에 대해 고유한 값을 설정하는 것으로 충분합니다.

> [!NOTE]
> 이 방법을 사용하면 바인딩을 통해 Employee 클래스의 문자열에 목록 항목의 내부 콘텐츠가 설정될 수도 있습니다. 예제에서와 같이 각 목록 항목 안에 있는 단추 컨트롤에는 직원 ID인 고유한 자동화 ID가 할당됩니다.

```csharp
Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}
```

## <a name="use-a-control-template"></a>컨트롤 템플릿 사용

컨트롤 템플릿을 사용하여 특정 형식의 각 인스턴스가 코드에서 정의될 때 고유한 자동화 속성을 획득하도록 할 수 있습니다. 컨트롤 인스턴스에서 **AutomationProperty**가 고유한 ID에 바인딩되도록 템플릿을 만듭니다. 다음 XAML은 컨트롤 템플릿을 사용하여 이 바인딩을 만드는 방법 한 가지를 보여 줍니다.

```xaml
<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>
```

이 컨트롤 템플릿을 사용하여 단추의 두 인스턴스를 정의할 때 다음 XAML과 같이 템플릿의 컨트롤에 대한 고유한 콘텐츠 문자열에 자동화 ID가 설정됩니다.

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>동적 컨트롤

사용자 코드에서 동적으로 생성되었으며 XAML 파일에서는 정적으로 또는 템플릿을 통해 생성되지 않은 컨트롤이 있으면 컨트롤의 **콘텐츠** 또는 **이름** 속성을 설정해야 합니다. 이 작업을 통해 각 동적 컨트롤은 고유한 자동화 속성을 갖게 됩니다. 예를 들어 목록 항목을 선택하면 표시되어야 하는 확인란이 있는 경우 다음과 같이 이러한 속성을 설정할 수 있습니다.

```csharp
private void CreateCheckBox(string txt, StackPanel panel)
{
   CheckBox cb = new CheckBox();
   cb.Content = txt; // Sets the AutomationProperties.Name
   cb.Height = 50;
   cb.Width = 100;
   cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
   panel.Children.Add(cb);
}
```

## <a name="see-also"></a>참고 항목

- [코딩된 UI 테스트를 사용하여 UWP 앱 테스트](../test/test-uwp-app-with-coded-ui-test.md)

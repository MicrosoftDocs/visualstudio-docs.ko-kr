---
title: 테스트를 위해 Windows 스토어 컨트롤에 대한 고유 자동화 속성 설정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d4ccf10f3ce085aa8f0275c40644f1a109616daf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672146"
---
# <a name="set-a-unique-automation-property-for-windows-store-controls-for-testing"></a>테스트를 위해 Windows 스토어 컨트롤에 대한 고유 자동화 속성 설정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML 기반 Windows 스토어 애플리케이션용 코딩된 UI 테스트를 실행하려는 경우 각 컨트롤을 식별하는 고유한 자동화 속성이 있어야 합니다.

 애플리케이션에서 XAML 컨트롤의 형식에 따라 고유한 자동화 속성을 할당할 수 있습니다. 다음과 같은 상황에서 이 고유한 자동화 속성을 할당하는 방법은 다음과 같습니다.

- [컨트롤의 정적 XAML 정의](#UniquePropertyWindowsStoreControlsStaticXAML)

- [Visual Studio 또는 Blend for Visual Studio를 사용하여 고유한 자동화 속성 할당](#UniquePropertyWindowsStoreControlsExpressionBlend)

- [DataTemplate 사용](#UniquePropertyWindowsStoreControlsDataTemplate)

- [컨트롤 템플릿 사용](#UniquePropertyWindowsStoreControlsControlTemplate)

- [동적 컨트롤](#UniquePropertyWindowsStoreControlsDynamicControls)

## <a name="use-methods-to-assign-a-unique-automation-property"></a>메서드를 사용하여 고유한 자동화 속성 할당

### <a name="static-xaml-definition"></a><a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> 정적 XAML 정의
 XAML 파일에 정의된 컨트롤에 대한 고유 자동화 속성을 지정하려면 AutomationProperties.AutomationId 또는 AutomationProperties.Name을 다음 예제와 같이 암시적 또는 명시적으로 설정할 수 있습니다. 이러한 값 중 하나를 설정하면 코딩된 UI 테스트 또는 작업 기록을 만들 때 컨트롤을 식별하는 데 사용할 수 있는 고유한 자동화 속성을 컨트롤에 부여하게 됩니다.

 **속성을 암시적으로 설정**

 XAML에서 컨트롤에 대한 이름 속성을 사용하여 AutomationProperties.AutomationId를 **ButtonX**로 설정합니다.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />

```

 XAML에서 컨트롤에 대한 콘텐츠 속성을 사용하여 AutomationProperties.Name을 **ButtonY**로 설정합니다.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />

```

 **속성을 명시적으로 설정**

 XAML에서 컨트롤에 대해 명시적으로 AutomationProperties.AutomationId를 **ButtonX**로 설정합니다.

```xaml
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />

```

 XAML에서 컨트롤에 대해 명시적으로 AutomationProperties.Name을 **ButtonY**로 설정합니다.

```
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="assign-unique-automation-properties-using-visual-studio-or-blend-for-visual-studio"></a><a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Visual Studio 또는 Blend for Visual Studio를 사용 하 여 고유한 자동화 속성 할당
 Visual Studio 또는 Blend for Visual Studio를 사용하여 단추, 목록 상자, 콤보 상자, 텍스트 상자와 같은 대화형 요소에 고유한 이름을 할당할 수 있습니다. 이렇게 하면 AutomationProperties.Name에 대한 고유한 값을 컨트롤에 부여하게 됩니다.

 **Visual Studio:****도구** 메뉴에서 **옵션**을 가리킨 다음 **텍스트 편집기**, **XAML** 및 **기타**를 차례대로 선택합니다.

 **생성 시 대화형 요소에 자동으로 이름 지정**을 선택한 다음 **확인**을 선택합니다.

 ![XAML 기타 옵션](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")

 **Blend for Visual Studio:** 다음 방법 중 하나를 사용하여 Blend for Visual Studio에서 이 작업을 수행할 수 있습니다.

> [!NOTE]
> XAML을 사용하여 정적으로 만든 컨트롤에 대해서는 이 방법만 사용할 수 있습니다.

 **기존 컨트롤에 고유한 이름을 지정하려면**

 **도구** 메뉴에서 다음과 같이 **대화형 요소 이름 지정**을 선택합니다.

 ![도구 메뉴에서 대화형 요소 이름 지정 선택](../test/media/cuit-windowsstoreproperty-blend-1.png "CUIT_WindowsStoreProperty_Blend_1")

 **만드는 컨트롤에 자동으로 고유한 이름을 지정하려면**

 **도구** 메뉴에서 **옵션**을 선택한 다음 **프로젝트**를 선택합니다. 다음과 같이 **생성 시 대화형 요소에 자동으로 이름 지정**을 선택한 다음 **확인**을 선택합니다.

 ![대화형 요소 이름을 지정하도록 프로젝트 설정](../test/media/cuit-windowsstoreproeprty-blend-2.png "CUIT_WindowsStoreProeprty_Blend_2")

### <a name="use-a-data-template"></a><a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> 데이터 템플릿 사용
 다음 XAML을 사용하면 ItemTemplate을 사용하여 간단한 템플릿을 정의하고 목록 상자의 값을 변수에 바인딩할 수 있습니다.

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

 또한 다음 XAML을 사용하면 템플릿을 ItemContainerStyle과 함께 사용하여 값을 변수에 바인딩할 수도 있습니다.

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

 그런 다음에는 이 예제 모두에 대해 다음 코드를 사용하여 ItemSource의 ToString() 메서드를 재정의해야 합니다. 이 코드는 AutomationProperties.Name 값이 설정되었고 고유한 값임을 확인합니다. 이는 바인딩을 사용하여 각 데이터가 바인딩된 목록 항목에 대해서는 고유한 자동화 속성을 설정할 수 없기 때문입니다. 이 경우에는 Automation Properties.Name에 대해 고유한 값을 설정하는 것으로 충분합니다.

> [!NOTE]
> 이 방법을 사용하면 바인딩을 통해 Employee 클래스의 문자열에 목록 항목의 내부 콘텐츠가 설정될 수도 있습니다. 예제에서와 같이 각 목록 항목 안에 있는 단추 컨트롤에는 직원 ID인 고유한 자동화 ID가 할당됩니다.

```

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

### <a name="use-a-control-template"></a><a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> 컨트롤 템플릿 사용
 컨트롤 템플릿을 사용하여 특정 형식의 각 인스턴스가 코드에서 정의될 때 고유한 자동화 속성을 획득하도록 할 수 있습니다. 컨트롤 인스턴스에서 AutomationProperty가 고유한 ID에 바인딩되도록 템플릿을 만들어야 합니다. 다음 XAML은 컨트롤 템플릿을 사용하여 이 바인딩을 만드는 방법 한 가지를 보여 줍니다.

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

<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a><a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> 동적 컨트롤
 사용자 코드에서 동적으로 생성되었으며 XAML 파일에서는 정적으로 또는 템플릿을 통해 생성되지 않은 컨트롤이 있으면 컨트롤의 콘텐츠 또는 이름 속성을 설정해야 합니다. 이렇게 하면 각 동적 컨트롤은 고유한 자동화 속성을 갖게 됩니다. 예를 들어 목록 항목을 선택하면 표시되어야 하는 확인란이 있는 경우 다음과 같이 이러한 속성을 설정할 수 있습니다.

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

---
title: XAML 디자이너에서 데이터에 바인딩
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1abe14c443432d0da0ab0c53b33f9321034228be
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "82921102"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>연습: XAML 디자이너에서 데이터에 바인딩

XAML 디자이너에서 아트보드와 속성 창을 사용하여 데이터 바인딩 속성을 설정할 수 있습니다. 이 연습의 예제에서는 데이터를 컨트롤에 바인딩하는 방법을 보여줍니다. 특히 이 연습에서는 `ItemCount`라는 [DependencyProperty](xref:Windows.UI.Xaml.DependencyProperty)가 포함된 간단한 쇼핑 카트 클래스를 만든 다음, [TextBlock](xref:Windows.UI.Xaml.Controls.TextBlock) 컨트롤의 **Text** 속성에 `ItemCount` 속성을 바인딩하는 방법을 보여 줍니다.

## <a name="to-create-a-class-to-use-as-a-data-source"></a>데이터 소스로 사용할 클래스를 만들려면

1. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택하고, **Windows 바탕 화면** 노드를 펼친 다음, **WPF 애플리케이션** 템플릿을 선택합니다.

1. **BindingTest** 프로젝트 이름을 지정한 다음 **확인** 단추를 선택합니다.

1. **MainWindow.xaml.cs**(또는 **MainWindow.xaml.vb**) 파일을 열고 다음 코드를 추가합니다. C#에서는 `BindingTest` 네임스페이스에 코드를 추가합니다(파일의 마지막 닫는 괄호 앞에 추가). Visual Basic에서는 새 클래스를 추가합니다.

   ```csharp
   public class ShoppingCart : DependencyObject
   {
       public int ItemCount
       {
           get { return (int)GetValue(ItemCountProperty); }
           set { SetValue(ItemCountProperty, value); }
       }

       public static readonly DependencyProperty ItemCountProperty =
            DependencyProperty.Register("ItemCount", typeof(int),
            typeof(ShoppingCart), new PropertyMetadata(0));
   }
   ```

   ```vb
   Public Class ShoppingCart
       Inherits DependencyObject

       Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
       Public Property ItemCount As Integer
           Get
               ItemCount = CType(GetValue(ItemCountProperty), Integer)
           End Get
           Set(value As Integer)
               SetValue(ItemCountProperty, value)
           End Set
       End Property
   End Class
   ```

   이 코드는 [PropertyMetadata](xref:Windows.UI.Xaml.PropertyMetadata) 개체를 사용하여 기본 항목 수로 값 0을 설정합니다.

1. **파일** 메뉴에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>ItemCount 속성을 TextBlock 컨트롤에 바인딩하려면

1. 솔루션 탐색기에서 **mainwindow.xaml** 의 바로 가기 메뉴를 열고 **뷰 디자이너**를 선택 합니다.

1. 도구 상자에서 [그리드](xref:Windows.UI.Xaml.Controls.Grid) 컨트롤을 선택하여 양식에 추가합니다.

1. `Grid`를 선택하고, [속성] 창에서 **DataContext** 속성 옆에 있는 **새로 만들기** 단추를 선택합니다.

1. **개체 선택** 대화 상자에서, **모든 어셈블리 표시** 확인란을 선택 취소하고, **BindingTest** 네임스페이스 아래에서 **ShoppingCart**를 선택한 다음, **확인** 단추를 선택합니다.

     다음 그림에서는 **ShoppingCart**가 선택된 **개체 선택** 대화 상자를 보여 줍니다.

     ![개체 선택 대화 상자](../designers/media/blendselectobject.png)

1. **도구 상자**에서, `TextBlock` 컨트롤을 선택하여 양식에 추가합니다.

1. `TextBlock` 컨트롤을 선택하고, [속성] 창에서 **Text** 속성의 오른쪽에 속성 마커를 선택한 다음, **데이터 바인딩 만들기**를 선택합니다. 속성 표식은 작은 상자 모양입니다.

1. [데이터 바인딩 만들기] 대화 상자의 **경로** 상자에서 **ItemCount : (int32)** 속성을 선택한 다음 **확인** 단추를 선택합니다.

     다음 그림에서는 **ItemCount** 속성이 선택된 **데이터 바인딩 만들기** 대화 상자를 보여 줍니다.

     ![데이터 바인딩 만들기 대화 상자](../designers/media/xaml_create_data_binding.png)

1. **F5** 키를 눌러 앱을 실행 합니다.

     `TextBlock` 컨트롤은 0의 기본값을 텍스트로 표시해야 합니다.

## <a name="see-also"></a>참고 항목

- [XAML 디자이너를 사용하여 UI 만들기](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [값 변환기 추가 대화 상자](https://msdn.microsoft.com/library/c5f3d110-a541-4b55-8bca-928f77778af8)

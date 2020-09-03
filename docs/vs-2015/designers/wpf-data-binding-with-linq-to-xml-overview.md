---
title: LINQ to XML로 WPF 데이터 바인딩 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3bf80845-891b-41de-a71b-4080b5bd3ea6
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c0cbd93f2d32c06ba52b2c47c1af8f326948609a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75843921"
---
# <a name="wpf-data-binding-with-linq-to-xml-overview"></a>LINQ to XML로 WPF 데이터 바인딩 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 <xref:System.Xml.Linq> 네임스페이스의 동적 데이터 바인딩 기능에 대해 소개합니다. 이러한 기능을 WPF(Windows Presentation Foundation)의 UI(사용자 인터페이스) 요소에 대한 데이터 소스로 사용할 수 있습니다.

## <a name="xaml-and-linq-to-xml"></a>XAML 및 LINQ to XML
 XAML(eXtensible Application Markup Language)은 .NET Framework 3.0 기술을 지원하기 위해 Microsoft에서 만드는 XML 언어입니다. XAML은 사용자 인터페이스 요소와 이벤트 및 데이터 바인딩과 같은 관련 기능을 나타내기 위해 WPF에서 사용됩니다. Windows Workflow Foundation에서 XAML은 프로그램 제어(*워크플로*)와 같은 프로그램 구조를 나타내는 데 사용됩니다. XAML을 통해 프로그램의 더욱 개별화된 동작을 정의하는 기술의 선언적 측면을 관련 절차형 코드에서 분리할 수 있습니다.

 XAML과 LINQ to XML은 다음 두 가지 주요 방식으로 상호 작용할 수 있습니다.

- XAML 파일이 제대로 구성된 XML이기 때문에 LINQ to XML과 같은 XML 기술을 통해 XAML 파일을 쿼리하고 조작할 수 있습니다.

- LINQ to XML 쿼리가 데이터 소스를 나타내기 때문에 이러한 쿼리를 WPF UI 요소의 데이터 바인딩에 대한 데이터 소스로 사용할 수 있습니다.

  이 문서에서는 두 번째 시나리오에 대해 설명합니다.

## <a name="data-binding-in-the-windows-presentation-foundation"></a>Windows Presentation Foundation의 데이터 바인딩
 WPF 데이터 바인딩을 통해 UI 요소에서 속성 중 하나를 데이터 소스와 연결할 수 있습니다. 이에 대한 간단한 예는 사용자 정의 개체에서 public 속성의 값을 제공하는 텍스트가 포함된 <xref:System.Windows.Controls.Label>입니다. WPF 데이터 바인딩은 다음 구성 요소를 사용합니다.

|구성 요소|설명|
|---------------|-----------------|
|바인딩 대상|데이터 소스와 연결할 UI 요소입니다. WPF의 시각적 요소는 <xref:System.Windows.UIElement> 클래스에서 파생됩니다.|
|대상 속성|데이터 바인딩 원본의 값을 반영하는 바인딩 대상의 *종속성 속성*입니다. 종속성 속성은 <xref:System.Windows.DependencyObject>가 파생되는 <xref:System.Windows.UIElement> 클래스에서 직접 지원합니다.|
|바인딩 소스|표시하기 위해 UI 요소에 제공되는 하나 이상의 값에 대한 원본 개체입니다. WPF는 CLR 개체, ADO.NET 데이터 개체, XML 데이터(XPath 또는 LINQ to XML 쿼리의 데이터) 또는 다른 <xref:System.Windows.DependencyObject>를 바인딩 원본으로 자동으로 지원합니다.|
|소스 경로|바인딩될 값이나 값의 집합으로 확인되는 바인딩 원본의 속성입니다.|

 종속성 속성은 UI 요소의 동적으로 계산된 속성을 나타내는 WPF에 특정한 개념입니다. 예를 들어, 종속성 속성에는 기본값이나 부모 요소에서 제공하는 값이 있는 경우가 많습니다. 이러한 특수 속성은 표준 속성의 경우처럼 필드가 아니라 <xref:System.Windows.DependencyProperty> 클래스의 인스턴스로 지원됩니다. 자세한 내용은 [종속성 속성 개요](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)를 참조하세요.

### <a name="dynamic-data-binding-in-wpf"></a>WPF의 동적 데이터 바인딩
 기본적으로 데이터 바인딩은 대상 UI 요소가 초기화될 때만 발생합니다. 이를 *일회성* 바인딩이라고 합니다. 일회성 바인딩은 대부분의 목적에 충분하지만 일반적으로 데이터 바인딩 솔루션에서는 변경 내용이 다음 중 하나를 사용하여 런타임에 동적으로 전파되어야 합니다.

- *단방향* 바인딩에서는 한 쪽의 변경 내용이 자동으로 전파됩니다. 원본의 변경 내용이 대상에 반영되는 경우가 가장 일반적이지만 때때로 그 반대의 경우가 유용할 수 있습니다.

- *양방향* 바인딩에서는 원본의 변경 내용이 대상에 자동으로 전파되고 대상의 변경 내용이 원본에 자동으로 전파됩니다.

  단방향 또는 양방향 바인딩이 발생하려면 소스에서 <xref:System.ComponentModel.INotifyPropertyChanged> 인터페이스를 구현하거나 지원되는 각 속성의 *PropertyNameChanged* 패턴을 사용하는 등의 방법으로 변경 알림 메커니즘을 구현해야 합니다.

  WPF의 데이터 바인딩에 대한 자세한 내용은 [데이터 바인딩(WPF)](https://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e)을 참조하세요.

## <a name="dynamic-properties-in-linq-to-xml-classes"></a>LINQ to XML 클래스의 동적 속성
 대부분의 LINQ to XML 클래스는 적절한 WPF 동적 데이터 소스로 적합하지 않습니다. 가장 유용한 정보 중 일부는 속성이 아니라 메서드를 통해서만 사용할 수 있으며 이러한 클래스의 속성은 변경 알림을 구현하지 않습니다. WPF 데이터 바인딩을 지원하기 위해 LINQ to XML에서는 *동적 속성*의 집합을 노출합니다.

 이러한 동적 속성은 <xref:System.Xml.Linq.XAttribute> 및 <xref:System.Xml.Linq.XElement> 클래스에 있는 기존 메서드 및 속성의 기능과 중복되는 특수 런타임 속성이며, WPF의 동적 데이터 소스로 작동하기 위한 목적으로만 이러한 클래스에 추가됩니다. 이 요구를 충족시키기 위해 이러한 모든 동적 속성은 변경 알림을 구현합니다. 이러한 동적 속성에 대한 자세한 참조 정보는 다음 섹션 [LINQ to XML 동적 속성](../designers/linq-to-xml-dynamic-properties.md)에서 제공됩니다.

> [!NOTE]
> <xref:System.Xml.Linq> 네임스페이스의 다양한 클래스에 있는 표준 public 속성 중 상당수를 일회성 데이터 바인딩에 사용할 수 있습니다. 그러나 이 체계에서 원본이나 대상은 동적으로 업데이트되지 않습니다.

### <a name="accessing-dynamic-properties"></a>동적 속성 액세스
 <xref:System.Xml.Linq.XAttribute> 및 <xref:System.Xml.Linq.XElement> 클래스의 동적 속성에는 표준 속성의 경우처럼 액세스할 수 없습니다. 예를 들어, C#과 같은 CLR 규격 언어에서 동적 속성에는 다음과 같은 특징이 있습니다.

- 컴파일 타임에 직접 액세스할 수 없습니다. 동적 속성은 컴파일러와 Visual Studio IntelliSense에 표시되지 않습니다.

- .NET 리플렉션을 사용하여 런타임에 검색하거나 액세스할 수 없습니다. 런타임에도 동적 속성은 기본 CLR 의미에서 속성이 아닙니다.

  C#에서는 <xref:System.ComponentModel> 네임스페이스에서 제공하는 기능을 통해 런타임에만 동적 속성에 액세스할 수 있습니다.

  그러나 XML 원본에서는 이와 대조적으로 다음과 같은 형태의 간단한 표기법을 통해 동적 속성에 액세스할 수 있습니다.

```
<object>.<dynamic-property>
```

 이러한 두 클래스의 동적 속성은 직접 사용할 수 있는 값이나 결과 값 또는 값 컬렉션을 얻기 위해 인덱스와 함께 제공되어야 하는 인덱서로 확인됩니다. 후자의 구문은 다음과 같습니다.

```
<object>.<dynamic-property>[<index-value>]
```

 자세한 내용은 [LINQ to XML 동적 속성](../designers/linq-to-xml-dynamic-properties.md)을 참조하세요.

 WPF 동적 바인딩을 구현하기 위해 동적 속성은 <xref:System.Windows.Data> 네임스페이스(무엇보다도 <xref:System.Windows.Data.Binding> 클래스)에서 제공하는 기능과 함께 사용됩니다

## <a name="see-also"></a>관련 항목
 Wpf 데이터 [바인딩 (wpf)](https://msdn.microsoft.com/library/90f79b97-17e7-40d1-abf0-3ba600ad1d7e) [에서 워크플로 마크업을 사용 하 여](https://msdn2.microsoft.com/library/ms735921(vs.90).aspx) LINQ to XML [LINQ to XML 동적 속성](../designers/linq-to-xml-dynamic-properties.md) [XAML](https://msdn.microsoft.com/library/5d858575-a83b-42df-ad3f-047ed2d6e3c8) 을 사용 하 [여 wpf 데이터 바인딩](../designers/wpf-data-binding-with-linq-to-xml.md)

---
title: 텍스트 템플릿 제어 블록
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, template code
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef39e82ea1abe95b3bea799545ed7fbf5b766fd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591790"
---
# <a name="text-template-control-blocks"></a>텍스트 템플릿 제어 블록
제어 블록을 사용하면 다양한 출력을 생성하기 위해 텍스트 템플릿에 코드를 작성할 수 있습니다. 다음과 같은 세 가지 종류의 제어 블록이 있으며 각각 여는 대괄호로 구분됩니다.

- `<# Standard control blocks #>`은 문을 포함할 수 있습니다.

- `<#= Expression control blocks #>`은 식을 포함할 수 있습니다.

- `<#+ Class feature control blocks #>`은 메서드, 필드 및 속성을 포함할 수 있습니다.

## <a name="standard-control-block"></a>표준 제어 블록
 표준 제어 블록은 문을 포함합니다. 예를 들어, 다음 표준 블록에서는 XML 문서에서 모든 특성의 이름을 가져옵니다.

```
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>

<#
    List<string> allAttributes = new List<string>();
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes.Count > 0)
    {
       foreach (XmlAttribute attr in attributes)
       {
           allAtributes.Add(attr.Name);
       }
     }
#>
```

 복합 문 안에 `if` 또는 `for`와 같은 일반 텍스트를 포함할 수 있습니다. 예를 들어 이 조각은 각 루프 반복에서 출력 줄을 생성합니다.

```
<#
       foreach (XmlAttribute attr in attributes)
       {
#>
Found another one!
<#
           allAtributes.Add(attr.Name);
       }
#>
```

> [!WARNING]
> 항상 {...} 사용 포함 된 일반 텍스트가 포함 된 중첩 문을 구분 합니다. 다음 예제는 제대로 작동하지 않을 수 있습니다.
>
> `<# if (ShouldPrint) #> Some text. -- WRONG`
>
> 대신 다음과 같이 {}(대괄호)를 포함해야 합니다.

```

<#
 if (ShouldPrint)
 {   //  "{" REQUIRED
#>
Some text.
<#
 }
#>
```

## <a name="expression-control-block"></a>식 제어 블록
 식 제어 블록은 출력 파일에 기록될 문자열을 제공하는 코드에 사용됩니다. 예를 들어, 위의 예제에서 코드 블록을 다음과 같이 수정하여 특성의 이름을 출력 파일로 인쇄할 수 있습니다.

```
<#
    XmlDocument xDoc = new XmlDocument();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {
#><#= attr.Name #><#
       }
    }
#>
```

## <a name="class-feature-control-block"></a>클래스 기능 제어 블록
 클래스 기능 제어 블록을 사용하여 메서드, 속성, 필드 또는 중첩 클래스를 텍스트 템플릿에 추가할 수 있습니다. 클래스 기능 블록은 텍스트 템플릿의 다른 부분에 있는 코드에 도우미 함수를 제공하는 데 가장 일반적으로 사용됩니다. 예를 들어, 다음 클래스 기능 블록에서는 특성 이름의 첫 문자를 대문자로 바꿉니다. 이름에 공백이 포함된 경우에는 모든 단어의 첫 문자를 대문자로 바꿉니다.

```
<#@ import namespace="System.Globalization" #>
```

```
<#+
    private string FixAttributeName(string name)
    {
        return CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name);
    }
#>
```

> [!NOTE]
> 같은 템플릿 파일에서 클래스 기능 제어 블록 뒤에 표준 제어 블록을 두지 않아야 합니다. 그러나 `<#@include#>` 지시문을 사용한 결과에는 이러한 제한 사항이 적용되지 않습니다. 각각의 포함된 파일에서는 표준 블록 뒤에 클래스 기능 블록이 올 수 있습니다.

 텍스트 및 식 블록을 클래스 기능 제어 블록 안에 포함하여 출력을 생성하는 함수를 만들 수 있습니다. 예:

```
<#+
    private void OutputFixedAttributeName(string name)
    {
#>
 Attribute:  <#= CultureInfo.CurrentCulture.TextInfo.ToTitleCase(name) #>
<#+  // <<< Notice that this is also a class feature block.
    }
#>
```

 이 함수는 표준 블록이나 다른 클래스 기능 블록에서 호출할 수 있습니다.

```
<# foreach (Attribute attribute in item.Attributes)
{
  OutputFixedAttributeName(attribute.Name);
}
#>
```

## <a name="how-to-use-control-blocks"></a>제어 블록을 사용하는 방법
 단일 템플릿의 모든 표준 및 식 제어 블록에 있는 모든 코드(포함된 템플릿의 모든 코드 포함)가 결합되어 생성된 코드의 `TransformText()` 메서드를 형성합니다. 지시문을 사용 하 여 다른 텍스트 템플릿을 포함 하는 방법에 대 한 자세한 내용은 `include` [T4 텍스트 템플릿 지시문](../modeling/t4-text-template-directives.md)을 참조 하세요.

 제어 블록을 사용할 때는 다음 사항을 고려해야 합니다.

- **언어도.** 텍스트 템플릿에서 C# 또는 Visual Basic 코드를 사용할 수 있습니다. 기본 언어는 C#이지만 `template` 지시문의 `language` 매개 변수를 사용하여 Visual Basic을 지정할 수 있습니다. 지시문에 대 한 자세한 내용은 `template` [T4 텍스트 템플릿 지시문](../modeling/t4-text-template-directives.md)을 참조 하세요.

     제어 블록에서 사용하는 언어는 텍스트 템플릿에서 생성하는 텍스트의 언어 또는 형식과 관련이 없습니다. Visual Basic 코드를 사용하여 C#을 생성할 수 있으며 그 반대로도 생성할 수 있습니다.

     `include` 지시문을 사용하여 포함하는 모든 텍스트 템플릿을 비롯한 지정된 텍스트 템플릿에서 한 언어만 사용할 수 있습니다.

- **지역 변수입니다.** 텍스트 템플릿의 표준 및 식 제어 블록에 있는 모든 코드가 단일 메서드로 생성되므로 로컬 변수 이름과 충돌하지 않는지 확인해야 합니다. 다른 텍스트 템플릿을 포함하는 경우 변수 이름이 모든 포함된 템플릿에서 고유하도록 해야 합니다. 이렇게 하는 한 가지 방법은 텍스트 템플릿을 식별하는 각 로컬 변수 이름(해당 텍스트 템플릿에 선언됨)에 문자열을 추가하는 것입니다.

     특히 여러 텍스트 템플릿을 포함하는 경우 로컬 변수를 선언할 때 적절한 값으로 초기화하는 것도 좋은 방법입니다.

- **제어 블록의 중첩.** 제어 블록은 다른 제어 블록 안에 중첩될 수 없습니다. 다른 제어 블록을 열기 전에 주어진 제어 블록을 항상 종료해야 합니다. 예를 들어, 다음은 표준 제어 블록의 일부로 식 블록의 텍스트를 인쇄하는 방법을 보여 줍니다.

    ```
    <#
    int x = 10;
    while (x-- > 0)
    {
    #>
    <#= x #>
    <# } #>
    ```

- **리팩터링이.** 텍스트 템플릿을 간단하고 이해하기 쉽게 유지하려면 다시 사용할 수 있는 코드를 클래스 기능 블록에서 도우미 함수로 구분하거나 Microsoft.VisualStudio.TextTemplating.TextTransformation 클래스에서 상속하는 텍스트 템플릿 클래스를 만들어 반복되는 코드를 방지하는 것이 좋습니다.

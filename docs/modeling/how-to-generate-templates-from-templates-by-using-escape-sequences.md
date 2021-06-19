---
title: 텍스트 템플릿에서 텍스트 템플릿 생성
description: 이스케이프 시퀀스를 사용 하 여 다른 텍스트 템플릿에서 텍스트 템플릿을 생성 하는 방법에 대 한 정보를 제공 합니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9347e32a72e7f590f8f513c4b47a4b7aae699f27
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387179"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>방법: 이스케이프 시퀀스를 사용하여 템플릿에서 템플릿 생성
다른 텍스트 템플릿을 생성 된 텍스트 출력으로 만드는 텍스트 템플릿을 만들 수 있습니다. 이렇게 하려면 이스케이프 시퀀스를 사용 하 여 텍스트 템플릿 태그를 나타내야 합니다. 이스케이프 시퀀스를 사용 하지 않는 경우 생성 된 텍스트 템플릿은 미리 정의 된 의미를 갖게 됩니다. 텍스트 템플릿에서 이스케이프 시퀀스를 사용 하는 방법에 대 한 자세한 내용은 [텍스트 템플릿에서 이스케이프 시퀀스 사용](../modeling/using-escape-sequences-in-text-templates.md)을 참조 하세요.

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>텍스트 템플릿 내에서 텍스트 템플릿을 생성 하려면

- 백슬래시 ()를 \\ 이스케이프 문자로 사용 하 여 개별 텍스트 템플릿 파일의 지시문, 문, 식 및 클래스 기능에 대 한 텍스트 템플릿 내에서 필요한 태그를 생성 합니다.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>예제
 다음 예에서는 이스케이프 문자를 사용 하 여 텍스트 템플릿에서 텍스트 템플릿을 생성 합니다. `output`지시문은 대상 파일 형식을 텍스트 템플릿 파일 형식 (.tt)으로 설정 합니다.

```csharp
\<#@ output extension=".tt" \#>
\<#@ assembly name="System.Xml.dll" \#>
\<#@ import namespace="System.Xml" \#>
\<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {\#>
           \<#= attr.Name \#>
       \<#}
     }
\#>
```

 생성 된 텍스트 출력은 텍스트 템플릿입니다.

```
<#@ output extension=".tt" #>
<#@ assembly name="System.Xml.dll" #>
<#@ import namespace="System.Xml" #>
<#
XmlDocument xDoc = new XmlDocument();
//System.Diagnostics.Debugger.Break();
    xDoc.Load(@"E:\CSharp\Overview.xml");
    XmlAttributeCollection attributes = xDoc.Attributes;
    if (attributes != null)
    {
       foreach (XmlAttribute attr in attributes)
       {#>
           <#= attr.Name #>
       <#}
     }
#>
```

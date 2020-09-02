---
title: 텍스트 템플릿에서 Visual Studio 2015 또는 기타 호스트 액세스 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a68886da-7416-4785-8145-3796bb382cba
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e8cedc66d6b52f80239364a3e51b73e93a69aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655329"
---
# <a name="accessing-visual-studio-or-other-hosts-from-a-text-template"></a>텍스트 템플릿에서 Visual Studio 또는 다른 호스트 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 템플릿에서는와 같이 템플릿을 실행 하는 호스트에서 노출 하는 메서드 및 속성을 사용할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 이는 전처리 텍스트 템플릿이 아닌 일반 텍스트 템플릿에 적용 됩니다.

## <a name="obtaining-access-to-the-host"></a>호스트에 대 한 액세스 권한 얻기

`hostspecific="true"`지시문에를 설정 `template` 합니다. 이  `this.Host` 를 통해 [ITextTemplatingEngineHost](/previous-versions/visualstudio/visual-studio-2012/bb126505(v=vs.110))형식의를 사용할 수 있습니다. 예를 들어이 형식에는 파일 이름을 확인 하 고 오류를 기록 하는 데 사용할 수 있는 멤버가 있습니다.

### <a name="resolving-file-names"></a>파일 이름 확인
 텍스트 템플릿에 상대적인 파일의 전체 경로를 찾으려면이를 사용 합니다. ResolvePath ().

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of myFile is:
<#= myFile #>

```

### <a name="displaying-error-messages"></a>오류 메시지 표시
 이 예에서는 템플릿을 변환할 때 메시지를 기록 합니다. 호스트가 인 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 오류 창에 추가 됩니다.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.CodeDom.Compiler" #>
<#
  string message = "test message";
  this.Host.LogErrors(new CompilerErrorCollection()
    { new CompilerError(
       this.Host.TemplateFile, // Identify the source of the error.
       0, 0, "0",   // Line, column, error ID.
       message) }); // Message displayed in error window.
#>

```

## <a name="using-the-visual-studio-api"></a>Visual Studio API 사용
 에서 텍스트 템플릿을 실행 하는 경우를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 사용 `this.Host` 하 여에서 제공 하는 서비스 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 로드 된 패키지 또는 확장에 액세스할 수 있습니다.

 Set hostspecific = "true"를 지정 하 고 `this.Host` 를로 캐스팅 <xref:System.IServiceProvider> 합니다.

 이 예제에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] API를 <xref:EnvDTE.DTE> 서비스로 가져옵니다.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#@ import namespace="EnvDTE" #>
<#
 IServiceProvider serviceProvider = (IServiceProvider)this.Host;
 DTE dte = serviceProvider.GetService(typeof(DTE)) as DTE;
#>
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>

```

## <a name="using-hostspecific-with-template-inheritance"></a>템플릿 상속과 함께 hostSpecific 사용
 `hostspecific="trueFromBase"`특성을 사용 하 고를 `inherits` 지정 하는 템플릿에서 상속 하는 경우에도를 지정 `hostspecific="true"` 합니다. 이렇게 하면 속성이 두 번 선언 된 결과에 대 한 컴파일러 경고가 방지 `Host` 됩니다.

---
title: 멀티 타기팅 프로젝트
description: 이 문서에서는 Mac용 Visual Studio에서 멀티 타기팅 프로젝트를 설정하는 방법에 대해 간략하게 설명합니다.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439045"
---
# <a name="projects-with-multiple-target-frameworks"></a>대상 프레임워크가 여러 개인 프로젝트
Mac용 Visual Studio에서 Xamarin 또는 .NET Core 프로젝트를 여러 버전의 .NET Framework 및 여러 시스템 플랫폼에서 실행되도록 구성할 수 있습니다. 예를 들어 .NET Framework 4.6 및 .NET Core 3.1 모두에서 실행되도록 프로젝트 대상을 지정할 수 있습니다. 

대상 프레임워크에 대한 자세한 내용은 [대상 프레임워크](/dotnet/standard/frameworks)를 참조하세요.

> [!NOTE] 
> 이 토픽은 Mac용 Visual Studio에 적용됩니다. Windows용 Visual Studio는 [Framework 대상 지정 개요](/visualstudio/ide/visual-studio-multi-targeting-overview)를 참조하세요.

## <a name="targeting-multiple-frameworks"></a>여러 프레임워크 대상 지정

대상 프레임워크는 프로젝트 파일에서 지정되며 프로젝트를 마우스 오른쪽 단추로 클릭하고 **도구 > 파일 편집** 명령을 선택하여 편집할 수 있습니다. 단일 대상 프레임워크를 지정하는 경우 TargetFramework 요소를 사용합니다. 다음 콘솔 앱 프로젝트 파일에서는 .NET Core 3.0을 대상 프레임워크로 지정하는 방법을 보여 줍니다.

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

다중 대상 프레임워크를 지정하는 경우 복수형 TargetFrameworks 요소를 사용합니다.

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

[여러 프레임워크를 대상으로 지정](/dotnet/standard/frameworks#how-to-specify-target-frameworks)하는 방법에 대해 자세히 알아봅니다.

## <a name="working-with-code-in-a-multi-target-project"></a>다중 대상 프로젝트에서 코드 작업
대상 프레임워크가 여러 개인 프로젝트에서 C# 파일을 편집하는 경우 사용할 대상 프레임워크를 지정하여 편집기 환경을 안내할 수 있습니다(예: 해당 프레임워크에서 지원하지 않는 API를 사용하는 경우 경고를 표시). 편집기 창의 왼쪽 위에 있는 **대상 프레임워크** 선택기를 사용하여 대상 프레임워크를 변경할 수 있습니다.

![편집기 창 위쪽에 있는 대상 프레임워크 선택기를 사용하여 대상 프레임워크 변경](media/project-multitargeting-framework-selector.png)

애플리케이션이 대상으로 하는 플랫폼에 따라 다른 API를 호출해야 하는 경우도 있습니다. 이렇게 하려면 조건부 코드를 작성하여 특정 플랫폼에 대한 코드를 컴파일할 수 있습니다.

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

코드를 작성할 때 애플리케이션에서 지원하는 대상 프레임워크 중 하나라도 특정 API가 누락될 경우 IntelliSense 자동 완성 제안에 경고가 표시되므로 이를 알 수 있습니다.

![IntelliSense에 표시된 경고 메시지 - API가 지정된 대상 프레임워크에 대해 작동하지 않음. 예제 텍스트: namespace System.Buffers, SharedUtils (netstandard2.0) - Not Available. 탐색 모음을 사용하여 컨텍스트를 전환할 수 있습니다.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>참고 항목

- [Framework 대상 지정 개요(Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [SDK 스타일 프로젝트의 대상 프레임워크](/dotnet/standard/frameworks#how-to-specify-target-frameworks)

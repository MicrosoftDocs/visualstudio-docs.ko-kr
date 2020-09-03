---
title: 멀티 타기팅 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
- multi-targeting [Visual Studio]
- multitargeting [Visual Studio]
ms.assetid: b1702c33-0672-4ebc-b779-2b324d6ea880
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e8b53c5bd4d6045d7582c24be865ae216f1114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851082"
---
# <a name="visual-studio-multi-targeting-overview"></a>Visual Studio 다중 대상 지정 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 이 버전에서는 애플리케이션에 필요한 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전을 지정할 수 있습니다. 따라서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 이 버전을 사용해서 이전 버전에서 시작한 프로젝트 개발을 계속하려는 경우 프레임워크 대상을 변경할 필요가 없습니다. 여러 가지 버전의 프레임워크를 대상으로 지정하는 프로젝트가 포함된 솔루션을 만들 수도 있습니다. 프레임워크 대상 지정을 통해 애플리케이션에서 지정된 버전의 프레임워크에서 제공되는 기능만 사용하도록 할 수 있습니다.

> [!TIP]
> 다른 플랫폼에 대한 애플리케이션을 대상으로 지정할 수도 있습니다. 자세한 내용은 [다중 대상](../msbuild/msbuild-multitargeting-overview.md) 을 참조 하세요.

## <a name="framework-targeting-features"></a>프레임워크 대상 지정 기능
 프레임워크 대상 지정에는 다음 기능이 포함됩니다.

- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 이전 버전을 대상으로 하는 프로젝트를 열면 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서는 프로젝트를 자동으로 업그레이드하거나 대상을 있는 그대로 유지할 수 있습니다.

- 프로젝트를 만들 경우 대상으로 지정할 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 버전을 지정할 수 있습니다.

- 기존 프로젝트에서 대상으로 지정하는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 버전을 변경할 수 있습니다.

- 같은 솔루션에 포함된 여러 프로젝트에서 각각 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 다른 버전을 대상으로 지정할 수 있습니다.

- 프로젝트에서 대상으로 지정하는 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 버전을 변경하면 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서는 필요에 따라 참조 및 구성 파일을 변경합니다.

  [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]의 이전 버전을 대상으로 지정하는 프로젝트 관련 작업을 할 경우 Visual Studio에서는 다음과 같이 개발 환경을 동적으로 변경합니다.

- **새 프로젝트** 대화 상자, **새 항목 추가** 대화 상자, **새 참조 추가** 대화 상자 및 **서비스 참조 추가** 대화 상자에서 항목을 필터링하여 대상 버전에서 사용할 수 없는 선택 항목을 생략합니다.

- **도구 상자**에서 사용자 지정 컨트롤을 필터링하여 대상 버전에서 사용할 수 없는 컨트롤을 제거하고 여러 컨트롤을 사용할 수 있을 경우에는 가장 최신 컨트롤만 표시합니다.

- IntelliSense를 필터링하여 대상 버전에서 사용할 수 없는 언어 기능을 생략합니다.

- **속성** 창에서 속성을 필터링하여 대상 버전에서 사용할 수 없는 속성을 생략합니다.

- 메뉴 옵션을 필터링하여 대상 버전에서 사용할 수 없는 옵션을 생략합니다.

- 빌드에는 컴파일러 버전 및 대상 버전에 적절한 컴파일러 옵션을 사용합니다.

> [!NOTE]
> 프레임워크 대상 지정을 수행해도 애플리케이션이 제대로 실행되지 않을 수 있습니다. 애플리케이션을 테스트하여 대상 버전에 대해 실행되는지 확인해야 합니다. .NET Framework 2.0 이전의 프레임워크 버전은 대상으로 지정할 수 없습니다.

## <a name="selecting-a-target-framework-version"></a>대상 프레임워크 버전 선택
 프로젝트를 만들 때 **새 프로젝트** 대화 상자에서 대상 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전을 선택합니다. 사용 가능한 프로젝트 템플릿 목록은 선택에 따라 필터링됩니다. 기존 프로젝트의 경우 [프로젝트 속성] 대화 상자에서 대상 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전을 변경할 수 있습니다. 자세한 내용은 [방법: 한 버전의 .NET Framework을 대상으로 하는 방법](../ide/how-to-target-a-version-of-the-dotnet-framework.md)을 참조 하세요.

> [!NOTE]
> Visual Studio의 Express 버전에서는 **새 프로젝트** 대화 상자에서 대상 프레임워크를 설정할 수 없습니다.

## <a name="resolving-system-and-user-assembly-references"></a>시스템 및 사용자 어셈블리 참조 확인
 .NET Framework 버전을 대상으로 지정하려면 먼저 적절한 어셈블리 참조를 설치해야 합니다. .NET Framework 버전 2.0, 3.0 및 3.5에 대한 어셈블리 참조는 [Microsoft Download Center, Microsoft Visual Studio](https://www.microsoft.com/download/details.aspx?id=25150)(Microsoft 다운로드 센터, Microsoft Visual Studio) 웹 사이트에서 다운로드할 수 있는 .NET Framework 3.5 SP1에 포함됩니다. .NET Framework 3.5 Client Profile, .NET Framework 4, .NET Framework 4 Client Profile 및 Silverlight에 대한 어셈블리 참조는 [Visual Studio Downloads](https://msdn.microsoft.com/vstudio/bb984878.aspx)(Visual Studio 다운로드) 웹 사이트에서도 다운로드할 수 있습니다.

> [!NOTE]
> .NET Framework Client Profile은 라이브러리 및 기능의 제한된 집합을 제공하는 .NET Framework의 하위 집합입니다. Client Profile에 대한 자세한 내용은 [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)을 참조하세요.

 **참조 추가** 대화 상자에서는 실수로 프로젝트에 추가될 수 없도록 대상 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전에 관련이 없는 시스템 어셈블리가 사용되지 않습니다. 시스템 어셈블리는 버전에 포함 된 .dll 파일입니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . 대상 버전 보다 이후 버전의 프레임 워크 버전에 속하는 참조는 확인 되지 않으며 이러한 참조에 종속 된 컨트롤은 추가할 수 없습니다. 해당 참조를 사용하도록 설정하려면 프로젝트의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 대상을 참조가 포함된 대상으로 다시 설정합니다.  자세한 내용은 [프로젝트 디자이너 소개](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)를 참조하세요.

 어셈블리 참조에 대한 자세한 내용은 [디자인 타임에 어셈블리 확인](../msbuild/resolving-assemblies-at-design-time.md)을 참조하세요.

## <a name="enabling-linq"></a>LINQ 사용
 .NET Framework 3.5 이상을 대상으로 지정하면 System.Core에 대한 참조 및 System.Linq에 대한 프로젝트 수준 가져오기(Visual Basic에서만)가 자동으로 추가됩니다. LINQ 기능을 사용하려면 Option Infer도 켜야 합니다(Visual Basic에서만). 대상을 이전 .NET Framework 버전으로 변경하면 참조 및 가져오기가 자동으로 제거됩니다. 자세한 내용은 [방법: LINQ 프로젝트 만들기](https://msdn.microsoft.com/library/a929e653-09a3-44be-881f-68ca33f192b2)를 참조하세요.

## <a name="see-also"></a>관련 항목
[다중 대상](../msbuild/msbuild-multitargeting-overview.md) 
 [ASP.NET 웹 프로젝트](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) 
 의 .NET Framework 다중 대상 지정 [플랫폼 호환성 및 시스템 요구 사항](/visualstudio/productinfo/vs2015-compatibility-vs)

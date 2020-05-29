---
title: XAML 개요
ms.date: 05/20/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 97f3bc7777023903d5fc38ad1bda7cde45b683b6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183485"
---
# <a name="overview-of-xaml"></a>XAML 개요

XAML(Extensible Application Markup Language)은 XML을 기반으로 하는 선언적 언어입니다. XAML은 다음과 같은 유형의 애플리케이션에서 사용자 인터페이스를 빌드하는 데 광범위하게 사용됩니다.

- [Windows Presentation Foundation (WPF) 앱](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP (유니버설 Windows 플랫폼) 앱](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 앱](/xamarin/xamarin-forms/xaml/)

다음 XAML 코드는 간단한 단추 컨트롤을 정의합니다.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML은 [Windows WF(WorkFlow Foundation) 앱](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml)에서 워크플로를 정의하는 데에도 사용됩니다.

## <a name="xaml-designer"></a>XAML 디자이너

Visual Studio 및 Blend for Visual Studio는 WPF, UWP 및 Xamarin.Forms 앱의 UI(사용자 인터페이스)를 빌드하는 데 유용한 XAML 디자이너를 제공합니다. 도구 상자 또는 자산 창에서 컨트롤을 끌어 속성 창에서 속성을 설정할 수 있습니다. 이렇게 하면 Visual Studio 및 Blend for Visual Studio 해당 XAML 코드를 만듭니다. XAML 코드를 직접 편집하려는 경우에도 이 작업을 수행할 수 있습니다.

이 설명서 집합의 문서에서는 Visual Studio 및 Blend for Visual Studio의 XAML 디자이너에 대해 설명합니다.

## <a name="whats-new"></a>새로운 기능

최신 정보는 Visual studio에서 [xaml 개발자 도구의 새로운 기능 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/) 블로그 게시물, [visual studio 2019 버전 16.7 PREVIEW 1의 xaml 도구 향상 버전 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/) 블로그 게시물 및 YouTube의 [Visual STUDIO 비디오에 있는 새로운 xaml 기능](https://youtu.be/yI9OyA4ZM2E) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [WPF 앱의 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 앱의 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 앱의 XAML](/xamarin/xamarin-forms/xaml/)

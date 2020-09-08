---
title: XAML 개요
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e14e23f9820301374bd435484ba784edf50294bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331944"
---
# <a name="overview-of-xaml"></a>XAML 개요

XAML(Extensible Application Markup Language)은 XML을 기반으로 하는 선언적 언어입니다. XAML은 다음과 같은 유형의 애플리케이션에서 사용자 인터페이스를 빌드하는 데 광범위하게 사용됩니다.

- [WPF(Windows Presentation Foundation) 앱](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP(유니버설 Windows 플랫폼) 앱](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 앱](/xamarin/xamarin-forms/xaml/)

다음 XAML 코드는 간단한 단추 컨트롤을 정의합니다.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML은 [Windows WF(WorkFlow Foundation) 앱](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml)에서 워크플로를 정의하는 데에도 사용됩니다.

## <a name="xaml-code-editor"></a>XAML 코드 편집기

Visual Studio IDE의 [XAML 코드 편집기](xaml-code-editor.md)에는 Windows 플랫폼용과 Xamarin.Forms용 WPF 및 UWP 앱을 만드는 데 필요한 모든 도구를 포함합니다. 또한 Visual Studio의 IDE(통합 개발 환경)에는 다른 플랫폼용 애플리케이션을 개발하는 데 사용할 수 있는 많은 기능이 포함되어 있지만 XAML에만 고유한 기능도 있습니다.

## <a name="xaml-designer"></a>XAML 디자이너

Visual Studio 및 Blend for Visual Studio는 WPF, UWP 및 Xamarin.Forms 앱의 UI(사용자 인터페이스)를 빌드하는 데 유용한 [XAML 디자이너](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)를 제공합니다. 도구 상자 또는 자산 창에서 컨트롤을 끌어 속성 창에서 속성을 설정할 수 있습니다. 이를 수행하면 Visual Studio 및 Blend for Visual Studio에서 해당 XAML 코드를 만듭니다. XAML 코드를 직접 편집하려는 경우에도 이 작업을 수행할 수 있습니다.

## <a name="whats-new"></a>새로운 기능

최신 정보는 다음 리소스를 참조하세요.

- **[Visual Studio 2019 버전 16.7 미리 보기 1의 XAML 도구 개선](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)** 블로그 게시물
- **[Visual Studio 2019의 XAML 개발자 도구의 새로운 기능](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)** 블로그 게시물
- YouTube의 **[Visual Studio의 새로운 XAML 기능](https://youtu.be/yI9OyA4ZM2E)** 동영상

## <a name="see-also"></a>추가 정보

- [WPF 앱의 XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP 앱의 XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms 앱의 XAML](/xamarin/xamarin-forms/xaml/)

---
title: Visual Studio 및에서 XAML 디자인 Blend for Visual Studio
titleSuffix: ''
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: eb18a2face5d9f1831bec35379a423f272c3e6ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82921366"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Visual Studio 및 Blend for Visual Studio에서 XAML 디자인

Visual Studio 및 Blend for Visual Studio는 다양한 앱 유형에 XAML을 사용하여 유용한 사용자 인터페이스 및 풍부한 미디어 환경을 빌드할 수 있게 해주는 시각적 도구를 제공합니다. 두 IDE(통합 개발 환경)에서 시각적 XAML 편집기(디자이너)를 비롯한 일반적인 기능을 공유합니다. WPF 및 UWP 플랫폼을 지원하는 Blend for Visual Studio에서는 시각적 상태를 디자인하고 애니메이션을 만드는 추가 도구를 제공합니다.

Visual Studio와 Blend for Visual Studio 간에 전환할 수 있으며, 두 IDE에서 같은 프로젝트를 동시에 열어 놓을 수도 있습니다. 한 IDE에서 XAML 파일에 저장된 변경 사항을 다른 IDE로 전환할 때 자동 다시 로드를 통해 적용할 수 있습니다. **Tools**  >  **Options**  >  **Environment**  >  두 IDE 중 하나에서 도구 옵션 환경**문서로** 이동 하 여 다시 로드 동작을 제어할 수 있습니다.

## <a name="installation"></a>설치

- WPF 앱을 만들려면 Visual Studio에서 **.NET 데스크톱 개발** 워크로드를 설치합니다. Blend for Visual Studio도 함께 설치됩니다.

     ![Visual Studio 설치 관리자에서 .NET 데스크톱 개발 워크 로드의 스크린샷](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- UWP 앱을 만들려면 Visual Studio에서 **유니버설 Windows 플랫폼 개발** 워크로드를 설치합니다. Blend for Visual Studio도 함께 설치됩니다.

     ![Visual Studio 설치 관리자에서 유니버설 Windows 플랫폼 개발 워크 로드의 스크린샷](../xaml-tools/media/uwp-workload.png)

- Xamarin.Forms 앱을 만들려면 Visual Studio에서 **.NET을 사용한 모바일 개발** 워크로드를 설치합니다. Blend for Visual Studio는 설치되지 *않습니다*. Blend에서는 Xamarin.Forms 앱을 지원하지 않습니다.

     ![Visual Studio 설치 관리자에서 .NET 작업을 사용한 모바일 개발 스크린샷](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>공유 기능

기본적인 개발 작업의 경우 대부분 Visual Studio 및 Blend for Visual Studio에서 약간의 차이점은 있지만 동일한 창과 기능 집합을 공유합니다. 중요 사항은 다음과 같습니다.

- **IntelliSense:** 두 Ide는 모두 문 완성 같은 IntelliSense 기능을 지원 합니다.

- **디버깅:** 앱이 실행 되는 동안 코드에서 중단점을 설정 하 여 실행 중인 응용 프로그램을 디버깅 하 고, [핫 다시 로드](../xaml-tools/xaml-hot-reload.md) 를 사용 하 여 XAML 코드를 변경 하는 등 [Visual Studio](inspect-xaml-properties-while-debugging.md) 및 [Blend for Visual Studio](../xaml-tools/debug-xaml-in-blend.md)에서 디버그할 수 있습니다. Visual Studio와 일관된 디버깅 환경을 유지하기 위해 Blend for Visual Studio에는 Visual Studio의 디버깅 창과 도구 모음이 대부분 포함되어 있습니다.

- **파일 다시 로드:** Visual Studio 또는 Blend for Visual Studio에서 XAML 파일을 편집할 수 있습니다. 편집 후 저장된 파일은 IDE를 전환할 때 자동으로 다시 로드됩니다. **Tools**  >  **Options**  >  **Environment**  >  두 IDE 중 하나에서 도구 옵션 환경**문서로** 이동 하 여 다시 로드 동작을 제어할 수 있습니다.

- **동기화 된 레이아웃 및 설정:** 동일한 개인 설정 계정을 사용 하 여 로그인 하면 Visual Studio 또는 Blend for Visual Studio에 대 한 디자인 사용자 지정 도구 창 레이아웃 및 설정 기본 설정이 장치 및 버전 간에 동기화 됩니다. [여러 컴퓨터 간에 설정 동기화](../ide/synchronized-settings-in-visual-studio.md)를 참조하세요.

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Blend for Visual Studio의 고급 기능

생산성을 향상시키려면 다음과 같은 작업에 Blend for Visual Studio를 사용하는 것이 좋습니다. 이러한 영역에 대해 Blend for Visual Studio는 Visual Studio 디자이너나 코드를 단독으로 사용할 때보다 더 많은 기능을 제공합니다.

| Task | Visual Studio | Visual Studio용 Blend | 추가 정보 |
| - | - | - | - |
| **시각적 상태 디자인** | 시각적 상태를 디자인하는 데 도움이 되는 도구는 없습니다. 프로그래밍 방식으로 도구를 만들어야 합니다. | 디자인 도구를 사용하여 해당 상태에 따라 컨트롤의 모양을 변경합니다. | [시각적 상태](modify-the-style-of-objects-in-blend.md#visual-states) |
| **애니메이션 만들기** |애니메이션을 만들 수 있는 디자인 도구가 없습니다. 프로그래밍 방식으로 애니메이션을 만들어야 합니다. 따라서 WPF의 애니메이션, 타이밍 시스템 및 광범위한 코딩 전문 기술을 이해하고 있어야 합니다.|애니메이션을 시각적으로 만들고 Blend for Visual Studio에서 미리 볼 수 있습니다. 코드로 애니메이션을 빌드하는 것보다 더 빠르고 정확합니다. 사용자 상호 작용을 처리하는 트리거를 추가하고 이벤트 처리기 및 기타 기능을 추가하는 코드로 전환할 수 있습니다.|[개체에 애니메이션 적용](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**보다 쉽게 조작할 수 있도록 도형 및 텍스트를 패스로 변환**|지원 안 됨|도형을 패스(더 우수한 편집 컨트롤 제공)로 변환하여 도형(예: 사각형 및 타원)에 대해 미세하거나 큰 변경을 수행할 수 있습니다. 패스 모양을 변경하거나 패스를 결합하고 여러 도형에서 복합형 패스를 만들 수 있습니다.<br /><br />또한 텍스트 블록을 패스로 변환하여 벡터 이미지로 조작할 수 있습니다.|[도형 및 패스 그리기](../xaml-tools/draw-shapes-and-paths.md)|
|**컨트롤, 템플릿 및 스타일 편집**|코딩 및 WPF 스타일, 템플릿에 대한 지식이 필요합니다.|모든 이미지를 컨트롤로 변환합니다.<br /><br />템플릿 편집 도구를 사용하여 몇 번의 마우스 클릭만으로 컨트롤, 스타일 및 템플릿을 변경할 수 있습니다.<br /><br />예를 들어 Blend for Visual Studio 스타일 리소스를 사용하여 단추, 목록 상자, 스크롤 막대, 메뉴 등과 같은 공용 WPF 컨트롤을 구현하고 Blend for Visual Studio에서 해당 색, 스타일 또는 기본 템플릿을 직접 변경할 수 있습니다. 그런 다음 원하는 경우 마무리 작업을 위해 코드로 전환할 수 있습니다.|[개체 스타일 수정](modify-the-style-of-objects-in-blend.md)|
|**데이터에 UI 연결**|SQL Server 데이터베이스, WCF 또는 웹 서비스, 개체, SharePoint 목록 등의 리소스에서 데이터 소스를 만든 다음 UI 컨트롤에 데이터 소스를 바인딩할 수 있습니다.<br /><br />대화형 디자인 환경의 경우 디자인 타임 데이터는 직접 만들어야 합니다.|.NET Framework 앱의 경우 프로토타입 및 테스트를 위해 쉽게 샘플 데이터를 만듭니다. 준비가 끝나면 라이브 데이터로 전환합니다.<br /><br />Blend for Visual Studio의 데이터 생성 기능은 매우 우수한 기능으로(즉시 이름, 숫자, URL 및 사진을 쉽게 추가할 수 있음) 시간을 대폭 절약하도록 도와줍니다.<br /><br />라이브 데이터의 경우 UI 컨트롤을 XML 파일이나 모든 CLR 데이터 소스에 바인딩할 수 있습니다.|[데이터 표시](display-data-in-blend.md)|

고급 XAML 디자인에 대한 자세한 내용은 [Blend for Visual Studio를 사용하여 UI 만들기](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)를 참조하세요.

## <a name="see-also"></a>참조

- [XAML 개요](xaml-overview.md)
- [Blend for Visual Studio 개요](creating-a-ui-by-using-blend-for-visual-studio.md)

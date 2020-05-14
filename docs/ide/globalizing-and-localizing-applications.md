---
title: 지역화 도구
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c6934c816574796d59f978c3d2f37f590cf578
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565125"
---
# <a name="develop-globalized-and-localized-apps"></a>세계화 및 지역화된 앱 개발

Visual Studio는 [.NET](/dotnet/standard/globalization-localization/)에 기본 제공된 서비스를 이용하여 전 세계의 사용자를 대상으로 쉽게 개발할 수 있습니다.

예를 들어, Windows Forms 앱용 프로젝트 시스템은 대체(fallback) UI 문화권 및 추가 UI 문화권에 대한 리소스 파일을 생성할 수 있습니다. Visual Studio에서 프로젝트를 빌드할 때 리소스 파일은 Visual Studio XML 형식(.resx)에서 중간 이진 형식(.resources)으로 컴파일된 다음, 위성 어셈블리에 포함됩니다. 자세한 내용은 [Visual Studio의 리소스 파일](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) 및 [데스크톱 앱용 위성 어셈블리 만들기](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps)를 참조하세요.

## <a name="bidirectional-languages"></a>양방향 언어

Visual Studio를 사용하여 아랍어 및 히브리어와 같이 오른쪽에서 왼쪽으로 기록되는 언어로 텍스트를 제대로 표시하는 애플리케이션을 만들 수 있습니다. 일부 기능의 경우 속성만 설정하면 됩니다. 기타 경우에는 기능을 코드로 구현해야 합니다.

> [!NOTE]
> 양방향 언어를 입력 및 표시하려면 적절한 언어로 구성된 Windows 버전을 사용해야 합니다. 적절한 언어 팩이 설치된 Windows 영어 버전 또는 적절히 지역화된 Windows 버전 중 하나일 수 있습니다.

### <a name="apps-that-support-bidirectional-languages"></a>양방향 언어를 지원하는 앱

- Windows 앱

   양방향 텍스트, 오른쪽에서 왼쪽 읽기 순서 및 미러링(창 레이아웃, 메뉴, 대화 상자 등 반전)에 대한 지원이 포함된 완전 양방향 애플리케이션을 만들 수 있습니다. 미러링을 제외하고 이러한 기능은 기본적으로 또는 속성 설정으로 사용할 수 있습니다. 미러링은 메시지 상자와 같은 일부 기능에만 기본적으로 지원됩니다. 다른 경우에는 미러링을 코드로 구현해야 합니다. 자세한 내용은 [Windows Forms 애플리케이션에 대한 양방향 지원](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)을 참조하세요.

- 웹 앱

   웹 서비스는 양방향 언어가 포함된 애플리케이션에 적합해지도록 UTF-8 및 유니코드 텍스트의 송수신을 지원합니다. 웹 클라이언트 애플리케이션은 브라우저를 기반으로 사용자 인터페이스를 제공하므로 웹 애플리케이션의 양방향 지원 정도는 사용자의 브라우저가 이 양방향 기능을 얼마나 잘 지원하는지에 따라 달라집니다. Visual Studio에서는 아랍어 및 히브리어 텍스트, 오른쪽에서 왼쪽 읽기 순서, 파일 인코딩 및 로컬 문화권 설정에 대한 지원을 사용하여 애플리케이션을 만들 수 있습니다. 자세한 내용은 [ASP.NET 웹 애플리케이션을 위한 양방향 지원](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)을 참조하세요.

> [!NOTE]
> 콘솔 앱에는 양방향 언어에 대한 텍스트 지원이 포함되지 않습니다. 이는 Windows가 콘솔 애플리케이션과 작동하는 방식 때문입니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 양방향 언어에 대한 지원](use-bidirectional-languages.md)
- [.NET 앱 세계화 및 지역화](/dotnet/standard/globalization-localization/)
- [.NET 앱의 리소스](/dotnet/framework/resources/)

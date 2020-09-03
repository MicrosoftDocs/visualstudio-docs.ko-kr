---
title: '방법: 사용자 지정 시작 페이지 업그레이드 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: a7854de705a961463b1e8435e7340548cfc23bf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293376"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>방법: Visual Studio 사용자 지정 시작 페이지 업그레이드
아래 나열된 단계에 따라 Visual Studio 2010 또는 Visual Studio 2012 사용자 지정 시작 페이지를 Visual Studio 2015로 업그레이드할 수 있습니다.

> [!WARNING]
> 이 절차에서 업그레이드된 사용자 지정 시작 페이지는 Visual Studio 갤러리의 [사용자 지정 시작 페이지](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.CustomStartPageProjectTemplate) 템플릿을 사용하여 만든 페이지입니다. 시작 페이지에 업그레이드해야 하는 다른 기능이 있을 수도 있습니다.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>사용자 지정 시작 페이지를 Visual Studio 2015로 업그레이드하려면

1. Visual Studio 2015 및 Visual Studio 2015 SDK가 설치되어 있는지 확인합니다. [Microsoft Visual Studio 2013 SDK](https://my.visualstudio.com/Downloads?pid=1436)에서 VSSDK를 다운로드할 수 있습니다.

2. 사용자 지정 템플릿 프로젝트를 엽니다. 프로젝트를 업그레이드해야 함을 알리는 메시지가 나타납니다. **확인** 을 클릭하고 업그레이드가 완료될 때까지 기다립니다.

3. 시작 페이지 프로젝트와 컨트롤 프로젝트 둘 다의 프로젝트 속성에서 대상 프레임워크가 .NET Framework 4.5 이상인지 확인합니다.

4. 시작 페이지 프로젝트에 대한 프로젝트 속성의 디버그 범주에서 Visual Studio 2015 버전의 devenv.exe 경로를 설정합니다.

5. 두 프로젝트의 프로젝트 참조에서 Microsoft.VisualStudio.Shell.11.0에 대한 참조를 제거하고 Microsoft.VisualStudio.Shell.14.0에 대한 참조를 추가합니다.

6. XML 편집기를 사용하여 StartPage.xaml을 열고 다음과 같이 변경합니다.

    1. 네임스페이스를 업데이트합니다. 다음 줄을

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         다음과 같이 변경합니다.

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. MyControl.xaml을 열고 네임스페이스 참조 `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` 을 `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` 으로 변경합니다.
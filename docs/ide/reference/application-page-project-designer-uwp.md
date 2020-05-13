---
title: UWP 앱의 애플리케이션 속성 페이지
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3c8f72d4e1d1caeacd5dfefef5310dc2cef83b92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77173082"
---
# <a name="application-property-page-uwp-projects"></a>애플리케이션 속성 페이지(UWP 프로젝트)

**애플리케이션** 속성 페이지를 사용하여 UWP(유니버설 Windows 플랫폼) 프로젝트의 어셈블리 및 패키지 정보와 대상 Windows 10 버전을 지정합니다.

![애플리케이션 속성 페이지](media/application-page-uwp.png)

**애플리케이션** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택합니다. 그런 다음, 메뉴 모음에서 **프로젝트** > **속성**을 선택합니다. 속성 페이지가 **애플리케이션** 탭에서 열립니다.

## <a name="general-section"></a>일반 섹션

**어셈블리 이름**&mdash; 어셈블리 매니페스트를 보유할 출력 파일의 이름을 지정합니다.

프로그래밍 방식으로 이 속성에 액세스하려면 <xref:VSLangProj.ProjectProperties.AssemblyName%2A>를 참조하세요.

**기본 네임스페이스**&mdash; 프로젝트에 추가된 파일에 대한 기본 네임스페이스를 지정합니다. 네임스페이스에 대한 자세한 내용은 [네임스페이스(C# 프로그래밍 가이드)](/dotnet/csharp/programming-guide/namespaces/), [네임스페이스(Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces) 또는 [네임스페이스(C++)](/cpp/cpp/namespaces-cpp)를 참조하세요.

프로그래밍 방식으로 이 속성에 액세스하려면 <xref:VSLangProj.ProjectProperties.RootNamespace%2A>를 참조하세요.

**어셈블리 정보**&mdash; 이 단추를 선택하면 [어셈블리 정보 대화 상자](../../ide/reference/assembly-information-dialog-box.md)가 표시됩니다.

**패키지 매니페스트**&mdash; 이 단추를 선택하면 매니페스트 디자이너가 열립니다. 또한 _솔루션 탐색기_에서 **Package.appxmanifest** 파일을 선택하여 매니페스트 디자이너에 액세스할 수 있습니다. 자세한 내용은 [매니페스트 디자이너를 사용하여 패키지 구성](/windows/msix/package/packaging-uwp-apps#configure-your-project)을 참조하세요.

## <a name="targeting-section"></a>대상 지정 섹션

이 섹션의 드롭다운 목록을 사용하여 앱에 대한 대상 버전과 최소 Windows 10 버전을 설정할 수 있습니다. 최신 버전의 Windows 10을 대상으로 지정하는 것이 좋고 엔터프라이즈 앱을 개발하는 경우 이전 최소 버전을 지원하는 것이 좋습니다. 선택할 Windows 10 버전에 대한 자세한 내용은 [UWP 버전 선택](/windows/uwp/updates-and-versions/choose-a-uwp-version)을 참조하세요.

Visual Studio의 플랫폼 대상 지정에 대한 자세한 내용은 [플랫폼 대상 지정](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [첫 번째 UWP 앱 만들기](/windows/uwp/get-started/your-first-app)
- [UWP 버전 선택](/windows/uwp/updates-and-versions/choose-a-uwp-version)

---
title: C# 프로젝트 속성의 애플리케이션 페이지
ms.date: 10/30/2018
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesApplicationWPF
- cs.ProjectPropertiesApplication
helpviewer_keywords:
- Project Designer, Application page
- Application page in Project Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ef9a38fc13d0d9c9f6b912f4cb2b83971d105c29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595828"
---
# <a name="application-page-project-designer-c"></a>프로젝트 디자이너, 애플리케이션 페이지(C#)

**프로젝트 디자이너**의 **애플리케이션** 페이지를 사용하여 프로젝트의 애플리케이션 설정과 속성을 지정할 수 있습니다.

**애플리케이션** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드(**솔루션** 노드 아님)를 선택합니다. 그런 다음, 메뉴 모음에서 **프로젝트** > **속성**을 선택합니다. **프로젝트 디자이너**가 나타나면 **애플리케이션** 탭을 클릭합니다.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="general-application-settings"></a>일반 애플리케이션 설정

다음 옵션을 사용하여 애플리케이션에 대한 일반 설정을 구성할 수 있습니다.

**어셈블리 이름**

어셈블리 매니페스트를 보유할 출력 파일의 이름을 지정합니다. 이 속성을 변경하면 **출력 이름** 속성도 변경됩니다.

[/out(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/out-compiler-option)을 사용하여 명령줄에서 이 변경을 수행할 수도 있습니다.

프로그래밍 방식으로 이 속성에 액세스하려면 <xref:VSLangProj.ProjectProperties.AssemblyName%2A>를 참조하세요.

**기본 네임스페이스**

프로젝트에 추가된 파일에 대한 기본 네임스페이스를 지정합니다.

코드에서 네임스페이스를 만드는 방법에 대한 자세한 내용은 [네임스페이스](/dotnet/csharp/language-reference/keywords/namespace)를 참조하세요.

프로그래밍 방식으로 이 속성에 액세스하려면 <xref:VSLangProj.ProjectProperties.RootNamespace%2A>를 참조하세요.

**대상 프레임워크**

애플리케이션의 대상 .NET 버전을 지정합니다. 이 옵션은 컴퓨터에 설치된 .NET 버전에 따라 다른 값을 가질 수 있습니다.

.NET Framework 프로젝트의 경우 기본값은 프로젝트를 만들 때 지정한 대상 프레임워크와 일치합니다.

.NET Core를 대상으로 하는 프로젝트의 경우 사용 가능한 버전은 다음과 같이 나타날 수 있습니다.

![.NET Core 프로젝트에 대한 프레임워크 버전 대상 지정](../media/application-target-framework.png)

> [!NOTE]
> 대화 상자를 처음 열면 [필수 조건 대화 상자](../../ide/reference/prerequisites-dialog-box.md)에 나열된 필수 조건 패키지가 자동으로 설정됩니다. 이후에 프로젝트의 대상 프레임워크를 변경하는 경우 새 대상 프레임워크에 맞도록 필수 구성 요소를 수동으로 선택해야 합니다.

자세한 내용은 [Framework 대상 지정 개요](../../ide/visual-studio-multi-targeting-overview.md)를 참조하세요.

**출력 형식**

빌드할 애플리케이션 종류를 지정합니다. 값은 프로젝트 형식에 따라 달라집니다. 예를 들어 **콘솔 앱** 프로젝트의 경우 **Windows 애플리케이션**, **콘솔 애플리케이션** 또는 **클래스 라이브러리**를 출력 형식으로 지정할 수 있습니다.

웹 애플리케이션 프로젝트의 경우 **클래스 라이브러리**를 지정해야 합니다.

**출력 형식** 속성에 대한 자세한 내용은 [/target(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/target-compiler-option)을 참조하세요.

프로그래밍 방식으로 이 속성에 액세스하는 방법에 대한 자세한 내용은 <xref:VSLangProj.ProjectProperties.OutputType%2A>를 참조하세요.

**바인딩 리디렉션 자동 생성**

앱 또는 해당 구성 요소가 동일한 어셈블리의 버전을 두 개 이상 참조하는 경우 프로젝트에 바인딩 리디렉션이 추가됩니다. 프로젝트 파일에서 바인딩 리디렉션을 수동으로 정의하려는 경우 **바인딩 리디렉션 자동 생성**의 선택을 취소합니다.

리디렉션에 대한 자세한 내용은 [어셈블리 버전 리디렉션](/dotnet/framework/configure-apps/redirect-assembly-versions)을 참조하세요.

**시작 개체**

애플리케이션 로드 시 호출할 진입점을 정의합니다. 일반적으로 애플리케이션의 기본 폼이나 애플리케이션 시작 시 실행되어야 하는 `Main` 프로시저로 설정됩니다. 클래스 라이브러리에 진입점이 없기 때문에 이 속성의 유일한 옵션은 **(설정 안 함)** 입니다.

기본적으로, WPF 앱 프로젝트에서 이 옵션은 **(설정 안 함)** 으로 설정됩니다. 다른 옵션은 \[projectname].App입니다. WPF 프로젝트에서는 애플리케이션을 시작할 때 UI 리소스를 로드하도록 시작 URI를 설정해야 합니다. 이렇게 하려면 프로젝트에서 *Application.xaml* 파일을 열고, `StartupUri` 속성을 프로젝트의 *.xaml* 파일(예: *Window1.xaml*)로 설정합니다. 허용되는 루트 요소 목록은 <xref:System.Windows.Application.StartupUri%2A>를 참조하세요. 또한 프로젝트의 클래스에서 `public static void Main()` 메서드를 정의해야 합니다. 이 클래스는 **시작 개체** 목록에 *ProjectName.ClassName*으로 나타납니다. 그런 다음 클래스를 시작 개체로 선택할 수 있습니다.

자세한 내용은 [/main(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/main-compiler-option)을 참조하세요. 프로그래밍 방식으로 이 속성에 액세스하려면 <xref:VSLangProj.ProjectProperties.StartupObject%2A>를 참조하세요.

**어셈블리 정보**

이 단추를 클릭하면 [어셈블리 정보](../../ide/reference/assembly-information-dialog-box.md) 대화 상자가 열립니다.

## <a name="resources"></a>리소스

**리소스** 옵션을 통해 앱에 대한 리소스 설정을 구성할 수 있습니다.

**아이콘 및 매니페스트**

기본적으로 이 라디오 단추는 선택되며 **아이콘** 및 **매니페스트** 옵션이 사용됩니다. 이렇게 하면 사용자 고유의 아이콘을 선택하거나 다른 매니페스트 생성 옵션을 선택할 수 있습니다. 프로젝트에 대한 리소스 파일을 제공하지 않는 경우 이 라디오 단추를 선택된 상태로 둡니다.

**아이콘**

프로그램 아이콘으로 사용할 *.ico* 파일을 설정합니다. **찾아보기**를 클릭하여 기존 그래픽을 찾거나 원하는 파일의 이름을 입력합니다. 자세한 내용은 [/win32icon(C# 컴파일러 옵션)](/dotnet/csharp/language-reference/compiler-options/win32icon-compiler-option)을 참조하세요.

프로그래밍 방식으로 이 속성에 액세스하려면 <xref:VSLangProj.ProjectProperties.ApplicationIcon%2A>를 참조하세요.

아이콘을 만드는 방법에 대한 자세한 내용은 [아이콘을 위한 이미지 편집기](/cpp/windows/image-editor-for-icons)를 참조하세요.

**Manifest**

Windows Vista에서 UAC(사용자 계정 컨트롤)로 애플리케이션을 실행하는 경우 매니페스트 생성 옵션을 선택합니다. 이 옵션에 사용할 수 있는 값은 다음과 같습니다.

- **기본 설정으로 구성된 매니페스트 포함** Windows Vista에서 Visual Studio가 작동하는 일반적인 방식(`requestedExecutionLevel`을 `AsInvoker`로 지정하여 애플리케이션의 실행 파일에 보안 정보 포함)을 지원합니다. 기본 옵션입니다.

- **매니페스트 없이 애플리케이션 만들기** 이 방법을 *가상화*라고 합니다. 이 옵션은 이전 애플리케이션과의 호환성을 위해 사용합니다.

- **Properties\app.manifest**. 이 옵션은 ClickOnce 또는 등록이 필요하지 않은 COM에 의해 배포된 애플리케이션에 필요합니다. ClickOnce 배포를 사용하여 애플리케이션을 게시하면 **매니페스트**가 자동으로 이 옵션으로 설정됩니다.

**리소스 파일**

프로젝트에 대한 리소스 파일을 제공하는 경우 이 라디오 단추를 선택합니다. 이 옵션을 선택하면 **아이콘** 및 **매니페스트** 옵션이 사용되지 않습니다.

경로 이름을 입력하거나 찾아보기 단추( **...** )를 사용하여 Win32 리소스 파일을 프로젝트에 추가합니다.

자세한 내용은 [.NET 앱의 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)를 참조하세요.

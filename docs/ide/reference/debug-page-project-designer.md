---
title: 프로젝트 디자이너, 디버그 페이지
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16be10dc69f203e52eb0dccc0e0738399d37ee3d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649429"
---
# <a name="debug-page-project-designer"></a>프로젝트 디자이너, 디버그 페이지

**프로젝트 디자이너**의 **디버그** 페이지를 사용하여 Visual Basic 또는 C# 프로젝트에서 디버깅 동작의 속성을 설정합니다.

**디버그** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택합니다. **프로젝트** 메뉴에서 **\<ProjectName>속성**을 선택합니다. **프로젝트 디자이너**가 나타나면 **디버그** 탭을 클릭합니다.

> [!NOTE]
> 이 항목은 UWP 앱에 적용되지 않습니다. UWP 앱의 경우 [디버그 세션 시작(VB, C#, C++ 및 XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)을 참조하세요.

## <a name="configuration-and-platform"></a>구성 및 플랫폼

다음 옵션을 사용하면 표시하거나 수정할 구성 및 플랫폼을 선택할 수 있습니다.

**구성**

표시하거나 수정할 구성 설정을 지정합니다. 설정에는 **디버그**(기본값), **릴리스** 또는 **모든 구성**이 포함됩니다.

**플랫폼**

표시하거나 수정할 플랫폼 설정을 지정합니다. 선택 항목에는 **CPU**(기본값), **x64** 및 **x86**이 포함됩니다.

## <a name="start-action"></a>시작 작업

**시작 작업**은 프로젝트, 사용자 지정 프로그램, URL 등 애플리케이션을 디버깅할 때 시작할 항목을 나타냅니다. 기본적으로 이 옵션은 **프로젝트 시작**으로 설정되어 있습니다. **디버그** 페이지의 **시작 작업** 설정은 `StartAction` 속성의 값을 결정합니다.

**시작 프로젝트**

이 옵션을 선택하여 애플리케이션을 디버깅할 때 실행 파일(Windows 애플리케이션 및 콘솔 애플리케이션 프로젝트의 경우)이 시작되도록 지정합니다. 이 옵션은 기본적으로 선택됩니다.

**시작 외부 프로그램**

이 옵션을 선택하여 애플리케이션을 디버깅할 때 특정 프로그램을 시작하도록 지정합니다.

**URL로 브라우저 시작**

이 옵션을 선택하여 애플리케이션을 디버깅할 때 특정 URL에 액세스하도록 지정합니다.

## <a name="start-options"></a>시작 옵션

**명령줄 인수**

이 텍스트 상자에 디버깅에 사용할 명령줄 인수를 입력합니다.

**작업 디렉터리**

이 텍스트 상자에 프로젝트를 시작할 디렉터리를 입력합니다. 또는 찾아보기 단추( **...** )를 클릭하여 디렉터리를 선택합니다.

**원격 컴퓨터 사용**

원격 컴퓨터에서 애플리케이션을 디버깅하려면 이 확인란을 선택하고 텍스트 상자에 원격 컴퓨터에 대한 경로를 입력합니다.

## <a name="debugger-engines"></a>디버거 엔진

**네이티브 코드 디버깅 사용**

이 옵션은 네이티브 코드의 디버깅이 지원되는지를 지정합니다. COM 개체를 호출하는 경우 또는 프로젝트를 호출하는 네이티브 코드로 작성된 사용자 지정 프로그램을 시작하고 네이티브 코드를 디버깅해야 하는 경우 이 확인란을 선택합니다. 이 확인란의 선택을 취소하여 비관리 코드의 디버깅을 비활성화합니다. 이 확인란은 기본적으로 선택되어 있지 않습니다.

**SQL Server 디버깅 사용**

Visual Basic 애플리케이션에서 SQL 프로시저의 디버깅을 사용하거나 사용하지 않도록 설정하려면 이 확인란을 선택하거나 선택을 취소합니다. 이 확인란은 기본적으로 선택되어 있지 않습니다.

## <a name="see-also"></a>참조

- [디버거 소개](../../debugger/debugger-feature-tour.md)
- [C# 디버그 구성에 대한 프로젝트 설정](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic 디버그 구성에 대한 프로젝트 설정](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [ClickOnce 앱 보안](../../deployment/securing-clickonce-applications.md)
- [방법: 구성 만들기 및 편집](../../ide/how-to-create-and-edit-configurations.md)

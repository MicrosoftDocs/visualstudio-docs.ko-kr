---
title: 속성 페이지, JavaScript
ms.date: 06/21/2017
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6883e556cd70adddd45fd442d338e10d1cafa1e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926190"
---
# <a name="property-pages-javascript"></a>속성 페이지, JavaScript

**속성 페이지**는 프로젝트 설정에 대한 액세스를 제공합니다. **속성 페이지**에 표시되는 페이지를 사용하여 프로젝트 속성을 변경할 수 있습니다.

프로젝트 속성에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택합니다. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

**속성 페이지**에 표시되는 페이지와 옵션은 다음과 같습니다.

## <a name="configuration-and-platform-page"></a>구성 및 플랫폼 페이지

표시하거나 수정할 구성 및 플랫폼을 선택하려면 다음 옵션을 사용합니다.

 **Configuration**

표시하거나 수정할 구성 설정을 지정합니다. 설정에는 **디버그**(기본값), **릴리스**, **모든 구성** 또는 사용자 정의 구성이 있습니다. 자세한 내용은 [방법: Visual Studio에서 디버그 및 릴리스 구성 설정](../../debugger/how-to-set-debug-and-release-configurations.md)을 참조하세요.

 **플랫폼**

표시하거나 수정할 플랫폼 설정을 지정합니다. 설정에는 **임의 CPU**([!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] 앱의 경우 기본값), **x64**, **ARM**, **x86** 또는 사용자 정의 플랫폼이 포함됩니다. 자세한 내용은 [방법: Visual Studio에서 디버그 및 릴리스 구성 설정](../../debugger/how-to-set-debug-and-release-configurations.md)을 참조하세요.

## <a name="general-page"></a>일반 페이지

프로젝트의 일반 속성을 설정하려면 다음 옵션을 사용합니다.

> [!NOTE]
> 일부 옵션은 UWP 앱에서만 사용할 수 있습니다.

 **출력 경로**

프로젝트 구성에 대한 출력 파일의 위치를 지정합니다. 상대 경로입니다. 절대 경로를 입력하면 프로젝트에 절대 경로가 저장됩니다. 기본 경로는 bin\Debug입니다.

단순화된 빌드 구성을 사용하면 프로젝트 시스템에서 디버그 버전을 빌드할지 아니면 릴리스 버전을 빌드할지 결정합니다. **디버그**,  > 디버깅 시작**을 클릭하면**(또는 **F5** 키 누르기) 지정한 **출력 경로**와 관계없이 빌드가 디버그 위치에 배치됩니다. 그러나 **빌드** 메뉴의 **솔루션 빌드** 명령을 사용하면 지정한 위치에 빌드가 배치됩니다. 고급 빌드 구성을 사용하도록 설정하려면 메뉴 모음에서 **도구** > **옵션**을 선택합니다. **옵션** 대화 상자에서 **프로젝트 및 솔루션**을 확장하고 **일반**을 선택한 다음 **고급 빌드 구성 표시** 확인란의 선택을 취소합니다. 이렇게 하면 모든 구성 값 및 디버그 버전을 빌드하는지 릴리스 버전을 빌드하는지 여부를 수동으로 제어할 수 있게 됩니다.

 **기본 언어**

프로젝트의 기본 언어를 지정합니다. 제어판의 **시계, 언어 및 국가별 옵션**에서 선택한 언어 옵션은 사용자의 기본 설정 언어를 지정합니다. 프로젝트의 기본 언어를 지정하면 사용자의 기본 설정 언어가 애플리케이션에서 제공되는 언어 리소스와 일치하지 않는 경우 지정된 기본 언어 리소스가 사용됩니다.

## <a name="debug-page"></a>디버그 페이지

프로젝트의 디버깅 동작에 대한 속성을 설정하려면 다음 옵션을 사용합니다.

> [!NOTE]
> 일부 옵션은 UWP 앱에서만 사용할 수 있습니다.

 **실행할 디버거**

디버거에 대한 기본 호스트를 지정합니다.

- Visual Studio 호스트 컴퓨터에서 애플리케이션을 시작하려면 **로컬 컴퓨터**를 선택합니다. 자세한 내용은 [로컬 컴퓨터에서 Windows 스토어 앱 실행](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)을 참조하세요.

- 시뮬레이터에서 애플리케이션을 시작하려면 **시뮬레이터**를 선택합니다. 자세한 내용은 [시뮬레이터에서 Windows 스토어 앱 실행](../../debugger/run-windows-store-apps-in-the-simulator.md)을 참조하세요.

- 원격 컴퓨터에서 애플리케이션을 시작하려면 **원격 컴퓨터**를 선택합니다. 원격 디버깅에 대한 자세한 내용은 [원격 컴퓨터에서 Windows 스토어 앱 실행](../../debugger/run-windows-store-apps-on-a-remote-machine.md)을 참조하세요.

**애플리케이션 시작**

**F5** 키를 누르거나 **디버그** > **디버깅 시작**을 클릭하면 애플리케이션을 시작하는지 여부를 지정합니다. 애플리케이션을 시작하려면 **예**를 선택하고, 그렇지 않은 경우 **아니요**를 선택합니다. **아니요**를 선택하더라도 애플리케이션을 시작하는 다른 방법을 사용하는 경우 애플리케이션을 디버그할 수 있습니다.

**디버거 형식**

디버그할 코드 형식을 지정합니다. JavaScript 코드를 디버그하려면 **스크립트만**을 선택합니다. 공용 언어 런타임에 의해 관리되는 코드를 디버그하려면 **관리 전용**을 선택합니다. C++ 코드를 디버그하려면 **네이티브 전용**을 선택합니다. C++ 및 JavaScript를 디버그하려면 **스크립트가 포함된 네이티브 코드**를 선택합니다. 관리 코드와 C++ 코드를 모두 디버그하려면 **혼합(관리/네이티브)** 을 선택합니다.

**로컬 네트워크 루프백 허용**

앱 테스트를 위해 IP 루프백 주소에 대한 액세스가 허용되는지 여부를 지정합니다. 클라이언트 앱이 서버 애플리케이션이 실행 중인 컴퓨터와 동일한 컴퓨터에 있는 경우 루프백 주소 사용을 허용하려면 **예**를 선택하고, 그렇지 않은 경우 **아니요**를 선택합니다. 이 속성은 **실행할 디버거** 속성이 **원격 컴퓨터**로 설정된 경우에만 사용할 수 있습니다.

**컴퓨터 이름**

디버거를 호스트할 원격 컴퓨터의 이름을 지정합니다. 이 속성은 **실행할 디버거**가 **원격 컴퓨터**로 설정된 경우에만 사용할 수 있습니다.

**인증 필요**

원격 컴퓨터에 인증이 필요한지 여부를 지정합니다. 이 속성은 **실행할 디버거**가 **원격 컴퓨터**로 설정된 경우에만 사용할 수 있습니다.

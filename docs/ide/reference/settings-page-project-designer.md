---
title: 설정 페이지, 프로젝트 디자이너
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f4ca1def334241999445e3f11cf142aa426d962
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566776"
---
# <a name="settings-page-project-designer"></a>설정 페이지, 프로젝트 디자이너

프로젝트 디자이너의 **설정** 페이지를 사용하여 프로젝트의 애플리케이션 설정을 지정합니다. 애플리케이션 설정을 통해 애플리케이션에 대한 속성 설정 및 기타 정보를 동적으로 저장 및 검색할 수 있습니다. 또한 클라이언트 컴퓨터에서 사용자 지정 애플리케이션 및 사용자 기본 설정을 유지 관리할 수도 있습니다. 자세한 내용은 [애플리케이션 설정 관리](../managing-application-settings-dotnet.md)를 참조하세요.

**설정** 페이지에 액세스하려면 **솔루션 탐색기**에서 프로젝트 노드를 선택하고 **프로젝트** > **속성**을 선택합니다. 프로젝트 디자이너가 나타나면 **설정** 탭을 선택합니다.

## <a name="header-bar"></a>머리글 표시줄

**설정** 페이지의 맨 위에 있는 머리글 표시줄에는 여러 가지 컨트롤이 있습니다.

**동기화**

**동기화**는 런타임에 또는 디버깅 중에 애플리케이션이 사용하는 사용자 범위 설정을 디자인 타임 시 정의된 기본값으로 복원합니다. 데이터를 복원하려면 런타임에 생성된 애플리케이션 관련 파일을 프로젝트 데이터가 아닌 디스크에서 제거합니다.

**웹 설정 로드**

**웹 설정 로드**는 인증된 사용자 또는 익명 사용자에 대한 설정을 로드할 수 있는 **로그인** 대화 상자를 표시합니다. 이 단추는 **서비스** 페이지에서 클라이언트 애플리케이션 서비스를 활성화하고 **웹 설정 서비스 위치**를 지정한 경우에만 활성화됩니다.

**코드 보기**

C# 프로젝트의 경우 **코드 보기** 단추를 통해 *Settings.cs* 파일의 코드를 볼 수 있습니다. 이 파일은 `Settings` 개체에서 특정 이벤트를 처리할 수 있도록 하는 `Settings` 클래스를 정의합니다. Visual Basic 이외의 언어에서는 사용자 설정을 유지하기 위해 이 래퍼 클래스의 `Save` 메서드를 명시적으로 호출해야 합니다. 일반적으로 기본 폼의 **Closing** 이벤트 처리기에서 이 작업을 수행합니다. 아래에 `Save` 메서드 호출의 예가 나와 있습니다.

```csharp
Properties.Settings.Default.Save();
```

Visual Basic 프로젝트의 경우 **코드 보기** 단추를 통해 *Settings.vb* 파일의 코드를 볼 수 있습니다. 이 파일은 `My.Settings` 개체에서 특정 이벤트를 처리할 수 있도록 하는 `MySettings` 클래스를 정의합니다. `My.Settings` 개체를 사용하여 애플리케이션 설정에 액세스하는 방법에 대한 자세한 내용은 [애플리케이션 설정 액세스](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)를 참조하세요.

애플리케이션 설정에 대한 자세한 내용은 [Windows Forms에 대한 애플리케이션 설정 개요](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms)를 참조하세요.

**액세스 한정자**

**액세스 한정자** 단추는 Visual Studio가 *Settings.Designer.cs* 또는 *Settings.Designer.vb*에서 생성하는 `Properties.Settings`(C#) 또는 `My.Settings`(Visual Basic) 도우미 클래스의 액세스 수준을 지정합니다.

Visual C# 프로젝트의 경우 액세스 한정자는 **Internal** 또는 **Public**일 수 있습니다.

Visual Basic 프로젝트의 경우 액세스 한정자는 **Friend** 또는 **Public**일 수 있습니다.

기본적으로 설정은 C#에서는 **Internal**이고 Visual Basic에서는 **Friend**입니다. Visual Studio에서 도우미 클래스를 **Internal** 또는 **Friend**로 생성하는 경우 실행 가능한( *.exe*) 애플리케이션은 클래스 라이브러리( *.dll* 파일)에 추가한 리소스 및 설정에 액세스할 수 없습니다. 클래스 라이브러리에서 리소스 및 설정을 공유해야 하는 경우 액세스 한정자를 **Public**으로 설정합니다.

설정 도우미 클래스에 대한 자세한 내용은 [애플리케이션 설정 관리](../managing-application-settings-dotnet.md)를 참조하세요.

## <a name="settings-grid"></a>설정 표

**설정 표**는 애플리케이션 설정을 구성하는 데 사용됩니다. 이 표에는 다음과 같은 열이 포함됩니다.

**이름**

이 필드에 애플리케이션 설정 이름을 입력합니다.

**형식**

드롭다운 목록을 사용하여 설정 형식을 선택합니다. 가장 자주 사용하는 형식이 드롭다운 목록에 나타납니다. 예를 들어, **String**, **(연결 문자열)** 및 **System.Drawing.Font**입니다. 목록 끝에서 **찾아보기**를 선택한 다음, **형식 선택** 대화 상자에서 형식을 선택하여 다른 형식을 선택할 수 있습니다. 형식을 선택하면 드롭다운 목록의 일반 형식에 추가됩니다(현재 솔루션만 해당).

**범위**

**애플리케이션** 또는 **사용자**를 선택합니다.

연결 문자열과 같은 애플리케이션 범위 설정은 애플리케이션에 연결됩니다. 사용자는 런타임에 애플리케이션 범위 설정을 변경할 수 없습니다.

시스템 글꼴과 같은 사용자 범위 설정은 사용자 기본 설정에 사용하기 위한 것입니다. 사용자는 런타임에 이를 변경할 수 있습니다.

**값**

애플리케이션 설정과 연결된 데이터 또는 값입니다. 예를 들어 설정이 글꼴인 경우 값은 **Verdana, 9.75pt, style=Bold**일 수 있습니다.

## <a name="see-also"></a>참고 항목

- [애플리케이션 설정 관리](../managing-application-settings-dotnet.md)
- [애플리케이션 설정 액세스(Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)

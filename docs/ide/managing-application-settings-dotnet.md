---
title: 애플리케이션 설정 관리(.NET)
description: 애플리케이션 코드에 포함되지 않지만 런타임에 필요한 애플리케이션 설정(이전에는 동적 속성이라 함)을 관리하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62e03210e83f434bd32d08c3fe0f7b2b539155e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596900"
---
# <a name="manage-application-settings-net"></a>애플리케이션 설정 관리(.NET)

애플리케이션 설정을 사용하여 애플리케이션 정보를 동적으로 저장할 수 있습니다. 설정을 사용하면 애플리케이션 코드(예: 연결 문자열), 사용자 기본 설정 및 런타임에 필요한 기타 정보에 포함되지 않아야 하는 정보를 클라이언트 컴퓨터에 저장할 수 있습니다.

애플리케이션 설정은 이전 버전의 Visual Studio에서 사용되던 동적 속성을 대체합니다.

각 애플리케이션 설정의 이름은 고유해야 합니다. 이 이름은 문자, 숫자, 숫자로 시작하지 않는 밑줄 등을 조합하여 사용할 수 있으며 공백이 있을 수 없습니다. 이름은 `Name` 속성을 통해 변경됩니다.

애플리케이션 설정은 XML로 serialize하는 데이터 형식 또는 `ToString`/`FromString`를 구현하는 `TypeConverter`이 있는 데이터 형식으로 저장할 수 있습니다. 가장 일반적인 형식은 `String`, `Integer`및 `Boolean`이지만 <xref:System.Drawing.Color>, <xref:System.Object>또는 연결 문자열로도 값을 저장할 수 있습니다.

애플리케이션 설정은 값도 보유합니다. 값은 **Value** 속성을 사용하여 설정되며 설정의 데이터 형식과 일치해야 합니다.

또한 디자인 타임에 애플리케이션 설정을 폼이나 컨트롤의 속성에 바인딩할 수 있습니다.

애플리케이션 설정은 범위에 따라 다음 두 가지 유형으로 분류됩니다.

- 애플리케이션 범위 설정은 웹 서비스에 대한 URL 또는 데이터베이스 연결 문자열과 같은 정보에 사용될 수 있습니다. 이러한 값은 애플리케이션과 연결되어 있으므로 사용자가 런타임에 변경할 수 없습니다.

- 사용자 범위 설정은 폼의 마지막 위치 또는 글꼴 기본 설정 지속 등의 정보에 사용될 수 있습니다. 사용자는 런타임에 이러한 값을 변경할 수 있습니다.

**Scope** 속성을 사용하여 설정 유형을 변경할 수 있습니다.

프로젝트 시스템은 애플리케이션 설정을 두 개의 XML 파일에 저장합니다.

- *app.config* 파일은 첫 번째 애플리케이션 설정을 만들 때 디자인 타임에 만들어집니다.

- *user.config* 파일은 애플리케이션을 실행하는 사용자가 사용자 설정 값을 변경할 때 런타임 시 만들어집니다.

애플리케이션에서 디스크에 쓰는 메서드를 명확하게 호출하지 않으면 사용자 설정의 변경 내용은 디스크에 쓰여지지 않습니다.

## <a name="create-application-settings-at-design-time"></a>디자인 타임에 애플리케이션 설정 만들기

디자인 타임에 **프로젝트 디자이너** 의 **설정** 페이지를 사용하거나 폼 또는 컨트롤의 **속성** 창을 사용하여 애플리케이션 설정을 만든 다음 설정을 속성에 바인딩할 수 있습니다.

애플리케이션 범위 설정(예: 데이터베이스 연결 문자열 또는 서버 리소스에 대한 참조)을 만들 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 에서는 `<applicationSettings>` 태그를 사용하여 해당 설정을 *app.config* 에 저장합니다. 연결 문자열은 `<connectionStrings>` 태그 아래 저장됩니다.

사용자 범위 설정(예: 기본 글꼴, 홈 페이지 또는 창 크기)을 만들 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 에서는 `<userSettings>` 태그를 사용하여 해당 설정을 *app.config* 에 저장합니다.

> [!IMPORTANT]
> 연결 문자열을 *app.config* 에 저장할 경우 연결 문자열에 있는 암호나 서버 경로 등의 중요한 정보가 누설되지 않도록 주의해야 합니다.
>
> 사용자가 사용자 ID와 암호를 입력하는 경우와 같이 외부 소스에서 연결 문자열 정보를 가져올 경우, 연결 문자열의 생성에 사용하는 값에 연결 동작을 변경하는 추가 연결 문자열 매개 변수가 포함되지 않도록 주의해야 합니다.
>
> 보호되는 구성 기능을 사용하여 구성 파일의 중요한 정보를 암호화할 수 있습니다. 자세한 내용은 [연결 정보 보호](/dotnet/framework/data/adonet/protecting-connection-information)를 참조하세요.

> [!NOTE]
> 클래스 라이브러리에 대한 구성 파일 모델은 없으므로 클래스 라이브러리 프로젝트에 대해서는 애플리케이션 설정이 적용되지 않습니다. 구성 파일을 가질 수 있는 Visual Studio Tools for Office DLL 프로젝트의 경우는 예외입니다.

## <a name="use-customized-settings-files"></a>사용자 지정 설정 파일 사용

설정 그룹을 편리하게 관리할 수 있도록 프로젝트에 사용자 지정 설정 파일을 추가할 수 있습니다. 단일 파일에 포함된 설정은 단위로 로드되어 저장됩니다. 자주 사용하는 그룹과 별로 사용하지 않는 그룹에 대해 별도의 파일에 설정을 저장하면 설정 로드 및 저장 시에 시간을 절약할 수 있습니다.

예를 들어, 프로젝트에 *SpecialSettings.settings* 와 같은 파일을 추가할 수 있습니다. `SpecialSettings` 클래스는 `My` 네임스페이스에서 노출되지 않지만 **코드 보기** 를 사용하면 `Partial Class SpecialSettings`가 포함된 사용자 지정 설정 파일을 읽을 수 있습니다.

**설정 디자이너** 는 먼저 프로젝트 시스템에서 생성되는 *Settings.settings* 파일을 검색합니다. 이 파일은 **프로젝트 디자이너** 가 **설정** 탭에 표시하는 기본 파일입니다. *Settings.settings* 는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 프로젝트의 *My Project* 폴더와 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 프로젝트의 *Properties* 폴더에 있습니다. 그런 다음, **프로젝트 디자이너** 는 프로젝트 루트 폴더에서 다른 설정 파일을 검색합니다. 그러므로 사용자 지정 설정 파일을 해당 폴더에 배치해야 합니다. 프로젝트의 다른 위치에 *.settings* 파일을 추가하면 **프로젝트 디자이너** 가 해당 파일을 찾을 수 없습니다.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Visual Basic에서 런타임에 애플리케이션 설정 액세스 또는 변경

Visual Basic 프로젝트에서는 런타임에 `My.Settings` 개체를 사용하여 애플리케이션 설정에 액세스할 수 있습니다. **설정** 페이지에서 **코드 보기** 단추를 클릭하여 *Settings.vb* 파일을 볼 수 있습니다. *Settings.vb* 에 정의된 `Settings` 클래스를 통해 사용자는 설정 클래스에서 <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>, <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> 등의 이벤트를 처리할 수 있습니다. *Settings.vb* 의 `Settings` 클래스는 사용자 소유 코드만 표시하고 전체적으로 생성된 클래스는 표시하지 않는 partial 클래스입니다. `My.Settings` 개체를 사용하여 애플리케이션 설정에 액세스하는 방법에 대한 자세한 내용은 [애플리케이션 설정 액세스(.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)를 참조하세요.

사용자가 런타임에 변경하는 사용자 범위 설정(예: 폼의 위치)의 값은 *user.config* 파일에 저장됩니다. 기본값은 여전히 *app.config* 에 저장되어 있습니다.

애플리케이션을 테스트할 때와 같이 런타임에 사용자 범위 설정을 변경하고 해당 설정을 기본값으로 다시 설정하려는 경우 **동기화** 버튼을 클릭합니다.

설정에 액세스할 때는 `My.Settings` 개체와 기본 *.settings* 파일을 사용하는 것이 좋습니다. 이는 **설정 디자이너** 를 사용하여 설정에 속성을 할당할 수 있을 뿐 아니라 사용자 속성이 애플리케이션이 종료되기 전에 자동으로 저장되기 때문입니다. 그러나 Visual Basic 애플리케이션에서 설정에 직접 액세스할 수 있습니다. 이 경우 `MySettings` 클래스에 액세스하고 프로젝트 루트의 사용자 지정 *.settings* 파일을 사용해야 합니다. 애플리케이션을 끝내기 전에 사용자 설정을 저장해야 합니다. C# 애플리케이션의 경우도 마찬가지이며 이는 다음 단원에서 설명합니다.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>C#에서 런타임에 애플리케이션 설정 액세스 또는 변경
<!-- markdownlint-enable MD003 MD020 -->

Visual Basic을 제외한 C# 등의 언어에서는 다음 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 예제에서와 같이 `Settings` 클래스에 직접 액세스해야 합니다.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

사용자 설정을 유지하기 위해 이 래퍼 클래스의 `Save` 메서드를 명시적으로 호출해야 합니다. 일반적으로 기본 폼의 `Closing` 이벤트 처리기에서 이 작업을 수행합니다. 다음 C# 예제에서는 `Save` 메서드를 호출하는 방법을 보여 줍니다.

```csharp
Properties.Settings.Default.Save();
```

`Settings` 클래스를 통해 애플리케이션 설정에 액세스하는 방법에 대한 일반적인 내용은 [애플리케이션 설정 개요(.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview)를 참조하세요. 설정 반복에 대한 자세한 내용은 이 [포럼 게시물](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral)을 참조하세요.

## <a name="see-also"></a>추가 정보

- [애플리케이션 설정 액세스(.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)

---
title: -ResetSettings(devenv.exe)
description: ResetSettings devenv 명령줄 스위치를 사용하여 Visual Studio 기본 설정을 복원하고 Visual Studio IDE를 자동으로 시작하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e523738ff23b40c80b5df21d90b582d94c59087f
ms.sourcegitcommit: a8031c1387d2090129ed33e063744f9f31653dcd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/01/2021
ms.locfileid: "110724540"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings(devenv.exe)

Visual Studio 기본 설정을 복원하고 자동으로 Visual Studio IDE를 시작합니다. 이 스위치는 필요에 따라 설정을 지정한 설정 파일(`*.vssettings`)로 다시 설정합니다.

기본 설정은 Visual Studio가 처음 시작될 때 선택된 프로필에서 가져옵니다.

> [!TIP]
> IDE(통합된 개발 환경)를 사용하여 설정을 다시 설정하는 방법을 알아보려면 [설정 다시 설정](../environment-settings.md#reset-settings)을 참조하세요.

## <a name="syntax"></a>구문

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>인수

- *SettingsFile*

  선택 사항입니다. Visual Studio에 적용할 `.vssettings` 파일의 전체 경로와 이름입니다.

- *DefaultCollectionSpecifier*

  선택 사항입니다. 복원할 설정의 기본 컬렉션을 나타내는 지정자입니다. 표에 나열된 기본 컬렉션 지정자 중 하나를 선택합니다.

  | 기본 컬렉션 이름 | 컬렉션 지정자 |
  | --- | --- |
  | **일반** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **웹 개발** | `Web` |
  | **웹 개발(코드 전용)** | `WebCode` |

## <a name="remarks"></a>설명

*SettingsFile* 을 지정하지 않으면 IDE가 기존 설정을 사용하여 열립니다. 


## <a name="example"></a>예제

첫 번째 예제에서는 `MySettings.vssettings` 파일에 저장된 설정을 적용합니다.

두 번째 예제에서는 Visual C# 기본 프로필을 복원합니다.

세 번째 예제에서는 설정을 적용한 후 Visual Studio를 닫습니다. `/Command "File.Exit"`를 추가할 수 있습니다.

```shell
devenv /ResetSettings "%USERPROFILE%\MySettings.vssettings"

devenv /ResetSettings CSharp

devenv /NoSplash /ResetSettings General /Command Exit 
```

## <a name="see-also"></a>추가 정보

- [환경 설정](../environment-settings.md)
- [Visual Studio IDE 개인 설정](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)

---
title: XAML 핫 다시 로드 문제 해결
description: XAML 핫 다시 로드에서 발생할 수 있는 문제를 해결 합니다.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 73d8653b2bcf06801c18e21d9a13b21843abc7d7
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82921252"
---
# <a name="troubleshooting-xaml-hot-reload"></a>XAML 핫 다시 로드 문제 해결

이 문제 해결 가이드에는 XAML 핫 재로드가 제대로 작동 하지 못하게 하는 대부분의 문제를 해결 해야 하는 자세한 지침이 포함 되어 있습니다.

WPF 및 UWP 앱에는 XAML 핫 다시 로드가 지원 됩니다. 운영 체제 및 도구 요구 사항에 대 한 자세한 내용은 [Xaml 핫 다시 로드를 사용 하 여 실행 중인 xaml 코드 작성 및 디버그](xaml-hot-reload.md)를 참조 하세요.

## <a name="hot-reload-is-not-available"></a>핫 다시 로드를 사용할 수 없습니다.

앱을 디버그 하는 동안 앱 내 도구 모음에서 "핫 다시 로드를 사용할 수 없습니다." 라는 메시지가 표시 되 면이 문서에 설명 된 지침에 따라 문제를 해결 합니다.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>XAML 핫 다시 로드를 사용할 수 있는지 확인

이 기능은 기본적으로 사용 하도록 설정 되어 있습니다. 앱 디버깅을 시작할 때 XAML 핫 다시 로드를 사용할 수 있는지 확인 하는 앱 내 도구 모음이 표시 되는지 확인 합니다.

![XAML 핫 다시 로드 사용 가능](../debugger/media/xaml-hot-reload-available.png)

앱 내 도구 모음이 표시 되지 않으면**일반** **디버그** > **옵션** > 을 엽니다. 두 옵션, **xaml 용 UI 디버깅 도구 사용** 및 **Xaml 핫 다시 로드 사용** 이 선택 되어 있는지 확인 합니다.

![XAML 핫 다시 로드 사용](../debugger/media/xaml-hot-reload-enable.png)

이러한 옵션을 선택한 경우 라이브 시각적 트리 (**디버그** > **Windows** > **라이브 시각적 트리**)로 이동 하 고 응용 프로그램 도구 모음 **에 런타임 도구 표시** 단추 (맨 왼쪽)를 선택 해야 합니다.

![XAML 핫 다시 로드 사용](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>프로세스에 연결 하는 대신 디버깅 시작을 사용 하는지 확인 합니다.

XAML 핫 다시 로드는 응용 프로그램이 시작 `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` 될 때 환경 변수를 1로 설정 해야 합니다. Visual Studio는 **디버그** > **디버깅 시작** 또는 **F5**명령의 일부로이를 자동으로 설정 합니다. **디버그** > **프로세스에 연결** 명령을 대신 사용 하 여 XAML 핫 다시 로드를 사용 하려면 환경 변수를 직접 설정 합니다.

> [!NOTE]
> 환경 변수를 설정 하려면 시작 단추를 사용 하 여 "환경 변수"를 검색 하 고 **시스템 환경 변수 편집**을 선택 합니다. 열리는 대화 상자에서 **환경 변수**를 선택한 다음 사용자 변수로 추가 하 고 값을로 `1`설정 합니다. 정리 하려면 디버깅을 마친 후 변수를 제거 합니다.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>MSBuild 속성이 올바른지 확인

기본적으로 소스 정보는 디버그 구성에 포함 됩니다. 프로젝트 파일 (예: * .csproj)의 MSBuild 속성에 의해 제어 됩니다. WPF의 경우 속성 `XamlDebuggingInformation`은 이며로 `True`설정 되어야 합니다. UWP의 경우 속성 `DisableXbfLineInfo`은 이며로 `False`설정 되어야 합니다. 다음은 그 예입니다. 

WPF:

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>올바른 빌드 구성 이름을 사용 하 고 있는지 확인 하십시오.

XAML 핫 다시 로드 (이전 섹션 참조)를 지원 하도록 올바른 MSBuild 속성을 수동으로 설정 하거나 기본 빌드 구성 이름 (디버그)을 사용 해야 합니다. MSBuild 속성을 올바르게 설정 하지 않으면 사용자 지정 빌드 구성 이름이 작동 하지 않고 릴리스 빌드가 되지 않습니다.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>XAML 파일에 오류가 없는지 확인 합니다.

XAML 파일에 **오류 목록**오류가 표시 되 면 Xaml 핫 다시 로드가 작동 하지 않을 수 있습니다.

## <a name="see-also"></a>참고 항목

[XAML 핫 다시 로드를 사용 하 여 실행 중인 XAML 코드 작성 및 디버그](xaml-hot-reload.md)

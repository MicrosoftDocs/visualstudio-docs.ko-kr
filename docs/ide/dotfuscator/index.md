---
title: Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator CE, Dotfuscator Community, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 보호, community edition, 난독 처리, .NET, 무료, Visual Studio 2019, Visual Studio 2017, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
description: Visual Studio에 포함된 Dotfuscator Community 무료 복사본을 사용하여 .NET 애플리케이션을 보호하는 방법을 알아봅니다.
ms.assetid: d9550502-0a82-49a6-b005-2caa791fbe02
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: f1b2c0bfd4adbd4a952a64f20fc3d2639a8abb5f
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/21/2020
ms.locfileid: "75918440"
---
# <a name="dotfuscator-community"></a>Dotfuscator Community

***PreEmptive Protection - Dotfuscator***는 보안 소프트웨어 개발 수명 주기에 맞도록 손쉽게 조정되는 포괄적인 .NET 애플리케이션 보호 기능을 제공합니다.
이 프로그램을 사용하여 데스크톱, 모바일, 서버 및 포함된 애플리케이션을 강화, 보호 및 정리함으로써 거래 비밀 및 기타 IP(지적 재산권)를 보호하고, 불법 복제 및 위조를 줄이고, 변조 및 무단 디버깅으로부터 보호하는 데 도움을 얻을 수 있습니다.
Dotfuscator는 추가적인 프로그래밍이나 소스 코드 액세스 없이도 컴파일된 어셈블리에 작동합니다.

![PreEmptive Protection - Dotfuscator](media/header.svg)

## <a name="why-protection-matters"></a>보호가 중요한 이유

**IP(지적 재산권)을 보호**하는 일은 매우 중요합니다.
애플리케이션의 코드에는 IP로 간주할 수 있는 디자인 및 구현 세부 정보가 포함되어 있습니다.
그렇지만 .NET Framework에서 빌드된 애플리케이션에는 [중요한 메타데이터 및 고급 중간 코드][assemblies]가 포함되어 있으며 이러한 항목들은 수많은 무료 자동화 도구 중 하나만으로 쉽게 리버스 엔지니어링할 수 있습니다.
리버스 엔지니어링을 중단하고 중지하여 무단 IP 공개를 방지하고 코드에 영업 비밀이 포함되어 있음을 알릴 수 있습니다.
Dotfuscator는 원래 애플리케이션 동작은 유지하면서 .NET 어셈블리를 [난독 처리][obfuscation]하여 리버스 엔지니어링을 방지할 수 있습니다.

**애플리케이션의 무결성을 보호**하는 것도 중요합니다.
리버스 엔지니어링 외에도 악의적인 사용자가 애플리케이션을 불법 복제하거나, 런타임에 애플리케이션의 동작을 변경하거나, 데이터를 조작하려고 할 수 있습니다.
Dotfuscator는 변조, 제3자 디버깅 및 루팅된 디바이스를 비롯한 [무단 사용을 감지 및 반응][checks]하는 기능을 애플리케이션에 삽입합니다.

Dotfuscator를 보안 소프트웨어 개발 수명 주기에 적용하는 방법에 대한 자세한 내용은 PreEmptive Solutions의 [SDL 응용 프로그램 보호 페이지][sdl-protection]를 참조하세요.

## <a name="about-dotfuscator-community"></a>Dotfuscator Community 정보

Microsoft Visual Studio 복사본에는 ***PreEmptive Protection - Dotfuscator Community*** 복사본이 있으며, 개인 용도로 사용 시 무료로 제공됩니다.
(이 무료 버전을 이전에는 Dotfuscator Community Edition 또는 Dotfuscator CE라고 했습니다.) Visual Studio에 포함된 Dotfuscator Community 버전을 설치하는 방법에 대한 지침은 [설치 페이지][install]를 참조하세요.

Dotfuscator Community는 개발자, 설계자 및 테스터를 위한 광범위한 [소프트웨어 보호 및 보안 강화][software-protection] 서비스를 제공합니다.
Dotfuscator Community에 포함된 [.NET Obfuscation][obfuscation] 및 기타 [애플리케이션 보호][app-protection] 기능의 예는 다음과 같습니다.

* 식별자 *[이름 바꾸기][renaming]* : 컴파일된 어셈블리의 리버스 엔지니어링을 더 어렵게 만듭니다.
* *[변조 방지][tamper]* : 변조된 애플리케이션의 실행을 감지하고 변조된 세션을 종료하거나 이러한 세션에 응답합니다.
* *[디버그 방지][debug]* : 실행 중인 애플리케이션에 대한 디버거 연결을 감지하고 디버그된 세션을 종료하거나 이러한 세션에 응답합니다.
* *[루팅 방지 디바이스][root]* : 루팅된 Android 디바이스에서 애플리케이션이 실행되고 있는지 감지하고 해당 디바이스의 세션을 종료하거나 세션에 응답합니다.
* *[애플리케이션 만료 동작][shelflife]* : “수명 종료” 날짜를 인코딩하고 만료된 애플리케이션 세션을 종료합니다.

이러한 기능과 이러한 기능이 애플리케이션 보호 전략에 맞게 조정되는 방법에 대한 자세한 내용은 [기능 페이지][capabilities]를 참조하세요.

Dotfuscator Community는 통합된 기본 보호 기능을 제공합니다.
Dotfuscator Community에 등록한 사용자와 전 세계에서 널리 사용되고 있는 [.NET Obfuscator][net-obfuscator].인 ***PreEmptive Protection - Dotfuscator Professional*** 사용자는 더 많은 애플리케이션 보호 조치를 사용할 수 있습니다.
Dotfuscator를 강화하는 방법에 대한 자세한 내용은 [업그레이드 페이지][upgrades]를 참조하세요.

## <a name="getting-started"></a>시작

::: moniker range="vs-2019"

Visual Studio에서 Dotfuscator Community 사용을 시작하려면 **검색 상자**(Ctrl+Q)에 `dotfuscator`를 입력합니다.

* Dotfuscator Community가 이미 설치되어 있는 경우, **검색 상자**의 ‘메뉴’ 제목 아래에 Dotfuscator Community를 시작하는 옵션이 표시됩니다.  자세한 내용은 [전체 Dotfuscator Community 사용자 가이드의 시작하기][get-started] 페이지를 참조하세요.
* Dotfuscator Community가 아직 설치되지 않은 경우, **검색 상자**의 ‘개별 구성 요소’ 제목 아래에 **PreEmptive Protection - Dotfuscator 설치**가 표시됩니다.  자세한 내용은 [설치 페이지][install]를 참조하세요.

::: moniker-end

::: moniker range="vs-2017"

Visual Studio에서 Dotfuscator Community 사용을 시작하려면 **빠른 실행**(Ctrl+Q) 검색 창에 `dotfuscator`를 입력합니다.

* Dotfuscator Community가 이미 설치되어 있으면 **빠른 실행**에 Dotfuscator Community 사용자 인터페이스를 시작하는 ‘메뉴’ 옵션이 표시됩니다.  자세한 내용은 [전체 Dotfuscator Community 사용자 가이드의 시작하기][get-started] 페이지를 참조하세요.
* Dotfuscator Community가 아직 설치되어 있지 않은 경우 **빠른 실행**에 관련 ‘설치’ 옵션이 표시됩니다.  자세한 내용은 [설치 페이지][install]를 참조하세요.

::: moniker-end

[preemptive.com의 Dotfuscator 다운로드 페이지][download]에서 Dotfuscator Community의 **최신 버전**을 가져올 수도 있습니다.

## <a name="full-documentation"></a>전체 설명서

이 페이지와 해당 하위 페이지에는 Dotfuscator Community 기능에 대한 간략한 개요와 [도구 설치 지침][install]이 제공되어 있습니다.

[Dotfuscator Community 사용자 인터페이스 사용을 시작하는 방법][get-started]을 비롯한 자세한 사용 지침은 [preemptive.com의 전체 Dotfuscator Community 사용자 가이드][full]를 참조하세요.

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[software-protection]:  https://www.preemptive.com/software-protection
[obfuscation]:  https://www.preemptive.com/obfuscation
[app-protection]:  https://www.preemptive.com/application-protection
[sdl-protection]:  https://www.preemptive.com/solutions/SDL-App-Protection
[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[download]:  https://www.preemptive.com/products/dotfuscator/downloads

[install]:  install.md
[capabilities]:  capabilities.md
[upgrades]:  upgrades.md

[get-started]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html

[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/index.html

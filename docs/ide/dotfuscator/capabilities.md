---
title: Dotfuscator의 기능
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 보호, community edition, 난독 처리, .NET, 무료, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Visual Studio에 포함된 Dotfuscator Community 무료 복사본의 기능을 알아봅니다.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 019acd338ab49dd08255e3dc5d174cf2e371b71e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75918411"
---
# <a name="capabilities-of-dotfuscator"></a>Dotfuscator의 기능

이 페이지에서는 [업그레이드][upgrades]를 통해 사용 가능한 고급 옵션에 대한 몇 가지 참조와 함께 Dotfuscator Community의 기능을 중점적으로 설명합니다.

Dotfuscator Community는 .NET 애플리케이션용 ‘빌드 후’ 시스템입니다. 
Dotfuscator Community를 통해 Visual Studio 사용자는 [어셈블리를 난독 처리][obfuscation]하고 [활성 방어 대책][checks]을 애플리케이션에 삽입할 수 있습니다. Dotfuscator가 없다면 모두 원래 소스 코드에 액세스해야 하는 작업입니다.
Dotfuscator는 계층화된 보호 전략을 생성하는 다양한 방법으로 애플리케이션을 보호합니다.

Dotfuscator Community는 [UWP(유니버설 Windows 플랫폼)][uwp] 및 [Xamarin][xamarin]을 포함한 광범위한 .NET 어셈블리 및 애플리케이션 형식을 지원합니다.

## <a name="intellectual-property-protection"></a>지적 재산권 보호

애플리케이션의 디자인, 동작 및 구현은 IP(지적 재산권)의 형식입니다.
그러나 .NET용으로 만들어진 애플리케이션은 기본적으로 공개됩니다. [고급 메타데이터 및 중간 코드를 포함][assemblies]하므로 .NET 어셈블리를 쉽게 리버스 엔지니어링할 수 있습니다.

Dotfuscator Community에는 기본 [.NET 난독 처리][obfuscation]가 [이름 바꾸기][renaming] 형식으로 포함됩니다.
Dotfuscator를 통해 코드를 난독 처리하면 중요한 명명 정보가 더 이상 공개되지 않으므로 리버스 엔지이어링을 통해 소스 코드에 무단 액세스할 위험이 감소합니다.
난독 처리는 검사로부터 코드를 보호하려는 노력을 나타내며 IP를 거래 비밀로 법적으로 보호하도록 설정하는 중요한 단계입니다.

Dotfuscator Community의 다양한 [애플리케이션 무결성 보호 기능](#application-integrity-protection)은 리버스 엔지니어링을 추가로 방지합니다.
예를 들어 잘못된 행위자가 프로그램 논리를 이해하기 위해 디버거를 애플리케이션의 실행 중인 인스턴스에 연결하려고 시도할 수 있습니다.
Dotfuscator는 이 시도를 방지하기 위해 [디버그 방지 동작][debug]을 애플리케이션에 삽입할 수 있습니다.

## <a name="application-integrity-protection"></a>애플리케이션 무결성 보호

소스 코드 보호뿐 아니라 애플리케이션이 설계된 대로 사용되도록 하는 것도 중요합니다.
공격자는 라이선싱 정책을 우회하거나(즉, 소프트웨어 불법 복제), 애플리케이션에서 처리되는 중요한 데이터를 훔치거나 조작하거나, 애플리케이션의 동작을 변경하기 위해 애플리케이션을 하이재킹하려고 시도할 수 있습니다.

Dotfuscator Community는 [조작 방지][checks], [디버그 방지][tamper] 및 [루팅 방지 디바이스][debug] 대책을 포함하여 [애플리케이션 유효성 검사 코드][root]를 어셈블리에 삽입할 수 있습니다.
잘못된 애플리케이션 상태가 검색되면 유효성 검사 코드가 [애플리케이션 코드를 호출하여 상황을 적절한 방식으로 해결][check-app]할 수 있습니다.
또는 애플리케이션의 잘못된 사용을 처리하는 코드를 작성하지 않으려는 경우 소스 코드를 수정할 필요 없이 Dotfuscator에서 [응답][check-action] 동작을 삽입할 수도 있습니다.

이와 같은 방법의 대부분은 평가 및 평가판 소프트웨어를 위해 [수명 종료 기한][shelflife]을 적용하는 데 사용될 수도 있습니다.

## <a name="see-also"></a>참고 항목

[전체 Dotfuscator Community 사용자 가이드의 이 항목][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  /dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html

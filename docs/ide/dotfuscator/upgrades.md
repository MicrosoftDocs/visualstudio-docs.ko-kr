---
title: Dotfuscator Community 업그레이드
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, 보호, community edition, 난독 처리, .NET, 무료, Visual Studio 2019, Visual Studio 2017, Visual Studio, 업그레이드, 명령줄
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Visual Studio에 포함된 Dotfuscator Community 무료 복사본을 업그레이드하는 방법을 알아봅니다.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 08492340022f772beadca8061a216de69fafc8af
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596803"
---
# <a name="upgrade-dotfuscator-community"></a>Dotfuscator Community 업그레이드

Dotfuscator Community는 Microsoft Visual Studio를 사용하는 모든 개발자에게 즉시 다양한 애플리케이션 보호 및 강화 기능을 제공합니다.
그러나 Dotfuscator 버전을 업그레이드하는 사용자에게는 더 많은 기능이 제공됩니다.

## <a name="registering-dotfuscator-community"></a>Dotfuscator Community 등록

Dotfuscator Community의 등록된 사용자는 [명령줄 지원][cli]과 같은 추가 기능에 액세스할 수 있으므로 Dotfuscator Community를 자동화된 빌드 프로세스에 쉽게 통합할 수 있습니다. 등록하면 [난독 처리된 스택 추적 디코딩][decode-obfuscated]에 사용되는 기본 제공 도구에 대한 액세스 권한도 부여됩니다.

등록은 빠르고 간단하며 무료입니다.
Dotfuscator Community를 등록하려면 [전체 Dotfuscator Community 사용자 가이드의 지침][register-ce]을 참조하세요.

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Dotfuscator Community는 기본 수준의 보호를 제공하지만 ***PreEmptive Protection - Dotfuscator Professional***에는 다음과 같은 향상된 난독 처리 변환 및 보호 기능이 포함됩니다.

* *지적 재산권 보호*
  * Enhanced Overload Induction™ 및 임의 식별자 선택을 포함한 추가적인 이름 바꾸기 옵션.
  * [자동화된 코드 디컴파일을 방지하기 위한 변환][control-flow]을 포함하여 엔터프라이즈급 난독 변환에 액세스.
  * 디컴파일된 코드를 단순 검색하지 못하도록 [중요한 문자열을 가리는][string-encryption] 기능.
  * 권한이 없는 소프트웨어 누수의 원인을 파악할 수 있도록 [소유권 및 배포 문자열을 어셈블리에 신중하게 포함][watermarking]하는 기능.
  * 중요한 부분이 분리되지 않아 공격자가 코드 요소의 역할을 확인하기가 훨씬 더 어렵도록 [어셈블리 여러 개를 하나로 결합][linking]하는 기능.
  * 전달되는 중요한 코드의 양을 줄이도록 [자동으로 애플리케이션에서 사용되지 않는 코드를 제거][pruning]하는 기능.
* *애플리케이션 무결성 보호*
  * 추가적인 [애플리케이션 방어 동작][check-actions].
  * 애플리케이션의 수명 종료 기한 전에 경고 기간을 제공하는 기능.
  * 수명 종료 경고 기간 중에 또는 기한 후에 애플리케이션 코드를 알리는 기능.

Dotfuscator Professional은 산업 표준 [.NET Obfuscator][net-obfuscator]이고 지속적인 지원, 유지 관리 및 제품 업데이트가 필요한 엔터프라이즈 개발자에게 적합합니다.
또한 Dotfuscator Professional은 Visual Studio와 더 밀접하게 통합되고 상업적으로 사용이 허가됩니다.

Dotfuscator Professional의 고급 애플리케이션 보호 기능에 대한 자세한 내용을 보려면 PreEmptive Solutions의 [Dotfuscator 개요 페이지][product-about]를 방문해서 [Dotfuscator Community와 비교][product-compare]해 보세요.
[preemptive.com][eval]에서 전체 기능이 지원되는 평가판을 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[전체 Dotfuscator Community 사용자 가이드의 이 문서][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html

---
title: 보안
ms.date: 06/01/2018
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio], applications
- application design, securability
ms.assetid: 7d32c4cf-8bec-4307-a2a8-42f0ceddf3eb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87f06746901baaaf14f91032f8968a0d99fc20c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595451"
---
# <a name="secure-applications"></a>보안 애플리케이션

디자인에서 배포에 이르기까지 애플리케이션을 개발하는 모든 과정에 보안을 고려해야 합니다. Visual Studio를 최대한 안전하게 실행하여 시작합니다. [사용자 권한](../ide/user-permissions-and-visual-studio.md)을 참조하세요.

안전한 애플리케이션을 효과적으로 개발하려면 보안 개념 및 개발할 플랫폼의 보안 기능에 대한 기본적인 내용과 보안 코딩 기술을 이해하고 있어야 합니다.

## <a name="code-for-security"></a>보안에 대한 코드

보안 문제를 일으키는 대부분의 코딩 오류는 개발자가 사용자 입력에 대해 잘못 가정하거나 개발 중인 플랫폼을 완전히 이해하지 못하기 때문에 발생합니다.

- [보안 코딩 지침](/dotnet/standard/security/secure-coding-guidelines)에서는 보안 시스템에서 사용하기 위해 .NET 코드를 설계하는 여러 가지 방법에 대해 설명합니다.
- [C++에 대한 보안 모범 사례](/cpp/top/security-best-practices-for-cpp)에는 C++ 개발자를 위한 보안 도구 및 사례에 대한 정보가 들어 있습니다.

## <a name="build-for-security"></a>보안에 대해 빌드

보안 또한 빌드 프로세스에서 중요한 고려 사항입니다. 몇 가지 추가 단계로 배포된 앱의 보안을 향상하고 무단 리버스 엔지니어링, 스푸핑 또는 기타 공격을 방지할 수 있습니다.

- [Dotfuscator](dotfuscator/index.md)는 무료이며 .NET 어셈블리를 리버스 엔지니어링 및 무단 사용 (예: 무단 디버깅)으로부터 보호합니다.
- 소프트웨어 구성 요소를 고유하게 식별하고 이름 스푸핑을 방지하는 데 [강력한 이름 서명](managing-assembly-and-manifest-signing.md)을 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [.NET의 보안](/dotnet/standard/security/index)
- [Azure 보안](/azure/security/)
- [Windows 10 Mobile 보안 가이드](/windows/security/threat-protection/windows-10-mobile-security-guide)
- [Apache Cordova 플랫폼 보안 기능](/visualstudio/cross-platform/tools-for-cordova/security/best-practices?view=toolsforcordova-2017)
- [ASP.NET Core 보안](/aspnet/core/security/?view=aspnetcore-2.1)
- [Windows Forms 보안](/dotnet/framework/winforms/windows-forms-security)

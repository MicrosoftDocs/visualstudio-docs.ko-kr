---
title: Visual Studio에서 FIPS 140-2 승인 작업 모드 지원
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d06204fd1ef6ee2deb5eadc514af1ede8ae9bb6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180495"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Visual Studio에서 FIPS 140-2 승인 작업 모드 지원

Visual Studio 2019 [버전 16.4](/visualstudio/releases/2019/release-notes-v16.4/)부터 Windows, Azure 및 .NET에서 FIPS(Federal Information Processing Standard ) 발행물 140-2 승인 작업 모드를 지원합니다. 그리고 [버전 16.5](/visualstudio/releases/2019/release-notes-archive-v16.5)의 Visual Studio에서는 이제 [원격 Linux 시스템 대상의 C++ 애플리케이션](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)을 개발할 때 FIPS 140-2 승인 작업 모드를 지원합니다.

Visual Studio의 FIPS 140-2 승인 작업 모드를 구성하려면 [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48)을 설치한 다음 그룹 정책 설정인 **시스템 암호화: 암호화, 해시, 서명에 FIPS 호환 알고리즘 사용**을 사용하도록 지정합니다.

FIPS 140-2 승인 작업 모드와 이 모드를 사용하도록 설정하는 방법에 대한 자세한 내용은 [FIPS 140-2 Validation](/windows/security/threat-protection/fips-140-validation/)(FIPS 140-2 유효성 검사)을 참조하세요.

> [!NOTE]
> iOS 또는 Android와 같은 타사 플랫폼용 앱을 개발하는 데 사용하는 도구는 FIPS 규격 알고리즘을 사용하지 않을 수 있습니다. Visual Studio 및 사용자가 설치하는 확장에 포함된 타사 소프트웨어에서도 FIPS 규격 알고리즘을 사용하지 못할 수 있습니다. 그리고 [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) 솔루션 개발에서는 FIPS 140-2 승인 작업 모드가 지원되지 않습니다.

## <a name="next-steps"></a>다음 단계

Visual Studio 및 기타 Microsoft 제품 및 서비스의 FIPS 140-2 승인 작업 모드에 대해 자세히 알아보려면 다음 링크를 참조하세요.

- [Visual Studio: C++를 사용하여 FIPS 규격 보안 원격 Linux 개발 설정](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows: System cryptography and using FIPS-compliant algorithms for encryption, hashing, and signing](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)(시스템 암호화 및 암호화, 해시, 서명에 FIPS 규격 알고리즘 사용)
- [.NET Core: ](/dotnet/standard/security/fips-compliance/)(FIPS 호환성)

## <a name="see-also"></a>참조

[보안 애플리케이션](securing-applications.md)

---
title: WIP(Windows Information Protection)에서 제외
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b4eb454f641b5bef7273464d605fb194f650790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588566"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>WIP 제외 앱으로 Visual Studio 구성

[WIP(Windows Information Protection)](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)는 기업의 통제 범위를 벗어나는 이메일, 소셜 미디어 및 퍼블릭 클라우드와 같은 앱을 통해 엔터프라이즈 데이터가 누출되지 않도록 보호합니다. WIP는 환경이나 다른 앱을 변경할 필요 없이 기업 소유 디바이스와 개인 디바이스에서 실수로 데이터가 누출되지 않도록 보호할 수 있도록 합니다.

WIP용으로 *확인된* 앱은 엔터프라이즈 데이터가 보호되지 않은 네트워크 위치로 이동하는 것을 방지하고 개인 데이터를 암호화하지 못하게 해야 합니다. Visual Studio는 확인된 앱이 아니므로 제외하지 않는 한 WIP 지원 환경에서 작동하지 않습니다. WIP 지원 머신에서 Visual Studio가 작동하도록 하려면 이 문서의 단계를 수행합니다.

## <a name="configure-vs-as-a-wip-exempt-app"></a>WIP 제외 앱으로 VS 구성

WIP 제한에서 Visual Studio를 제외할 수 있지만 엔터프라이즈 데이터는 계속 사용할 수 있습니다. WIP 제외 앱은 IP 주소 또는 호스트 이름을 사용하여 엔터프라이즈 클라우드 리소스에 연결할 수 있습니다. 암호화가 적용되지 않고 앱에서 로컬 파일에 액세스할 수 있습니다.

WIP에서 Visual Studio를 제외하려면 [단계에 따라 데스크톱 앱을 제외합니다](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>WIP 제외 AppLocker 정책 파일 만들기

Visual Studio에는 여러 이진 파일이 포함되어 있으므로 [WIP 제외 AppLocker 정책 파일을 만듭니다](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker를 사용하면 폴더 내의 모든 파일에 대한 규칙을 자동으로 생성할 수 있습니다.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>AppCompat를 엔터프라이즈 클라우드 리소스 정책에 추가

Visual Studio가 네트워크에서 엔터프라이즈 데이터에 액세스할 수 있는 위치를 지정하려면 다음 [단계에 따라 보호된 앱이 엔터프라이즈 데이터를 찾고 전송할 수 있는 위치를 정의합니다](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Windows가 IP 주소를 통해 클라우드 리소스에 대한 연결을 차단하지 못하게 하려면 /\*AppCompat\*/ 문자열을 설정에 추가해야 합니다.

## <a name="see-also"></a>참고 항목

- [WIP를 사용한 앱 동작](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)

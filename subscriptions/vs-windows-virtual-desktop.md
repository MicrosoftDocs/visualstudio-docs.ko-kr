---
title: Visual Studio 구독의 Microsoft Windows Virtual Desktop 혜택 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 872c5746-5357-4764-949b-aa525a0adf1a
ms.date: 04/20/2020
ms.topic: conceptual
description: Visual Studio 구독을 통해 Microsoft Windows Virtual Desktop을 활용할 수 있는 방법을 알아봅니다.
ms.openlocfilehash: 865e18d7b8672520fcb771a1db56141fb6fd9f0a
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800608"
---
# <a name="access-windows-virtual-desktop-in-subscriptions"></a>구독에서 Windows Virtual Desktop 액세스 
이제 Visual Studio 구독자는 Microsoft Windows Virtual Desktop 서비스에 대해 Azure 개발/테스트 개별 크레딧을 사용할 수 있습니다.  
Windows Virtual Desktop은 클라우드에서 실행되는 포괄적인 데스크톱 및 앱 가상화 서비스입니다. 간소화된 관리, 다중 세션 Windows 10, 엔터프라이즈용 Microsoft 365에 대한 최적화, Remote Desktop Services(RDS) 환경에 대한 지원을 제공하는 유일한 VDI(가상 데스크톱 인프라)입니다. 몇 분 내에 Azure에서 Windows 데스크톱 및 앱을 배포하고 크기를 조정하며 기본 제공 보안 및 규정 준수 기능을 사용합니다.
Azure에서 Windows Virtual Desktop을 실행하면 다음과 같은 작업이 가능합니다.
- 확장 가능한 완전한 Windows 10을 제공하는 다중 세션 Windows 10 배포 설정
- 엔터프라이즈용 Office 365 앱을 가상화하고 다중 사용자 가상 시나리오에서 실행되도록 최적화
- Windows 7 가상 데스크톱에 무료 기간 연장 보안 업데이트 제공
- 기존 RDS(원격 데스크톱 서비스)와 Windows Server 데스크톱 및 앱을 컴퓨터로 가져오기
- 데스크톱 및 앱 가상화
- 통합된 관리 환경을 사용해 Windows 10, Windows Server, Windows 7 데스크톱 및 앱을 관리합니다. Windows Virtual Desktop에서 수행할 수 있는 작업에 대한 자세한 내용은 [소개 비디오](https://docs.microsoft.com/azure/virtual-desktop/overview)를 시청하세요.

## <a name="use-windows-virtual-desktop-with-azure"></a>Azure와 함께 Windows Virtual Desktop 사용 
이제 Visual Studio 구독자는 몇 가지 방법으로 Azure 구독을 사용해 Windows Virtual Desktop 서비스 요금을 지불할 수 있습니다.
- [Azure DevTest 개별 크레딧](vs-azure.md).  구독의 일부로 Azure DevTest 개별 크레딧을 받는 구독자는 이러한 크레딧을 사용하여 Windows Virtual Desktop 서비스 요금을 지불할 수 있습니다.  월별 크레딧의 양은 구독 수준에 따라 달라집니다.
- [Azure DevTest 종량제 구독](vs-azure-payg.md).  Azure 구독을 만들고 결제 방법을 연결하여 Windows Virtual Desktop 사용 요금을 원활하게 지불할 수 있습니다. 
- [Azure 기업계약 DevTest 제안](azure-ea-devtest.md).  이 제안에서는 기업계약이 있는 구독자가 Azure를 사용하여 Windows Virtual Desktop 요금을 할인된 가격으로 지불할 수 있습니다. 

## <a name="requirements"></a>요구 사항
Windows Virtual Desktop에는 VM이 가입될 Azure AD(Azure Active Directory)가 필요합니다.  그리고 사용자는 이 Azure AD의 멤버여야 합니다.  Azure AD를 구현하는 데는 다음 두 가지 옵션이 있습니다.
- Azure AD 디렉터리 서비스.  대부분의 사용자의 경우 이 옵션이 더 구현하기 쉽습니다.
- 도메인 컨트롤러 승격을 실행하는 가상 머신.  이 옵션 사용하려면 더 많은 작업을 설정해야 하지만 대부분의 사용자가 부담하는 운영 비용은 더 낮습니다.
Windows Virtual Desktop을 사용하기 위한 필수 조건의 전체 목록을 보려면 Windows Virtual Desktop [개요 페이지](https://docs.microsoft.com/azure/virtual-desktop/overview#requirements)를 참조하세요. 

## <a name="get-started"></a>시작 
모든 필수 조건이 충족되면 구현을 준비하기 위해 몇 가지 작업을 완료합니다.  다음 자습서를 확인하여 시작하세요.
- [Windows Virtual Desktop 테넌트 만들기](https://docs.microsoft.com/azure/virtual-desktop/virtual-desktop-fall-2019/tenant-setup-azure-active-directory)
- Azure Portal을 사용하여 [호스트 풀 만들기](https://docs.microsoft.com/azure/virtual-desktop/create-host-pools-azure-marketplace)
- Windows Virtual Desktop에 대한 [앱 그룹 관리](https://docs.microsoft.com/azure/virtual-desktop/manage-app-groups)

## <a name="eligibility"></a>자격
| 구독 수준                                                 |     채널                                            | 이점                                                          | 갱신 가능?    |
|--------------------------------------------------------------------|---------------------------------------------------------|------------------------------------------------------------------|---------------|
| Visual Studio Enterprise(Standard)   | VL, Azure, 일반 정품, | 사용 가능|  예          |
| GitHub Enterprise가 포함된 Visual Studio Enterprise  | VL | 사용 가능|  예          |
| Visual Studio Professional(표준) | VL, Azure, 일반 정품                                       | 사용 가능                                                             |  예             |
| GitHub Enterprise가 포함된 Visual Studio Professional | VL                                       | 사용 가능                                        |  예           |
| Visual Studio Test Professional(표준)                         | VL, 일반 정품                                              | 사용 가능|  예          |
| MSDN 플랫폼(표준)                                          | VL, 일반 정품                                              | 사용 가능                                         |  예          |
| Visual Studio Enterprise(Standard)  | NFR<sup>1</sup> |사용할 수 없음  | N/A |
| Visual Studio Enterprise, Visual Studio Professional(월간 클라우드) | Azure | 사용할 수 없음 | N/A |

<sup>1</sup>  포함:  ‘NFR(전매금지), FTE, MVP(Most Valuable Professional), RD(Regional Director), MPN(Microsoft 파트너 네트워크), VSIP(Visual Studio Industry Partner), Microsoft Certified Trainer, BizSpark, Imagine’

> [!NOTE]
> Microsoft는 더 이상 Visual Studio Professional 연간 구독 및 클라우드 구독에 Visual Studio Enterprise 연간 구독을 제공하지 않습니다. 기존 고객 환경 및 해당 구독의 갱신, 증가, 감소 또는 취소 기능은 변경되지 않습니다. 새 고객은 [https://visualstudio.microsoft.com/vs/pricing/](https://visualstudio.microsoft.com/vs/pricing/)으로 이동하여 Visual Studio를 구입하기 위한 다양한 옵션을 살펴보세요.

어떤 구독을 사용하고 있는지 확실하지 않나요?  자신의 이메일 주소에 할당된 모든 구독을 보려면 [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions?wt.mc_id=o~msft~docs)에 연결합니다. 일부 구독이 표시되지 않으면 하나 이상이 다른 전자 메일 주소에 할당되어 있을 수 있습니다.  해당 구독을 보려면 해당 전자 메일 주소로 로그인해야 합니다.

## <a name="see-also"></a>참조
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Windows Virtual Desktop 설명서](https://docs.microsoft.com/azure/virtual-desktop/)

## <a name="next-steps"></a>다음 단계
-   Visual Studio 구독을 구매해야 하는 경우 다음을 확인하세요.
     - Microsoft Store를 통한 [소매 구매 가격](https://visualstudio.microsoft.com/vs/pricing/)
     - [볼륨 라이선싱 프로그램](https://www.microsoft.com/licensing/default)
-   [Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/overview)에 대한 정보 

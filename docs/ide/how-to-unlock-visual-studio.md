---
title: 평가판 버전 확장 또는 라이선스 업데이트
description: Visual studio의 무료 평가판을 확장하고, 온라인 구독 또는 제품 키를 사용하여 Visual Studio의 잠금을 해제하고, 부실한 또는 만료된 라이선스를 업데이트하는 방법에 대해 알아봅니다.
ms.date: 12/18/2019
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 8e11d77a94c7c1d3d7b038ecea1a6c61646e371f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027574"
---
# <a name="extend-a-trial-version-or-update-a-license"></a>평가판 버전 확장 또는 라이선스 업데이트

[Visual Studio Professional 또는 Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/compare/)의 무료 평가판을 30일 동안 평가할 수 있습니다. 그리고 로그인하면 평가 기간을 90일로 연장할 수 있습니다. (Visual Studio Community는 평가 기간 없이 무료로 제공됩니다. 그러나 [라이선스를 최신](#update-a-stale-license)으로 유지하려면 정기적으로 [로그인](signing-in-to-visual-studio.md)해야 합니다.)

평가 기간이 종료한 후 Visual Studio를 계속 사용하려면 [온라인 구독](#use-an-online-subscription) 또는 [제품 키](#enter-a-product-key)를 사용하여 잠금을 해제합니다.

## <a name="use-an-online-subscription"></a>온라인 구독 사용

1. IDE의 오른쪽 위에 있는 **로그인** 단추를 선택하거나 **파일** > **계정 설정**을 선택하여 **계정 설정** 대화 상자를 열고 **로그인** 단추를 선택합니다.

1. Microsoft 계정이나 회사 또는 학교 계정에 대한 자격 증명을 입력합니다. Visual Studio에서 해당 계정과 연결된 Visual Studio 구독 또는 Azure DevOps 조직을 찾습니다.

> [!IMPORTANT]
> **팀 탐색기** 도구 창에서 Azure DevOps 조직에 연결하면 Visual Studio에서 연결된 온라인 구독을 자동으로 찾습니다. Azure DevOps 조직에 연결하면 Microsoft 계정 및 회사 또는 학교 계정을 사용하여 로그인할 수 있습니다. 해당 사용자 계정에 대한 온라인 구독이 있으면 Visual Studio에서 IDE를 자동으로 잠금 해제합니다.

Visual Studio 구독 및 사용 방법에 대한 자세한 내용은 [구독 지원 FAQ](https://visualstudio.microsoft.com/subscriptions/support/) 페이지를 참조하세요.

## <a name="enter-a-product-key"></a>제품 키 입력

1. **파일** > **계정 설정**을 선택하여 **계정 설정** 대화 상자를 열고 **제품 키가 있는 라이선스** 링크를 선택합니다.

1. 제공된 입력란에 제품 키를 입력합니다.

> [!TIP]
> 시험판 버전의 Visual Studio에는 제품 키가 없습니다. 시험판 버전을 사용하려면 IDE에 로그인해야 합니다.

Visual Studio용 Visual Studio 제품 키 및 이를 가져오는 방법에 대한 자세한 내용은 [Visual Studio 구독에서 제품 키 사용](/visualstudio/subscriptions/product-keys) 페이지를 참조하세요.

## <a name="update-a-stale-license"></a>부실 라이선스 업데이트

Visual Studio에 "라이선스가 만료될 예정이므로 업데이트해야 합니다."라는 메시지가 표시될 수 있습니다.

![Visual Studio 부실 라이선스 메시지](../ide/media/vs2017_stale-license.png)

이 메시지는 구독이 여전히 유효할 수 있지만 Visual Studio에서 구독을 최신 상태로 유지하는 데 사용하는 라이선스 토큰이 새로 고쳐지지 않았음을 나타냅니다. Visual Studio는 다음과 같은 이유로 라이선스가 부실함을 보고합니다.

* Visual Studio를 사용하지 않았거나 오랜 시간 동안 인터넷에 연결하지 않았습니다.
* Visual Studio에서 로그아웃했습니다.

라이선스 토큰이 부실해지기 전에 Visual Studio에서 먼저 자격 증명을 다시 입력하라는 경고 메시지가 표시됩니다.

자격 증명을 다시 입력하지 않으면 토큰이 부실해지고 **계정 설정** 대화 상자에 토큰이 만료될 때까지 남은 기간이 표시됩니다. 토큰이 만료된 후에는 계정의 자격 증명을 다시 입력해야 Visual Studio를 계속 사용할 수 있습니다.

> [!Important]
> 인터넷 연결이 제한되거나 인터넷에 연결되지 않은 환경에서 오랫동안 Visual Studio를 사용하는 경우 작업이 중단되지 않도록 제품 키를 사용하여 Visual Studio의 잠금을 해제해야 합니다.

## <a name="update-an-expired-license"></a>만료된 라이선스 업데이트

구독이 만료되어 Visual Studio 액세스 권한이 더 이상 없으면 사용자 구독을 갱신하거나 구독이 있는 다른 계정을 추가해야 합니다. 사용 중인 라이선스에 대한 자세한 정보를 보려면 **파일** > **계정 설정**으로 이동하고 대화 상자의 오른쪽에 있는 라이선스 정보를 살펴봅니다. 다른 계정에 연결된 다른 구독이 있는 경우 **계정 추가** 링크를 선택하여 대화 상자의 왼쪽에 있는 **모든 계정** 목록에 해당 계정을 추가합니다.

## <a name="get-support"></a>지원 받기

때로는 무엇인가 잘못됩니다. 문제가 발생하는 경우 몇 가지 지원 옵션은 다음과 같습니다.

* [문제 보고](how-to-report-a-problem-with-visual-studio.md) 도구를 사용하여 제품 문제를 보고합니다.
* 구독, 계정 및 요금 청구 관련 질문에 대한 답변은 [구독 지원 FAQ](https://visualstudio.microsoft.com/subscriptions/support/)를 확인하세요.

## <a name="see-also"></a>참고 항목

* [Visual Studio에 로그인](../ide/signing-in-to-visual-studio.md)
* [Visual Studio 버전 비교](https://visualstudio.microsoft.com/vs/compare/)
* [Visual Studio 구독에 대한 자세한 정보](/visualstudio/subscriptions/)

---
title: ClickOnce 배포 API를 사용하여 자동 앱 업데이트
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9300fbf8b348b1016d36d414d17a66c45f6494b9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444619"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>방법: ClickOnce 배포 API를 사용하여 프로그래밍 방식으로 애플리케이션 업데이트 확인
ClickOnce는 응용 프로그램이 배포된 후 업데이트하는 두 가지 방법을 제공합니다. 첫 번째 방법에서는 ClickOnce 배포를 구성하여 특정 간격으로 업데이트가 자동으로 확인됩니다. 두 번째 메서드에서는 클래스를 <xref:System.Deployment.Application.ApplicationDeployment> 사용 하 여 사용자 요청 등 이벤트에 따라 업데이트를 확인 하는 코드를 작성할 수 있습니다.

 다음 절차에는 프로그래밍 방식 업데이트를 수행하기 위한 몇 가지 코드가 표시되며 프로그래밍 방식의 업데이트 검사를 사용하도록 ClickOnce 배포를 구성하는 방법도 설명합니다.

 ClickOnce 응용 프로그램을 프로그래밍 방식으로 업데이트하려면 업데이트 위치를 지정해야 합니다. 이를 배포 공급자라고도 합니다. 이 속성 설정에 대한 자세한 내용은 [클릭Once 업데이트 전략 선택을](../deployment/choosing-a-clickonce-update-strategy.md)참조하십시오.

> [!NOTE]
> 아래에 설명된 기술을 사용하여 한 위치에서 응용 프로그램을 배포하고 다른 위치에서 업데이트할 수도 있습니다. 자세한 내용은 [배포 업데이트의 대체 위치 지정 방법:](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)을 참조하십시오.

### <a name="to-check-for-updates-programmatically"></a>프로그래밍 방식으로 업데이트를 확인하려면

1. 기본 명령줄 또는 시각적 도구를 사용하여 새 Windows Forms 응용 프로그램을 만듭니다.

2. 사용자가 업데이트를 확인하기 위해 선택할 단추, 메뉴 항목 또는 기타 사용자 인터페이스 항목을 만듭니다. 해당 항목의 이벤트 처리기에서 다음 메서드를 호출하여 업데이트를 확인하고 설치합니다.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. 응용 프로그램을 컴파일합니다.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Mage.exe를 사용하여 프로그래밍 방식으로 업데이트를 확인하는 응용 프로그램을 배포합니다.

- 연습에서 설명한 대로 Mage.exe를 사용하여 응용 프로그램을 배포하는 방법에 대한 지침을 [따르십시오: ClickOnce 응용 프로그램을 수동으로 배포합니다.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) 배포 매니페스트를 생성하기 위해 Mage.exe를 호출할 때 `providerUrl`명령줄 스위치를 사용하고 ClickOnce가 업데이트를 확인해야 하는 URL을 지정해야 합니다. 예를 들어 `http://www.adatum.com/MyApp`응용 프로그램이 에서 업데이트되는 경우 배포 매니페스트를 생성하는 호출은 다음과 같을 수 있습니다.

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>MageUI.exe를 사용하여 프로그래밍 방식으로 업데이트를 확인하는 응용 프로그램을 배포합니다.

- 연습에서 설명한 대로 Mage.exe를 사용하여 응용 프로그램을 배포하는 방법에 대한 지침을 [따르십시오: ClickOnce 응용 프로그램을 수동으로 배포합니다.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) 배포 **옵션** 탭에서 **시작 위치** 필드를 응용 프로그램 매니페스트ClickOnce업데이트에 대해 확인합니다. 업데이트 **옵션** 탭에서 **이 응용 프로그램을 선택하여 업데이트 확인란을 선택합니다.**

## <a name="net-framework-security"></a>.NET Framework 보안
 응용 프로그램에 프로그래밍 방식 업데이트를 사용할 수 있는 완전 신뢰 권한이 있어야 합니다.

## <a name="see-also"></a>참조
- [방법: 배포 업데이트를 위한 대체 위치 지정](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
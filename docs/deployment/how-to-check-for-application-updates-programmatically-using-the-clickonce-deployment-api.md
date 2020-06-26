---
title: ClickOnce 배포 API를 사용 하 여 자동 앱 업데이트
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 6aee738d972b7c6e8c857ae87bb25758d871fe28
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382577"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>방법: ClickOnce 배포 API를 사용하여 프로그래밍 방식으로 애플리케이션 업데이트 확인
ClickOnce는 응용 프로그램이 배포 된 후 응용 프로그램을 업데이트 하는 두 가지 방법을 제공 합니다. 첫 번째 방법에서는 특정 간격으로 업데이트를 자동으로 확인 하도록 ClickOnce 배포를 구성할 수 있습니다. 두 번째 메서드에서는 클래스를 사용 하 여 <xref:System.Deployment.Application.ApplicationDeployment> 사용자 요청과 같은 이벤트를 기반으로 업데이트를 확인 하는 코드를 작성할 수 있습니다.

 다음 절차에서는 프로그래밍 방식 업데이트를 수행 하는 몇 가지 코드를 보여 주고 프로그래밍 방식 업데이트 검사를 사용 하도록 ClickOnce 배포를 구성 하는 방법을 설명 합니다.

 ClickOnce 응용 프로그램을 프로그래밍 방식으로 업데이트 하려면 업데이트 위치를 지정 해야 합니다. 이를 배포 공급자 라고도 합니다. 이 속성을 설정 하는 방법에 대 한 자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조 하세요.

> [!NOTE]
> 또한 아래에 설명 된 기술을 사용 하 여 한 위치에서 응용 프로그램을 배포 하 고 다른 위치에서 업데이트할 수 있습니다. 자세한 내용은 [방법: 배포 업데이트를 위한 대체 위치 지정](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)을 참조 하세요.

### <a name="to-check-for-updates-programmatically"></a>프로그래밍 방식으로 업데이트를 확인 하려면

1. 선호 하는 명령줄 또는 시각적 도구를 사용 하 여 새 Windows Forms 응용 프로그램을 만듭니다.

2. 사용자가 업데이트를 확인 하기 위해 선택 하려는 단추, 메뉴 항목 또는 기타 사용자 인터페이스 항목을 만듭니다. 해당 항목의 이벤트 처리기에서 다음 메서드를 호출 하 여 업데이트를 확인 하 고 설치 합니다.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. 응용 프로그램을 컴파일합니다.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Mage.exe를 사용 하 여 프로그래밍 방식으로 업데이트를 확인 하는 응용 프로그램 배포

- [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)에 설명 된 대로 Mage.exe를 사용 하 여 응용 프로그램을 배포 하기 위한 지침을 따르세요. Mage.exe를 호출 하 여 배포 매니페스트를 생성 하는 경우 명령줄 스위치를 사용 하 `providerUrl` 고 ClickOnce에서 업데이트를 확인 해야 하는 URL을 지정 해야 합니다. 예를 들어 응용 프로그램이에서 업데이트 되는 경우 `http://www.adatum.com/MyApp` 배포 매니페스트를 생성 하는 호출은 다음과 같이 표시 될 수 있습니다.

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>MageUI.exe를 사용 하 여 프로그래밍 방식으로 업데이트를 확인 하는 응용 프로그램 배포

- [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)에 설명 된 대로 Mage.exe를 사용 하 여 응용 프로그램을 배포 하기 위한 지침을 따르세요. **배포 옵션** 탭에서 **시작 위치** 필드를 ClickOnce가 업데이트를 확인 해야 하는 응용 프로그램 매니페스트로 설정 합니다. **업데이트 옵션** 탭에서 **이 응용 프로그램이 업데이트를 확인 해야 함** 확인란의 선택을 취소 합니다.

## <a name="net-framework-security"></a>.NET Framework 보안
 응용 프로그램에는 프로그래밍 방식 업데이트를 사용할 수 있는 완전 신뢰 권한이 있어야 합니다.

## <a name="see-also"></a>추가 정보
- [방법: 배포 업데이트를 위한 대체 위치 지정](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
---
title: 방법-배포 업데이트에 대 한 대체 위치 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c71586c43fa1a71205d61ae21fb94c267daf497d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85381914"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>방법: 배포 업데이트를 위한 대체 위치 지정
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]처음에 CD 또는 파일 공유에서 응용 프로그램을 설치할 수 있지만 응용 프로그램은 웹에서 정기적으로 업데이트를 확인 해야 합니다. 초기 설치 후 응용 프로그램이 웹에서 자동으로 업데이트 될 수 있도록 배포 매니페스트에서 업데이트에 대 한 대체 위치를 지정할 수 있습니다.

> [!NOTE]
> 이 기능을 사용 하려면 응용 프로그램을 로컬로 설치 하도록 구성 해야 합니다. 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)를 참조 하세요. 또한 네트워크에서 응용 프로그램을 설치 하는 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 대체 위치를 설정 하면에서 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 초기 설치 및 모든 후속 업데이트에 대해 해당 위치를 사용 하 게 됩니다. 응용 프로그램을 로컬로 설치 하는 경우 (예: CD에서) 초기 설치는 원본 미디어를 사용 하 여 수행 되 고 모든 후속 업데이트는 대체 위치를 사용 합니다.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>MageUI.exe (Windows Forms 기반 유틸리티)를 사용 하 여 업데이트를 위한 대체 위치 지정

1. .NET Framework 명령 프롬프트를 열고 다음을 입력 합니다.

     **mageui.exe**

2. **파일** 메뉴에서 **열기** 를 선택 하 여 응용 프로그램의 배포 매니페스트를 엽니다.

3. **배포 옵션** 탭을 선택합니다.

4. **시작 위치**라는 텍스트 상자에 응용 프로그램 업데이트에 대 한 배포 매니페스트를 포함 하는 디렉터리에 대 한 URL을 입력 합니다.

5. 배포 매니페스트를 저장 합니다.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Mage.exe를 사용 하 여 업데이트를 위한 대체 위치 지정

1. .NET Framework 명령 프롬프트를 엽니다.

2. 다음 명령을 사용 하 여 업데이트 위치를 설정 합니다. 이 예제에서 *HelloWorld.exe* 는 응용 프로그램 매니페스트에 대 한 경로입니다 .이 경로에는 항상. 응용 프로그램 확장명이 있으며 응용 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `http://adatum.com/Update/Path` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 프로그램 업데이트를 확인 하는 URL입니다.

    **Mage-HelloWorld.exe 업데이트-ProviderUrl http: \/ /adatum.com/Update/Path**

3. 파일을 저장합니다.

   > [!NOTE]
   > 이제 *Mage.exe*를 사용 하 여 파일에 다시 서명 해야 합니다. 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)를 참조 하세요.

## <a name="net-framework-security"></a>.NET Framework 보안
 CD와 같은 오프 라인 미디어에서 응용 프로그램을 설치 하 고 컴퓨터가 온라인 상태 이면는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 먼저 배포 매니페스트의 태그에 지정 된 URL을 확인 `<deploymentProvider>` 하 여 업데이트 위치에 최신 버전의 응용 프로그램이 포함 되어 있는지 확인 합니다. 이 경우에서 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 초기 설치 디렉터리 대신 응용 프로그램을 직접 설치 하 고 CLR (공용 언어 런타임)에서를 사용 하 여 응용 프로그램의 신뢰 수준을 결정 합니다 `<deploymentProvider>` . 컴퓨터가 오프 라인 이거나 연결할 수 없는 경우는 `<deploymentProvider>` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] cd에서 설치 하 고, CLR은 설치 지점에 따라 트러스트를 부여 합니다. CD 설치의 경우 응용 프로그램이 완전 신뢰를 수신 합니다. 모든 후속 업데이트는 해당 신뢰 수준을 상속 합니다.

 를 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 사용 하는 모든 응용 프로그램은 응용 프로그램 `<deploymentProvider>` 매니페스트에서 필요한 사용 권한을 명시적으로 선언 해야 합니다. 따라서 응용 프로그램은 서로 다른 컴퓨터에서 서로 다른 신뢰 수준을 수신 하지 않습니다.

## <a name="see-also"></a>추가 정보
- [연습: 수동으로 ClickOnce 애플리케이션 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)
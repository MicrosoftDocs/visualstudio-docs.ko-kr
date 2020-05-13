---
title: '방법: 배포 업데이트의 대체 위치 지정 | 마이크로 소프트 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037222"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>방법: 배포 업데이트를 위한 대체 위치 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

처음에는 CD [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 또는 파일 공유에서 응용 프로그램을 설치할 수 있지만 응용 프로그램은 웹에서 정기적으로 업데이트되는지 확인해야 합니다. 배포 매니페스트에서 업데이트에 대한 대체 위치를 지정하여 응용 프로그램이 초기 설치 후 웹에서 자체적으로 업데이트할 수 있도록 할 수 있습니다.  
  
> [!NOTE]
> 이 기능을 사용하려면 응용 프로그램을 로컬로 설치하도록 구성해야 합니다. 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동으로 배포를](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)참조하십시오. 또한 네트워크에서 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 설치하는 경우 대체 위치를 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 설정하면 초기 설치 및 모든 후속 업데이트모두에 해당 위치를 사용합니다. 응용 프로그램을 로컬로 설치하는 경우(예: CD에서) 초기 설치는 원래 미디어를 사용하여 수행되며 이후의 모든 업데이트는 대체 위치를 사용합니다.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>MageUI.exe(Windows 양식 기반 유틸리티)를 사용하여 업데이트의 대체 위치 지정  
  
1. .NET Framework 명령 프롬프트를 열고 다음을 입력합니다.  
  
     **mageui.exe**  
  
2. **파일** 메뉴에서 **열기를** 선택하여 응용 프로그램의 배포 매니페스트를 엽니다.  
  
3. **배포 옵션** 탭을 선택합니다.  
  
4. **시작 위치라는**텍스트 상자에 응용 프로그램 업데이트에 대한 배포 매니페스트를 포함하는 디렉터리에 대한 URL을 입력합니다.  
  
5. 배포 매니페스트를 저장합니다.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Mage.exe를 사용하여 업데이트의 대체 위치 지정  
  
1. .NET Framework 명령 프롬프트를 엽니다.  
  
2. 다음 명령을 사용하여 업데이트 위치를 설정합니다. 이 예제에서 **HelloWorld.exe.application은** 항상 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .application 확장이 있고 응용 프로그램 `http://adatum.com/Update/Path` 업데이트를 확인하는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] URL인 응용 프로그램 매니페스트에 대한 경로입니다.  
  
     **매지 - 업데이트 HelloWorld.exe.application -providerUrl http:\//adatum.com/Update/Path**  
  
3. 파일을 저장합니다.  
  
    > [!NOTE]
    > 이제 Mage.exe를 사용하여 파일에 다시 서명해야 합니다. 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동으로 배포를](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)참조하십시오.  
  
## <a name="net-framework-security"></a>.NET Framework 보안  
 CD와 같은 오프라인 매체에서 응용 프로그램을 설치하고 컴퓨터가 온라인 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 상태인 경우 먼저 `<deploymentProvider>` 배포 매니페스트의 태그에 지정된 URL을 확인하여 업데이트 위치에 최신 버전의 응용 프로그램이 포함되어 있는지 확인합니다. 이 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 초기 설치 디렉터리 대신 거기에서 직접 응용 프로그램을 설치하고 공통 언어 런타임(CLR)은 을 사용하여 `<deploymentProvider>`응용 프로그램의 신뢰 수준을 결정합니다. 컴퓨터가 오프라인 상태이거나 `<deploymentProvider>` 연결할 수 없는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 경우 CD에서 설치하고 CLR은 설치 지점을 기반으로 신뢰를 부여합니다. 즉, CD 설치의 경우 응용 프로그램이 완전 신뢰를 받습니다. 이후의 모든 업데이트는 해당 신뢰 수준을 상속합니다.  
  
 응용 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 프로그램이 다른 `<deploymentProvider>` 컴퓨터에서 서로 다른 수준의 신뢰를 받지 않도록 사용하는 모든 응용 프로그램은 응용 프로그램 매니페스트에 필요한 권한을 명시적으로 선언해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: ClickOnce 응용 프로그램 수동으로 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [클릭원스 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)   
 [클릭한 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)

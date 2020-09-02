---
title: '방법: ClickOnce 응용 프로그램의 URL 활성화 사용 안 함 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75a98706858323693ec01ec3c3420a6d2d25ffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697222"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>방법: ClickOnce 애플리케이션의 URL 활성화를 사용하지 않도록 설정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일반적으로 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션은 웹 서버에서 설치된 후 바로 자동으로 시작됩니다. 보안상 이유로 이 동작을 사용하지 않도록 결정하고 사용자에게 **시작** 메뉴에서 애플리케이션을 시작하도록 알릴 수 있습니다. 다음 절차에서는 URL 활성화를 사용하지 않도록 설정하는 방법에 대해 설명합니다.  
  
 이 방법은 웹 서버에서 사용자 컴퓨터에 설치된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 대해서만 사용할 수 있습니다. URL을 사용하여 시작할 수 있는 온라인 전용 애플리케이션에는 사용할 수 없습니다. 온라인 전용 애플리케이션 및 설치된 애플리케이션 간 차이점에 대한 자세한 내용은 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)을 참조하세요.  
  
 이 절차에서는 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] 도구 MageUI.exe를 사용합니다. 이 도구에 대 한 자세한 내용은 참조 하세요. [MageUI.exe (매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)합니다. 또한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]을(를) 사용하여 이 작업을 수행할 수 있습니다.  
  
## <a name="procedure"></a>프로시저  
  
#### <a name="to-disable-url-activation-for-your-application"></a>애플리케이션의 URL 활성화를 사용하지 않도록 설정하려면  
  
1. MageUI.exe에서 배포 매니페스트를 엽니다. 아직 만들지 않은 경우 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)의 단계를 따릅니다.  
  
2. **배포 옵션** 탭을 선택합니다.  
  
3. **설치 후 자동으로 애플리케이션 실행** 확인란의 선택을 취소합니다.  
  
4. 매니페스트를 저장하고 여기에 서명합니다.  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)

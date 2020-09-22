---
title: '방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18c8dd4d0bc79ac2f3af44b8b5f8dd6faacb9f45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841602"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>방법: ClickOnce 애플리케이션을 사용하여 필수 구성 요소 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모든 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 실행 하려면 컴퓨터에 올바른 버전의 .NET Framework가 설치 되어 있어야 합니다. 많은 응용 프로그램에는 다른 필수 구성 요소가 있습니다. 응용 프로그램을 게시할 때 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램과 함께 패키지할 필수 구성 요소 집합을 선택할 수 있습니다. 설치 시 각 필수 구성 요소가 이미 있는지 여부를 확인 하는 검사가 수행 됩니다. 그렇지 않으면 응용 프로그램을 설치 하기 전에 설치 됩니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
 필수 구성 요소를 패키지 하 고 게시 하는 대신 구성 요소에 대 한 다운로드 위치를 지정할 수도 있습니다. 예를 들어, 게시 하는 모든 응용 프로그램에 대 한 필수 구성 요소를 포함 하는 대신, 모든 필수 구성 요소에 대 한 설치 관리자를 포함 하는 중앙 집중식 파일 공유 또는 웹 위치를 사용할 수 있습니다. 설치 시 구성 요소는 해당 위치에서 다운로드 되 고 설치 됩니다.  
  
> [!IMPORTANT]
> 첫 번째 응용 프로그램을 게시 하기 전에 개발 컴퓨터에 필수 구성 요소 설치 관리자 패키지를 추가 해야 합니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . 자세한 내용은 [방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 포함](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md)을 참조 하세요.  
  
 필수 구성 요소는 **프로젝트 디자이너**의 **게시** 창에서 액세스할 수 있는 **필수 구성 요소** 대화 상자에서 관리 됩니다.  
  
> [!NOTE]
> 미리 결정 된 필수 구성 요소 목록 외에도 목록에 사용자 고유의 구성 요소를 추가할 수 있습니다. 자세한 내용은 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)를 참조 하세요.  
  
### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>ClickOnce 응용 프로그램과 함께 설치 하기 위한 필수 구성 요소를 지정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴의 **속성**을 클릭 합니다.  
  
2. **게시** 창을 선택 합니다.  
  
3. 필수 구성 **요소 단추를** 클릭 하 여 **필수 구성 요소** 대화 상자를 엽니다.  
  
4. **필수 구성 요소** 대화 상자에서 **필수 구성 요소를 설치하기 위한 설치 프로그램 만들기** 확인란이 선택되어 있는지 확인합니다.  
  
5. **필수** 구성 요소 목록에서 설치할 구성 요소를 확인 한 다음 **확인**을 클릭 합니다.  
  
     선택한 구성 요소는 응용 프로그램과 함께 패키지 되 고 게시 됩니다.  
  
### <a name="to-specify-a-different-download-location-for-prerequisites"></a>필수 구성 요소에 대해 다른 다운로드 위치를 지정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴의 **속성**을 클릭 합니다.  
  
2. **게시** 창을 선택 합니다.  
  
3. 필수 구성 **요소 단추를** 클릭 하 여 **필수 구성 요소** 대화 상자를 엽니다.  
  
4. **필수 구성 요소** 대화 상자에서 **필수 구성 요소를 설치하기 위한 설치 프로그램 만들기** 확인란이 선택되어 있는지 확인합니다.  
  
5. **필수 조건에 대 한 설치 위치 지정** 섹션의 **다음 위치에서 필수 구성 요소 다운로드**를 선택 합니다.  
  
6. 드롭다운 목록에서 위치를 선택 하거나 URL, 파일 경로 또는 FTP 위치를 입력 한 다음 확인을 클릭 **합니다.**  
  
    > [!NOTE]
    > 지정 된 구성 요소의 설치 관리자가 지정 된 위치에 있는지 확인 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

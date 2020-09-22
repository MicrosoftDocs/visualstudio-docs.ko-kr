---
title: '방법: ClickOnce 보안 설정 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b104a7a0451da7f772077d2f566b36b9f601c17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841622"
---
# <a name="how-to-enable-clickonce-security-settings"></a>How to: Enable ClickOnce Security Settings
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 응용 프로그램에 대 한 코드 액세스 보안은 응용 프로그램을 게시 하기 위해 사용 하도록 설정 되어야 합니다. 이 작업은 게시 마법사를 사용 하 여 응용 프로그램을 게시할 때 자동으로 수행 됩니다.  
  
 응용 프로그램을 빌드하거나 디버그할 때 코드 액세스 보안을 사용 하도록 설정 하면 성능에 영향을 줄 수 있습니다. 이러한 경우에는 보안 설정을 일시적으로 사용 하지 않도록 설정할 수 있습니다.  
  
 **프로젝트 디자이너**의 **보안** 페이지에서 ClickOnce 보안 설정을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.  
  
### <a name="to-enable-clickonce-security-settings"></a>ClickOnce 보안 설정을 사용 하도록 설정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **보안** 탭을 클릭합니다.  
  
3. **ClickOnce 보안 설정 사용** 확인란을 선택합니다.  
  
     이제 보안 페이지에서 응용 프로그램에 대 한 보안 설정을 사용자 지정할 수 있습니다.  
  
    > [!NOTE]
    > 이 확인란은 **게시** 마법사를 사용 하 여 응용 프로그램을 게시할 때마다 자동으로 선택 됩니다.  
  
### <a name="to-disable-clickonce-security-settings"></a>ClickOnce 보안 설정을 사용 하지 않도록 설정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **보안** 탭을 클릭합니다.  
  
3. **ClickOnce 보안 설정 사용** 확인란의 선택을 취소 합니다.  
  
     응용 프로그램은 완전 신뢰 보안 설정으로 실행 됩니다. **보안** 페이지의 모든 설정은 무시 됩니다.  
  
    > [!NOTE]
    > 게시 마법사를 사용 하 여 응용 프로그램을 게시할 때마다이 확인란이 선택 됩니다. 게시를 성공적으로 완료 한 후에 다시 지워야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 응용 프로그램에 대 한 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)

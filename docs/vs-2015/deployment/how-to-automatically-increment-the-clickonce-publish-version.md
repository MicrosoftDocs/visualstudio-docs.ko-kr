---
title: '방법: ClickOnce 게시 버전 자동 증가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 50faf70e8eda6ef7ab01201102540729497eb87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683917"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>방법: ClickOnce 게시 버전 자동 증가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램을 게시할 때 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 속성을 변경 하면 `Publish Version` 응용 프로그램이 업데이트로 게시 됩니다. 기본적으로 Visual Studio는 `Revision` 응용 프로그램을 게시할 때마다의 수를 자동으로 증가 시킵니다 `Publish Version` .  
  
 **프로젝트 디자이너**의 **게시** 페이지에서이 동작을 사용 하지 않도록 설정할 수 있습니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
### <a name="to-disable-automatically-incrementing-the-publish-version"></a>게시 버전 자동 증가를 사용 하지 않도록 설정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. **게시 버전** 섹션에서 **릴리스할 때마다 자동으로 수정 번호 증가** 확인란의 선택을 취소 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: ClickOnce 게시 버전 설정](../deployment/how-to-set-the-clickonce-publish-version.md)   
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

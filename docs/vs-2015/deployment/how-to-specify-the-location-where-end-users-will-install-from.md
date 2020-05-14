---
title: '방법: 최종 사용자가 설치할 위치 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82181d906adc3454dfe77ef4fb21d8bdf99df16f
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557990"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>방법: 최종 사용자의 설치 원본 위치 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 게시 하는 경우 사용자가 응용 프로그램을 다운로드 하 여 설치 하는 위치는 처음에 응용 프로그램을 게시할 위치는 아닐 수 있습니다. 예를 들어, 일부 조직에서는 개발자가 응용 프로그램을 스테이징 서버에 게시 한 다음 관리자가 응용 프로그램을 웹 서버로 이동할 수 있습니다.  
  
 이 경우 `Installation URL` 속성을 사용 하 여 사용자가 응용 프로그램을 다운로드 하기 위해 이동할 웹 서버를 지정할 수 있습니다. 응용 프로그램 매니페스트에서 업데이트를 찾을 수 있는 위치를 알 수 있도록이 작업이 필요 합니다.  
  
 `Installation URL` 속성은 **프로젝트 디자이너**의 **게시** 페이지에서 설정할 수 있습니다.  
  
 **참고** 속성 **마법사**를 사용 하 여 `Installation URL` 속성을 설정할 수도 있습니다. 자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조 하세요.  
  
### <a name="to-specify-an-installation-url"></a>설치 URL을 지정 하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
2. **게시** 탭을 클릭합니다.  
  
3. 설치 URL 필드에 형식 `https://www.contoso.com/ApplicationName`를 사용 하 여 정규화 된 URL을 사용 하 여 설치 위치를 입력 하거나 `\\Server\ApplicationName`형식을 사용 하 여 UNC 경로를 입력 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: Visual Studio의 파일 복사 위치 지정](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)   
 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

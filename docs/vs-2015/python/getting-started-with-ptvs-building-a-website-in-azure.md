---
title: 'PTVS 시작: Azure에서 웹 사이트 빌드 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 3bdbda36-14d2-4fde-ba42-d91042777ff6
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 288fb24c9c1c4ddee1cb59a968e717531e274af1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300591"
---
# <a name="getting-started-with-ptvs-building-a-website-in-azure"></a>PTVS 시작: Azure에서 웹 사이트 빌드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Azure에서 Python 웹 사이트를 신속하게 빌드할 수 있습니다.  
  
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)을 통해 이러한 지침을 확인할 수 있습니다.  
  
 새 프로젝트... 대화 상자에서 Python 프로젝트 아래의 Bottle 웹 프로젝트를 선택합니다.  이 [Bottle](http://bottlepy.org/docs/dev/index.html) 템플릿은 [부트스트랩 프레임워크](https://getbootstrap.com/)를 기준으로 하는 시작 사이트입니다.  프로젝트를 만들 때 Visual Studio에서 종속성(이 경우 Bottle)을 가상 환경에 설치하라는 메시지를 표시합니다.  Azure 웹 사이트에 배포하기 때문에 사이트 작업에 필요한 비트를 배포하기 위해 가상 환경에 종속성을 추가해야 합니다.  또한 Python 2.7 또는 3.4 32비트를 기반으로 하는 환경을 설정해야 합니다.  프로젝트를 만든 후 F5 키를 눌러 사이트를 로컬로 실행합니다.  
  
 Azure에서 쉽게 사이트를 체험해 볼 수 있습니다.  Azure 구독이 없는 경우 [try.azurewebsites.net](https://trywebsites.azurewebsites.net/)을 사용할 수 있습니다.  이 사이트는 소셜 로그인만으로 한 번에 한 시간 동안 Azure Websites를 체험할 수 있는 간단한 방법을 제공합니다.  신용 카드를 사용할 필요가 없습니다.  언어 변경 드롭다운에서 빈 사이트 템플릿을 선택한 다음 만들기를 선택합니다.  "웹 애플리케이션 작업"에서 게시 프로필 다운로드를 선택하고 Visual Studio에서 사용할 파일을 저장합니다.  운영 체제의 git를 사용하여 배포할 수도 있습니다.  
  
 Visual Studio 및 직접 만든 프로젝트로 다시 전환합니다.  솔루션 탐색기에서 프로젝트 노드를 선택하고 오른쪽 포인터 단추를 선택한 다음 게시를 선택합니다.  Azure 구독이 있는 경우 대화 상자에서 Microsoft Azure 웹 사이트를 클릭하여 여기서 사이트를 관리할 수 있습니다.  이 연습에서는 가져오기를 선택하여 방금 다운로드한 게시 프로필을 선택합니다.  게시 프로필에 필요한 모든 정보가 있으므로 게시를 선택할 수 있습니다.  몇 초 내에 새 브라우저 창이 열리고 사이트가 라이브로 Azure 클라우드에 호스트됩니다.  
  
 간단한 웹 사이트는 쉽지만 Azure의 보다 중요한 웹 애플리케이션에 대한 자세한 내용은 [심층 분석](https://www.youtube.com/watch?v=WG3pGmoo8nE&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=10) 동영상과 이 채널의 기타 동영상(시작 또는 심층 분석 동영상 페이지의 오른쪽 위에 있는 링크)을 참조하세요.  
  
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6)을 통해 이러한 지침을 확인할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Wiki 설명서](https://github.com/Microsoft/PTVS/wiki/Web-Project)   
 [PTVS Getting Started and Deep Dive Videos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)(PTVS 시작 및 자세히 알아보기 동영상)

---
title: 'PTVS 시작: 코딩 시작(프로젝트) | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 28622f290d82f86bf3d18cc4f40cfcfc8e953dad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537155"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>PTVS 시작: 코딩 시작(프로젝트)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS(Python Tools for Visual Studio)는 코드 관리에 도움이 됩니다. 
 
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2)을 통해 이러한 지침을 확인할 수 있습니다. 
 
 이전에 Python을 사용한 적이 있다면 프로젝트가 디스크의 파일 레이아웃에 따라 정의된다는 것을 알고 있을 것입니다. 이 방식은 일반 Python 프로젝트에서는 효과적이지만 추가 파일(JavaScript 포함 웹 페이지, 단위 테스트 및 빌드 스크립트)이 있는 경우 파일 시스템이 다소 제한적일 수 있습니다. Visual Studio는 프로젝트를 사용하여 세 가지 작업을 수행합니다. 
 
- 중요한 파일을 식별합니다. 중요한 파일은 버전 제어 시스템에 체크 인하는 파일(소스 파일, 리소스 등)이지만 빌드 출력으로 생성된 파일은 아닙니다. 또한 중요한 파일은 다른 사용자가 앱에서 작업할 수 있도록 다른 컴퓨터로 복사하는 파일입니다. 
 
- 파일 사용 방법을 지정합니다. 파일이 변경될 때마다 도구에서 처리해야 하는 파일이 있을 수도 있습니다. Visual Studio 프로젝트는 이 정보를 캡처할 수 있습니다. 
 
- 구성 요소 경계를 정의합니다. 앱에 여러 구성 요소가 있는 경우 각각 별도의 프로젝트에 넣을 수 있습니다. 이러한 프로젝트는 결국 다른 빌드 또는 디버그 설정으로 빌드된 다른 서버에 배포되거나, C++ 또는 Node.js와 같은 Visual Studio에서 지원하는 다른 언어를 사용하여 작성될 수 있습니다. 
 
  시작하는 데 도움이 되는 여러 프로젝트 템플릿이 있습니다. 작업하려는 Python 코드가 이미 있는 경우 기존 코드 마법사를 통해 모든 파일을 포함하는 프로젝트를 만들 수 있습니다. 일부 인기 있는 프레임워크에 대한 여러 개의 웹 프로젝트가 있습니다. PTVS 샘플 팩에서 추가 템플릿을 사용할 수 있습니다. 제공된 웹 템플릿이 다른 프레임워크에서 작동하게 하는 옵션이 있습니다. Python 애플리케이션 템플릿은 깨끗한 빈 프로젝트입니다. 시작하기 위한 모듈 한 개가 있습니다. 
 
  Visual Studio는 모든 파일, 검색 경로 및 Python 환경을 포함하여 열린 프로젝트를 솔루션 탐색기 창에 표시합니다. 새 항목을 추가하려면 프로젝트 폴더를 선택하고 상황에 맞는 메뉴(오른쪽 포인터 단추 누름)에서 추가, 새 항목을 차례로 선택합니다. 대화 상자에서 항목을 선택하고 항목의 이름을 사용자 지정한 다음 프로젝트에 항목을 추가할 수 있습니다. 
 
  솔루션 탐색기에 끌어다 놓을 수 있습니다. 프로젝트 디렉터리 구조에 파일을 이미 복사한 경우 솔루션 탐색기 맨 위에서 모든 파일 표시를 선택할 수 있습니다. 그런 다음 추가할 항목을 선택하고 상황에 맞는 메뉴에서 프로젝트에 포함을 선택할 수 있습니다. 
 
  짧은 [youtube 동영상](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2)을 통해 이러한 지침을 확인할 수 있습니다. 
 
## <a name="see-also"></a>관련 항목 
 [Wiki 설명서](https://github.com/Microsoft/PTVS/wiki/Projects) [PTVS 시작 및 자세히 알아보기 동영상](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

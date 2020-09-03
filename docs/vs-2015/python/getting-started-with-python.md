---
title: Python 시작 하기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 33f4f6fb-0ae4-4234-9df2-531f2d3af17f
caps.latest.revision: 13
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 97d60fe31f838c4cc497701f4560dc426ebc1cc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80543969"
---
# <a name="getting-started-with-python"></a>Python 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS (Visual Studio용 Python 도구)는 강력한 Python 개발 환경을 제공 하는 Visual Studio의 무료 [오픈 소스](https://github.com/Microsoft/ptvs) 플러그 인입니다.  
  
## <a name="python-the-language"></a>Python 언어
  
Python은 응용 프로그램, 웹 사이트 및 클라우드 서비스에서 작업 하는 많은 대학, 과학자, 앱 스크립터가, 평범한 개발자 및 전문 개발자가 사용 하는 널리 사용 되는 프로그래밍 언어입니다.

프로그래밍 언어인 Python은 다음과 같습니다.
  
- 신뢰할 수 있습니다.
- 일반적으로 빠른 프로그램, 앱 스크립팅, 데스크톱 앱, 웹 서버, 웹 서비스 및 과학적 컴퓨팅을 스크립팅 하는 데 유용 합니다.
- 배우기 쉽고 효율적인 코딩을 유도하는 뛰어난 디자인을 가지고 있습니다(많은 대학에서 초급 프로그래밍 과정에 사용함).
- 유연 하 고 명령적, 기능 및 개체 지향 프로그래밍 스타일을 지원 합니다.
- 무료 및 오픈 소스.
- 모든 주요 운영 체제에서 제대로 실행 됩니다.  
- 빠르고 유용 하 고 잘 디자인 된 여러 라이브러리에서 지원 됩니다.  
- 많은 설명서, 샘플 및 강력한 개발자 커뮤니티에서 지원 됩니다.  

언어에 대 한 자세한 내용은 python.org의 [초보자를 위한 Python](https://www.python.org/about/gettingstarted/) 부터 시작 하세요.

Python 자체를 설치 하려면를 방문 [https://www.python.org/download/](https://www.python.org/download/) 하세요.

## <a name="python-tools-for-visual-studio"></a>Python Tools for Visual Studio
  
[Visualstudio.com](https://www.visualstudio.com/explore/python-vs)에서 설치할 수 있는 Visual Studio용 Python 도구는 다음과 같은 기능을 제공 합니다.  
  
- 여러 해석기 지원: 다양한 버전의 CPython, IronPython 및 IPython  
- Python 코드의 폴더 구조를 암시적으로 선택하고 앱 코드, 테스트 코드, 웹 페이지, JavaScript, 빌드 스크립트 등을 식별할 수 있도록 명시적으로 제어할 수 있는 프로젝트 시스템.  
- 콘솔, 웹, Azure, 데이터 과학 및 기타 형식의 프로젝트에 대한 프로젝트 템플릿    
- Python 용 Azure SDK (아래 참조)    
- 색 지정, 모든 코드 및 라이브러리에 대한 자동 완성, 시그니처 도움말, 클래스 뷰, 정의로 이동, 모든 참조 찾기, 리팩터링 등을 포함한 다양한 편집 및 코드 이해 기능    
- 대화형(REPL) 창
- 데이터 시각화를 사용한 IPython
- IronPython 및 .NET/WPF 지원    
- Visual Studio 프로젝트 없이 풍부한 디버깅, 기존 실행 파일에 대한 기능, 혼합 모드 디버깅, Mac/Windows/Linux로 원격 디버깅 및 대화형 창 내에서 디버깅   
- 프로파일링 도구  
- 테스트 도구  
  
다음 리소스는 시작하는 데 도움이 될 수 있습니다.

- [설치 가이드](https://github.com/Microsoft/PTVS/wiki/PTVS-Installation)    
- [Getting started and deep dive short videos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)(PTVS 시작 및 자세히 알아보기 동영상)  
- 설치 및 기능 데모 (27 분)] (https://www.youtube.com/watch?v=JNNAOypc6Ek)  
- [설명서](https://github.com/Microsoft/PTVS/wiki)  

Visual Studio가 현재는 Python을 사용 하 여 독립 실행형 실행 파일을 만드는 수단을 제공 하지 않습니다. 즉, 기본적으로 포함 된 Python 인터프리터를 사용 하는 프로그램을 의미 합니다. 그러나 [StackOverflow](https://stackoverflow.com/questions/5458048/how-to-make-a-python-script-standalone-executable-to-run-without-any-dependency)에 설명된 것처럼 Python 커뮤니티 내에 이렇게 하는 다양한 방법이 있습니다. 또한 CPython은 블로그 게시물 [Using CPython's Embeddable Zip File](https://devblogs.microsoft.com/python/cpython-embeddable-zip-file/)(CPython의 포함 가능한 Zip 파일 사용)에 설명된 것처럼 네이티브 애플리케이션 내에 포함되는 기능을 지원합니다.
  
## <a name="building-ui-with-python"></a>Python을 사용 하 여 UI 빌드  

Python을 사용 하 여 UI를 작성 하는 주요 제품은 [PySide (공식 바인딩)](https://wiki.qt.io/PySide) ( [PySide 다운로드](https://download.qt.io/official_releases/pyside/.)도 참조) 및 [PyQt](https://wiki.python.org/moin/PyQt)라고도 하는 python에 대 한 바인딩을 포함 하는 [Qt 프로젝트](https://www.qt.io/qt-for-application-development/)입니다. 현재는 Visual Studio의 Python 지원에 UI 개발용 특정 도구가 포함되지 않습니다.

## <a name="azure-sdk-for-python"></a>Python용 Azure SDK
  
Windows, Mac 및 Linux를 지원하는 Python용 Azure SDK을 통해 Microsoft Azure 서비스를 쉽게 이용하고 관리할 수 있습니다. 자세한 내용은 다음 리소스를 참조하세요. 

- SDK를 설치하려면 [Python Package Index](https://pypi.python.org/pypi/azure)(Python 패키지 인덱스)를 사용하거나 Azure 문서에서 [Python 및 SDK 설치](/azure/developer/python/azure-sdk-install)를 따르세요. 
- [Python 개발자 센터용 Azure SDK](https://azure.microsoft.com/develop/python/)에는 설치부터 자습서 포함 설명서에 이르기까지 많은 도움말이 있습니다.  중요 사항은 다음과 같습니다.  
- 방법 가이드:
  - [저장소 Blob](https://azure.microsoft.com/develop/python/how-to-guides/blob-service/)  
  - [저장소 큐](https://azure.microsoft.com/develop/python/how-to-guides/queue-service/)  
  - [저장소 테이블](https://azure.microsoft.com/develop/python/how-to-guides/table-service/)  
  - [Service Bus 큐](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-queues/)
  - [항목/구독 Service Bus](https://azure.microsoft.com/develop/python/how-to-guides/service-bus-topics/) 
  - [서비스 관리](https://azure.microsoft.com/develop/python/how-to-guides/service-management/)  

## <a name="scientific-computing"></a>과학적 컴퓨팅

모든 Python 데이터 과학자 라이브러리 외에도 Visual Studio용 Python 도구는 Azure에서 호스트할 수 있는 IPython 및 IPython Notebook을 지원합니다.

[University of California, Irvine](https://www.lfd.uci.edu/~gohlke/pythonlibs/#scipy-stack)(캘리포니아 대학교 어바인 캠퍼스)에서 IPython 및 과학적 컴퓨팅 라이브러리(matplotlib, scipy, numpy 등)를 가져오는 것이 좋습니다.  
  
## <a name="see-also"></a>관련 항목  

[PTVS 시작: Visual Studio 설정](../python/getting-started-with-ptvs-setting-up-visual-studio.md) 
 [PTVS 시작: 코딩 시작 (프로젝트)](../python/getting-started-with-ptvs-start-coding-projects.md) 
 [PTVS 시작: 코드 편집](../python/getting-started-with-ptvs-editing-code.md) 
 [PTVS 시작: 디버깅](../python/getting-started-with-ptvs-debugging.md) 
 [PTVS 시작: 대화형 Python](../python/getting-started-with-ptvs-interactive-python.md) 
 [PTVS 시작: Azure에서 웹 사이트 빌드](../python/getting-started-with-ptvs-building-a-website-in-azure.md)

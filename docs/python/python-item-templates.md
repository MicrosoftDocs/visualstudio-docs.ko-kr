---
title: Python 프로젝트용 항목 템플릿
description: Visual Studio의 추가 > 새 항목 대화 상자를 통해 사용할 수 있는 Python 프로젝트용 항목 템플릿의 참조 목록입니다.
ms.date: 12/06/2018
ms.topic: tutorial
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c093dad1364fd5209f51c8e87e3fb99b3c1d3c4a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "62430346"
---
# <a name="python-item-templates"></a>Python 항목 템플릿

항목 템플릿은 **프로젝트** > **새 항목 추가** 메뉴 명령 또는 **솔루션 탐색기**의 상황에 맞는 메뉴에서 **추가** > **새 항목** 명령을 통해 Python 프로젝트에서 사용할 수 있습니다.

![새 항목 추가 대화 상자](media/project-item-templates.png)

항목에 대해 제공한 이름을 사용하여 템플릿은 일반적으로 프로젝트에서 현재 선택한 폴더(폴더를 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴를 표시하면 해당 폴더가 자동으로 선택됨) 내에 하나 이상의 파일 및 폴더를 만듭니다. 항목을 추가하면 Visual Studio 프로젝트에 포함되고 **솔루션 탐색기**에 항목이 나타납니다.

다음 표에서는 Python 프로젝트 내에서 각 항목 템플릿의 효과를 간략히 설명합니다.

| 템플릿 | 템플릿에서 만드는 항목 |
| --- | --- |
| **빈 Python 파일** | *.py* 확장명을 사용하는 빈 파일 |
| **Python 클래스** | 하나의 빈 Python 클래스 정의를 포함하는 *.py* 파일 |
| **Python 패키지** | *\_\_init\_\_.py* 파일을 포함하는 폴더 |
| **Python 단위 테스트** | 파일에서 테스트를 실행하기 위한 `unittest.main()` 호출과 함께 `unittest` 프레임워크를 기반으로 한 단일 단위 테스트가 있는 *.py* 파일 |
| **HTML 페이지** | `<head>` 및 `<body>` 요소로 구성된 간단한 페이지 구조의 *.html* 파일 |
| **JavaScript** | 빈 *.js* 파일 |
| **스타일시트** | `body`에 대한 빈 스타일을 포함하는 *.css* 파일 |
| **텍스트 파일** | 빈 *.txt* 파일 |
| **Django 1.9 앱**<br/>**Django 1.4 앱** | 앱 이름을 사용하는 폴더로, Django 1.9의 경우 [Visual Studio의 Django 알아보기, 2-2단계](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure)에 설명된 대로 Django 앱에 대한 핵심 파일을 포함합니다. Django 1.4의 경우 *migrations* 폴더, *admin.py* 파일 및 *apps.py* 파일은 포함되지 않습니다. |
| **IronPython WPF 창** | 두 개의 병렬 파일(빈 `<Grid>` 요소로 `<Window>`를 정의하는 *.xaml* 파일과 `wpf` 라이브러리를 사용하여 XAML 파일을 로드하는 연결된 *.py* 파일)로 구성된 WPF 창. 일반적으로 IronPython 프로젝트 템플릿 중 하나를 사용하여 만든 프로젝트 내에서 사용됩니다. [Python 프로젝트 관리 - 프로젝트 템플릿](managing-python-projects-in-visual-studio.md#project-templates)을 참조하세요. |
| **웹 역할 지원 파일** | 프로젝트 루트(프로젝트에서 선택한 폴더와 관계없음)의 *bin* 폴더. 이 폴더에는 Azure Cloud Service 웹 역할에 대한 기본 배포 스크립트와 *web.config* 파일이 포함됩니다. 템플릿에는 세부 정보를 설명하는 *readme.html* 파일도 포함되어 있습니다. |
| **작업자 역할 지원 파일** | 프로젝트 루트(프로젝트에서 선택한 폴더와 관계없음)의 *bin* 폴더. 이 폴더에는 *web.config* 파일과 함께 Azure Cloud Service 작업자 역할에 대한 기본 배포 및 시작 스크립트가 포함됩니다. 템플릿에는 세부 정보를 설명하는 *readme.html* 파일도 포함되어 있습니다. |
| **Azure web.config(FastCGI)** | [WSGI](https://wsgi.readthedocs.io/en/latest/) 개체를 사용하여 들어오는 연결을 처리하는 앱에 대한 항목이 포함된 *web.config* 파일. 이 파일은 일반적으로 IIS를 실행하는 웹 서버의 루트에 배포됩니다. 자세한 내용은 [IIS에 대한 앱 구성](configure-web-apps-for-iis-windows.md)을 참조하세요. |
| **Azure web.config(HttpPlatformHandler)** | 소켓에서 들어오는 연결을 수신 대기하는 앱에 대한 항목이 포함된 *web.config* 파일. 이 파일은 일반적으로 Azure App Service와 같이 IIS를 실행하는 웹 서버의 루트에 배포됩니다. 자세한 내용은 [IIS에 대한 앱 구성](configure-web-apps-for-iis-windows.md)을 참조하세요. |
| **Azure 정적 파일 web.config** | 일반적으로 *static* 폴더(또는 정적 항목을 포함하는 다른 폴더)에 추가되어 해당 폴더에 대한 Python 처리를 사용하지 않도록 설정하는 *web.config* 파일. 이 구성 파일은 위의 FastCGI 또는 HttpPlatformHandler 구성 파일 중 하나와 함께 작동합니다. 자세한 내용은 [IIS에 대한 앱 구성](configure-web-apps-for-iis-windows.md)을 참조하세요. |
| **Azure 원격 디버깅 web.config** | 사용되지 않습니다(더 이상 지원되지 않는 Windows용 Azure App Service의 원격 디버깅에 사용됨). |

## <a name="see-also"></a>참조

- [Python 프로젝트 관리 - 프로젝트 템플릿](managing-python-projects-in-visual-studio.md#project-templates)
- [Python 웹 프로젝트 템플릿](python-web-application-project-templates.md)
- [Azure App Service에 게시](publishing-python-web-applications-to-azure-from-visual-studio.md)

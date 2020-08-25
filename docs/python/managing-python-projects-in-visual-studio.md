---
title: Python 애플리케이션 프로젝트 관리
description: Visual Studio의 프로젝트는 파일 간의 종속성과 애플리케이션의 관계 복잡성을 관리합니다.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9031b0107babf3d31b6e3b70bb7952cd83467d7d
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238792"
---
# <a name="python-projects-in-visual-studio"></a>Visual Studio의 Python 프로젝트

일반적으로 Python 애플리케이션은 폴더 및 파일만 사용하여 정의되지만 애플리케이션이 커질수록 이 구조는 복잡해질 수 있으며 자동 생성된 파일, 웹 애플리케이션용 JavaScript 등을 포함할 수 있습니다. Visual Studio 프로젝트는 이러한 복잡성을 관리하는 데 도움이 됩니다. 프로젝트( *.pyproj* 파일)는 프로젝트와 관련된 모든 소스 및 콘텐츠 파일을 식별하며 각 파일에 대한 빌드 정보를 포함하고 소스 제어 시스템과 통합할 정보를 유지 관리하며 애플리케이션을 논리 구성 요소로 구성하는 데 도움을 줍니다.

![솔루션 탐색기에서 Python 프로젝트](media/projects-solution-explorer.png)

또한 프로젝트는 항상 Visual Studio *솔루션* 내에서 관리되므로 서로를 참조할 수 있는 프로젝트를 여러 개 포함할 수 있습니다. 예를 들어 Python 프로젝트에서 확장 모듈을 구현하는 C++ 프로젝트를 참조할 수 있습니다. 이 관계를 통해 Visual Studio에서는 Python 프로젝트 디버그를 시작할 때 자동으로 C++ 프로젝트를 빌드합니다(필요한 경우). (일반적인 설명은 [Visual Studio의 솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md)를 참조하세요.)

Visual Studio는 기존 폴더 트리에서 프로젝트를 만드는 템플릿과 깨끗하고 빈 프로젝트를 만드는 템플릿을 비롯하여 다양한 애플리케이션 구조를 신속하게 설정할 수 있도록 해주는 다양한 Python 프로젝트 템플릿을 제공합니다. 인덱스는 [프로젝트 템플릿](#project-templates)을 참조하세요.

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019는 Visual Studio 프로젝트 및 솔루션 파일을 만들지 않고도 Python 코드가 포함된 폴더를 열어 해당 코드를 실행하도록 지원합니다. 자세한 내용은 [빠른 시작: 폴더에서 Python 코드 열기 및 실행](quickstart-05-python-visual-studio-open-folder.md)을 참조하세요. 하지만 이 섹션에서 설명한 대로 프로젝트 파일 사용을 통해 얻을 수 있는 이점이 있습니다.
::: moniker-end

> [!Tip]
> 프로젝트가 없으면 모든 버전의 Visual Studio가 Python 코드와 잘 작동합니다. 예를 들어 편집기를 마우스 오른쪽 단추로 클릭하고 **디버깅 시작**을 선택하여 Python 파일 자체를 열고 자동 완성, IntelliSense 및 디버깅을 활용할 수 있습니다. 그러나 이러한 코드는 항상 기본 전역 환경을 사용하기 때문에 코드가 다른 환경용으로 작성된 경우 잘못된 완성 또는 오류가 표시될 수 있습니다. 또한 Visual Studio는 단일 파일이 열리는 폴더의 모든 파일과 패키지를 분석하므로 상당한 CPU 시간을 소비할 수 있습니다.
>
> [기존 파일에서 프로젝트 만들기](#create-project-from-existing-files)에 설명된 대로 기존 코드에서 Visual Studio 프로젝트를 만드는 것이 간단합니다.

![동영상에 대한 비디오 카메라 아이콘](../install/media/video-icon.png "비디오 시청") [심층 분석: Python 프로젝트에서 소스 제어 사용](https://youtu.be/Aq8eqApnugM)(youtube.com, 8분 55초)도 시청하세요.

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>파일 추가. 시작 파일 할당. 환경 설정

애플리케이션을 개발할 때 일반적으로 다양한 유형의 새 파일을 프로젝트에 추가해야 합니다. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **기존 항목**을 선택하여 추가할 파일을 찾거나 **추가** > **새 항목**을 선택하여 다양한 항목 템플릿이 들어 있는 대화 상자를 표시하면 이러한 파일을 추가할 수 있습니다. [항목 템플릿](python-item-templates.md) 참조에 설명된 대로 옵션에는 빈 Python 파일, Python 클래스, 단위 테스트 및 웹 애플리케이션과 관련된 다양한 파일이 포함됩니다. 테스트 프로젝트를 통해 이러한 옵션을 시도해 보고 사용자의 Visual Studio 버전에서 사용 가능한 항목을 알아볼 수 있습니다.

각 Python 프로젝트에는 **솔루션 탐색기**에서 굵게 표시된 시작 파일이 하나씩 할당되어 있습니다. 시작 파일은 디버깅을 시작하거나(**F5** 또는 **디버그** > **디버깅 시작**) **대화형** 창에서 프로젝트를 실행할 때(**Shift**+**Alt**+**F5** 또는 **디버그** > **Python 대화형에서 프로젝트 실행**) 실행됩니다. 이 파일을 변경하려면 새 파일을 마우스 오른쪽 단추로 클릭하고 **시작 항목으로 설정**(또는 이전 버전의 Visual Studio에서는 **시작 파일로 설정**)을 선택합니다.

> [!Tip]
> 프로젝트에서 선택한 시작 파일을 제거하고 새 시작 파일을 선택하지 않으면 프로젝트를 실행하려고 할 때 Visual Studio에서 시작할 Python 파일을 알지 못합니다. 이 경우 Visual Studio 2017 버전 15.6 이상에서는 오류가 표시되고, 이전 버전에서는 Python 인터프리터를 실행하는 출력 창이 열리거나 출력 창이 표시된 후 거의 즉시 사라집니다. 이러한 동작이 발생할 경우 할당된 시작 파일이 있는지 확인합니다.
>
> 어떤 이유로든 출력 창을 열어 두려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택한 다음, **디버그** 탭을 선택하고 **인터프리터 인수** 필드에 `-i`를 추가합니다. 이 인수를 사용하면 프로그램이 완료된 후 인터프리터가 대화형 모드로 전환되어 창이 열린 상태로 유지되며 **Ctrl**+**Z** > **Enter** 키를 누르면 종료됩니다.

::: moniker range="vs-2017"
새 프로젝트는 항상 기본 글로벌 Python 환경과 연결됩니다. 프로젝트를 다른 환경(가상 환경 포함)과 연결하려면 프로젝트의 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고, **Python 환경 추가/제거**를 선택하고, 원하는 항목을 선택합니다.
::: moniker-end
::: moniker range=">=vs-2019"
새 프로젝트는 항상 기본 글로벌 Python 환경과 연결됩니다. 프로젝트를 다른 환경(가상 환경 포함)과 연결하려면 프로젝트의 **Python 환경** 노드를 마우스 오른쪽 단추로 클릭하고, **환경 추가..** 를 선택하고, 원하는 항목을 선택합니다. 도구 모음의 환경 드롭다운 컨트롤을 사용하여 환경을 선택하거나 다른 환경을 프로젝트에 추가할 수도 있습니다.

![Python 도구 모음의 환경 추가 명령](media/environments/environments-toolbar-2019.png)
::: moniker-end

활성 상태의 환경을 변경하려면 아래 표시된 것처럼 **솔루션 탐색기**에서 원하는 환경을 마우스 오른쪽 단추로 클릭하고 **환경 활성화**를 선택합니다. 자세한 내용은 [프로젝트의 환경 선택](selecting-a-python-environment-for-a-project.md)을 참조하세요.

![Python 프로젝트에 대한 환경 활성화](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>프로젝트 템플릿

Visual Studio는 처음부터 작성하거나 기존 코드에서 작성하는 등 Python 프로젝트를 설정하는 다양한 방법을 제공합니다. 템플릿을 사용하려면 **파일** > **새로 만들기** > **프로젝트** 메뉴 명령을 선택하거나 **솔루션 탐색기**에서 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다. 두 방법 모두 아래의 **새 프로젝트** 대화 상자가 표시됩니다. Python 관련 템플릿을 보려면 “Python”을 검색하거나 **설치됨** > **Python** 노드를 선택합니다.

![Python 템플릿이 있는 새 프로젝트 대화 상자](media/projects-new-project-dialog.png)

다음 표에서는 Visual Studio 2017 이상에서 사용 가능한 템플릿을 요약하여 보여줍니다(일부 템플릿만 이전 모든 버전에서 사용 가능).

| 템플릿 | Description |
| --- | --- |
| [**기존 Python 코드에서**](#create-project-from-existing-files) | 폴더 구조의 기존 Python 코드에서 Visual Studio 프로젝트를 만듭니다.  |
| **Python 애플리케이션** | 하나의 비어있는 소스 파일을 포함하는 새로운 Python 애플리케이션에 대한 기본 프로젝트 구조입니다. 기본적으로 프로젝트는 기본 글로벌 환경의 콘솔 인터프리터에서 실행되며 [서로 다른 환경을 할당](selecting-a-python-environment-for-a-project.md)하여 변경할 수 있습니다. |
| [**Azure Cloud Service**](python-azure-cloud-service-project-template.md) | Python으로 작성된 Azure Cloud Service에 대한 프로젝트입니다. |
| [**웹 프로젝트**](python-web-application-project-templates.md) | Bottle, Django 및 Flask를 비롯한 다양한 프레임워크를 기반으로 하는 웹앱에 대한 프로젝트입니다. |
| **IronPython 애플리케이션** | Python 애플리케이션 템플릿과 유사하지만 .NET interop 및 .NET 언어로 혼합 모드 디버깅을 기본적으로 사용하는 IronPython을 사용합니다. |
| **IronPython WPF 애플리케이션** | 애플리케이션의 사용자 인터페이스에 대한 Windows Presentation Foundation XAML 파일에 IronPython을 사용하는 프로젝트 구조입니다. Visual Studio는 XAML UI 디자이너를 제공하고 코드 숨김은 Python으로 작성할 수 있으며 애플리케이션은 콘솔을 표시하지 않고 실행됩니다. |
| **IronPython Silverlight 웹 페이지** | Silverlight를 사용하여 브라우저에서 실행되는 IronPython 프로젝트입니다. 애플리케이션의 Python 코드는 웹 페이지에 스크립트로 포함됩니다. 상용구 스크립트 태그는 Silverlight 내부에서 실행되는 IronPython을 초기화하는 일부 JavaScript 코드를 가져오며, 여기서 Python 코드가 DOM과 상호 작용할 수 있습니다. |
| **IronPython Windows Forms 애플리케이션** | Windows Forms에서 코드를 사용하여 만든 UI와 IronPython을 사용하는 프로젝트 구조입니다. 콘솔을 표시하지 않고 애플리케이션을 실행합니다. |
| **백그라운드 애플리케이션(IoT)** | 디바이스에서 백그라운드 서비스로 실행되도록 Python 프로젝트 배포를 지원합니다. 자세한 내용은 [Windows IoT 개발자 센터](https://dev.windows.com/en-us/iot)를 참조하세요. |
| **Python 확장 모듈** | 이 템플릿은 Python 워크로드와 함께 **Python 네이티브 개발 도구**를 Visual Studio 2017 이상에 설치한 경우([설치](installing-python-support-in-visual-studio.md) 참조) Visual C++ 아래에 나타납니다. 여기서는 [Python용 C++ 확장 만들기](working-with-c-cpp-python-in-visual-studio.md)에 설명된 대로 C++ 확장 DLL의 핵심 구조를 제공합니다. |

> [!Note]
> Python은 해석된 언어이므로 Visual Studio의 Python 프로젝트는 다른 컴파일된 언어 프로젝트(예: C#)와 같은 독립 실행형 실행 파일을 생성하지 않습니다. 자세한 내용은 [질문 및 답변](overview-of-python-tools-for-visual-studio.md#questions-and-answers)을 참조하세요.

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>기존 파일의 프로젝트 만들기

> [!Important]
> 여기에 설명된 프로세스는 원래 원본 파일을 이동하거나 복사하지 않습니다. 복사본으로 작업하려면 먼저 폴더를 복제합니다.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>연결된 파일

연결된 파일은 프로젝트로 가져온 파일이지만 일반적으로 애플리케이션의 프로젝트 폴더 외부에 상주합니다. **솔루션 탐색기**에서 오버레이드된 바로 가기 아이콘이 있는 일반 파일로 나타납니다. ![연결된 파일 아이콘](media/projects-linked-file-icon.png)

연결된 파일은 `<Compile Include="...">` 요소를 사용하여 *.pyproj* 파일에 지정됩니다. 연결된 파일은 디렉터리 구조 외부에 상대 경로를 사용하는 경우 암시적이고, **솔루션 탐색기** 내에서 경로를 사용하는 경우 명시적입니다.

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

다음 조건에서는 연결된 파일이 무시됩니다.

- 연결된 파일에는 프로젝트 디렉터리 내에서 있는 Include 특성에 지정된 경로 및 링크 메타데이터가 포함됩니다.
- 연결된 파일이 프로젝트 계층 구조 내에 존재하는 파일을 복제하는 경우
- 연결된 파일에는 프로젝트 계층 구조 외부 상대 경로인 링크 경로와 링크 메타데이터가 포함됩니다.
- 링크 경로가 루트임

### <a name="work-with-linked-files"></a>연결된 파일 작업

기존 항목을 링크로 추가하려면 파일을 추가할 프로젝트에서 폴더를 마우스 오른쪽 단추로 클릭하고 **추가** > **기존 항목**을 선택합니다. 표시되는 대화 상자에서 파일을 선택하고 **추가** 단추의 드롭다운에서 **링크로 추가**를 선택합니다. 충돌하는 파일이 없다면 이 명령은 선택한 폴더에 링크를 만듭니다. 하지만 같은 이름의 파일이 이미 있거나 해당 파일에 대한 링크가 프로젝트에 이미 있는 경우 링크가 추가되지 않습니다.

프로젝트 폴더에 이미 있는 파일로 링크를 시도하면 링크가 아닌 일반 파일로 추가됩니다. 파일을 링크로 변환하려면 **파일** > **다른 이름으로 저장**을 선택하여 파일을 프로젝트 계층 구조 외부 위치에 저장합니다. 그러면 Visual Studio에서 링크로 자동 변환합니다. 마찬가지로 **파일** > **다른 이름으로 저장**을 사용하여 링크를 다시 변환하고 프로젝트 계층 구조 내의 파일에 저장할 수 있습니다.

**솔루션 탐색기**에서 연결된 파일을 이동하면 링크가 이동되지만 실제 파일은 영향을 받지 않습니다. 마찬가지로, 링크를 삭제하면 파일에 영향을 주지 않고 링크가 제거됩니다.

연결된 파일의 이름을 바꿀 수 없습니다.

## <a name="references"></a>참고자료

Visual Studio 프로젝트는 프로젝트 및 확장에 참조 추가를 지원하며 이 내용은 **솔루션 탐색기**의 **참조** 노드 아래 나타납니다.

![Python 프로젝트에서 확장 참조](media/projects-extension-references.png)

일반적으로 확장 참조는 프로젝트 간의 종속성을 나타내며 디자인 타임에 IntelliSense를 제공하거나 컴파일 타임에 링크를 제공하는 데 사용됩니다. Python 프로젝트는 유사한 방식으로 참조를 사용하지만, Python의 동적 특성으로 인해 주로 디자인 타임에 향상된 IntelliSense를 제공하는 데 사용됩니다. 또한 추가 종속성을 설치하기 위해 Microsoft Azure에 배포하는 데도 사용할 수 있습니다.

### <a name="extension-modules"></a>확장 모듈

*.pyd* 파일에 대한 참조를 통해 생성된 모듈에 IntelliSense를 사용할 수 있습니다. Visual Studio는 *.pyd* 파일을 Python 인터프리터에 로드하고 해당 형식과 함수를 내부적으로 검사합니다. 또한 함수에 대한 doc 문자열의 구문 분석을 시도하여 서명 도움말도 제공합니다.

언제든지 디스크에서 확장 모듈이 업데이트되는 경우 Visual Studio는 백그라운드로 모듈을 다시 분석합니다. 이 작업은 런타임 동작에 영향을 주지 않지만, 분석이 완료될 때까지 일부 완성 기능을 사용할 수 없습니다.

모듈을 포함하는 폴더에 [검색 경로](search-paths.md)를 추가해야 할 수 있습니다.

### <a name="net-projects"></a>.NET 프로젝트

IronPython으로 작업하는 경우 .NET 어셈블리에 참조를 추가하여 IntelliSense를 사용하도록 설정할 수 있습니다. 사용자 솔루션에 있는 .NET 프로젝트의 경우 Python 프로젝트에서 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**, **프로젝트** 탭을 차례로 선택한 후 원하는 프로젝트를 찾습니다. 별도로 다운로드한 DLL의 경우 원하는 대신 **찾아보기** 탭을 선택하여 원하는 DLL을 찾아봅니다.

IronPython의 참조는 `clr.AddReference('<AssemblyName>')`이 호출될 때까지 사용할 수 없으므로 어셈블리(일반적으로 코드의 시작 부분)에도 적절한 `clr.AddReference` 호출을 추가해야 합니다. 예를 들어 Visual Studio의 **IronPython Windows Forms 애플리케이션** 프로젝트 템플릿에서 만든 코드는 파일의 맨 위에 두 개의 호출을 포함합니다.

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>WebPI 프로젝트

WebPI 피드를 통해 추가 구성 요소를 설치할 수 있는 Microsoft Azure Cloud Services에 배포할 WebPI 제품 항목에 대한 참조를 추가할 수 있습니다. 기본적으로 표시된 피드는 Python에 국한되며 Django, CPython 및 기타 핵심 구성 요소를 포함합니다. 아래 표시된 것처럼 사용자 고유의 피드를 선택할 수도 있습니다. Microsoft Azure에 게시할 때 설치 작업은 참조된 모든 제품을 설치합니다.

> [!IMPORTANT]
> WebPI 프로젝트는 Visual Studio 2017 또는 Visual Studio 2019에서 사용할 수 없습니다.

![WebPI 참조](media/projects-webPI-components.png)

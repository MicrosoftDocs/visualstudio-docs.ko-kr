---
title: 혼합 모드 Python/C++ 디버깅에 대한 기호
description: Visual Studio에서 완벽한 혼합 모드 C++ 및 Python 디버깅을 위해 기호 로드 기능을 제공하는 방법입니다.
ms.date: 11/12/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 4a735c374216b1810b3abd99ffab89000cec8b8f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540922"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Python 인터프리터에 대한 디버깅 기호 설치

완전한 디버깅 환경을 제공하기 위해, Visual Studio의 [혼합 모드 Python 디버거](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)는 수많은 내부 데이터 구조를 구문 분석하는 데 사용되는 Python 인터프리터의 디버그 기호가 필요합니다. 예를 들어 *python27.dll*의 경우 해당 기호 파일은 *python27.pdb*이고, *python36.dll*의 경우 기호 파일은 *python36.pdb*입니다. 인터프리터의 각 버전은 다양한 모듈에 대한 기호 파일도 제공합니다.

Visual Studio 2017 이상에서 Python 3 및 Anaconda 3 인터프리터는 자동으로 각 기호를 설치하고 Visual Studio는 자동으로 해당 기호를 찾습니다. Visual Studio 2015 이전 버전의 경우 또는 다른 인터프리터를 사용하는 경우 별도로 기호를 다운로드한 다음, **디버깅** > **기호** 탭의 **도구** > **옵션** 대화 상자를 통해 Visual Studio가 해당 기호를 가리키도록 해야 합니다. 이러한 단계는 다음 섹션에 자세히 설명되어 있습니다.

Visual Studio는 기호가 필요한 경우(일반적으로 혼합 모드 디버깅 세션을 시작하는 경우) 메시지를 표시할 수 있습니다. 이 경우 다음과 같은 두 가지 선택 사항이 포함된 대화 상자를 표시합니다.

- **기호 설정 대화 상자 열기**는 **디버깅** > **기호** 탭에 대한 **옵션** 대화 상자를 엽니다.
- **인터프리터용 기호 다운로드**는 이 현재 설명서 페이지를 엽니다. 이 경우 **도구** > **옵션**을 선택하고 **디버깅** > **기호** 탭으로 이동하여 계속합니다.

    ![혼합 모드 디버거 기호 프롬프트](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>기호 다운로드

- Python 3.5 이상: Python 설치 관리자를 통해 디버그 기호를 가져옵니다. **사용자 지정 설치**를 선택하고 **다음**을 선택하여 **고급 옵션**으로 이동한 다음, **디버깅 기호 다운로드** 및 **디버그 버전의 이진 파일 다운로드** 상자를 선택합니다.

    ![디버그 기호를 포함한 Python 3.x 설치 관리자](media/mixed-mode-debugging-symbols-installer35.png)

    기호 파일( *.pdb*)은 루트 설치 폴더에 있습니다(개별 모듈에 대한 기호 파일도 *DLLs* 폴더에 있음). 따라서 Visual Studio는 자동으로 해당 기호 파일을 찾으므로 추가 단계가 필요하지 않습니다.

- Python 3.4.x 이전 버전: 기호는 [공식 배포](#official-distributions) 또는 [Enthought Canopy](#enthought-canopy)에서 다운로드 가능한 *.zip* 파일로 제공됩니다. 다운로드한 후에 로컬 폴더(예: Python 폴더 내의 *Symbols* 폴더)에 파일의 압축을 풀어 계속합니다.

    > [!Important]
    > 기호는 Python의 부 빌드 간에 다르고 32비트 빌드와 64비트 빌드 간에도 다르므로 버전을 정확하게 일치시키고자 할 수 있습니다. 사용 중인 인터프리터를 확인하려면 **솔루션 탐색기**의 프로젝트 아래에서 **Python 환경** *노드*를 확장하고 환경 이름을 확인합니다. 그런 다음 **Python 환경** *창*으로 전환하여 설치 위치를 확인합니다. 그런 다음, 해당 위치에서 명령 창을 열고 *python.exe*를 시작합니다. 그러면 정확한 버전과 32비트인지, 64비트인지 표시됩니다.

- ActiveState Python과 같은 타사 Python 배포의 경우: 해당 배포 작성자에게 문의하여 기호를 제공하도록 요청합니다. 그러나 WinPython은 자체로서는 표준 Python 인터프리터를 변경하지 않고 통합하므로 해당 버전 번호에 대한 공식 배포의 기호를 사용합니다.

## <a name="point-visual-studio-to-the-symbols"></a>Visual Studio가 기호를 가리키도록 하기

기호를 별도로 다운로드한 경우 아래 단계에 따라 Visual Studio가 이 사실을 인지하도록 합니다. Python 3.5 또는 이후 설치 관리자를 통해 기호를 설치한 경우 Visual Studio에서 자동으로 해당 기호를 찾습니다.

1. **도구** > **옵션** 메뉴를 선택하고 **디버깅** > **기호**로 이동합니다.

1. 도구 모음에서 **추가** 단추를 선택하고(아래에 설명되어 있음) 다운로드한 기호를 확장한 폴더(*python.pdb*가 있는 위치, 예: 아래에 표시된 *c:\python34\Symbols*)를 입력하고 **확인**을 선택합니다.

    ![혼합 모드 디버거 기호 옵션](media/mixed-mode-debugging-symbols.png)

1. 디버깅 세션 중에 Visual Studio에서 Python 인터프리터의 소스 파일 위치를 묻는 메시지를 표시할 수 있습니다. 소스 파일을 다운로드한 경우(예: [python.org/downloads/](https://www.python.org/downloads/)에서) 해당 위치도 가리킬 수 있습니다.

> [!Note]
> 대화 상자에 표시된 기호 캐싱 기능은 온라인 소스에서 가져온 기호의 로컬 캐시를 만드는 데 사용됩니다. 이미 로컬에 있는 Python 인터프리터 기호에는 이러한 기능이 필요하지 않습니다. 어느 경우이든 자세한 내용은 [Visual Studio 디버거에서 기호 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

## <a name="official-distributions"></a>공식 배포

| Python 버전 | 다운로드 |
| --- | --- |
| 3.5 이상 | Python 설치 관리자를 통해 기호를 설치하세요. |
| 3.4.4 | [32비트](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32비트](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32비트](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32비트](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32비트](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32비트](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32비트](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32비트](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32비트](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32비트](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32비트](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64비트](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32비트](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32비트](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32비트](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32비트](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32비트](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32비트](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32비트](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32비트](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32비트](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32비트](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32비트](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32비트](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32비트](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32비트](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32비트](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64비트](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy는 버전 1.2 버전에서 시작하는 이진 파일에 대한 기호를 제공합니다. 배포와 함께 자동으로 설치되지만, 앞에서 설명한 대로 여전히 기호가 포함된 폴더를 기호 경로에 수동으로 추가해야 합니다. Canopy의 일반적인 사용자별 설치에서 기호는 64비트 버전의 경우 *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts*에 위치하고, 32비트 버전의 경우 *%UserProfile%\AppData\Local\Enthought\ Canopy32\User\Scripts*에 위치합니다.

Enthought Canopy 1.1 및 이전 버전과 EPD(Enthought Python Distribution)는 인터프리터 기호를 제공하지 않으므로 혼합 모드 디버깅과 호환되지 않습니다.

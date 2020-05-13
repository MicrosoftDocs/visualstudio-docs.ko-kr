---
title: Requirements.txt 파일을 사용하여 패키지 종속성 관리
description: requirements.txt 파일은 프로젝트의 종속성을 설명합니다. requirements.txt 파일이 포함된 프로젝트를 수신하는 경우 해당 종속성을 한 단계로 쉽게 설치할 수 있습니다.
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a1853df63354801ebf0413d3c8707135cb9bb800
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62535725"
---
# <a name="manage-required-packages-with-requirementstxt"></a>requirements.txt를 사용하여 필수 패키지 관리

빌드 시스템을 사용하여 다른 사람과 프로젝트를 공유하거나 환경을 복원해야 하는 다른 위치에 프로젝트를 복사하려는 경우 프로젝트에 필요한 외부 패키지를 지정해야 합니다. 권장되는 방법은 필요한 종속 패키지 버전을 설치하는 pip 명령 목록이 들어 있는 [requirements.txt 파일](https://pip.readthedocs.org/en/latest/user_guide.html#requirements-files)(readthedocs.org)을 사용하는 것입니다. 가장 일반적인 명령은 `pip freeze > requirements.txt`이며, 이 명령은 환경의 현재 패키지 목록을 *requirements.txt*에 기록합니다.

기술적으로, 파일 이름을 사용하여 요구 사항을 추적할 수 있으나(패키지 설치 시 `-r <full path to file>` 사용) Visual Studio에서 *requirements.txt*에 대한 구체적인 지원을 제공합니다.

- *requirements.txt*가 포함된 프로젝트를 로드하여 이 파일에 나열된 모든 패키지를 설치하려면 **솔루션 탐색기**에서 **Python 환경** 노드를 확장하고 환경 노드를 마우스 오른쪽 단추로 클릭한 다음, **requirements.txt에서 설치**를 선택합니다.

    ![requirements.txt에서 설치](media/environments/environments-requirements-txt-install.png)

- 가상 환경에 종속성을 설치하려면 먼저 해당 환경을 만들어 활성화한 후 **requirements.txt에서 설치** 명령을 사용합니다. 가상 환경 만들기에 대한 자세한 내용은 [가상 환경 사용](selecting-a-python-environment-for-a-project.md#use-virtual-environments)을 참조하세요.

- 필요한 모든 패키지를 이미 한 환경에 설치한 경우 **솔루션 탐색기**에서 해당 환경을 마우스 오른쪽 단추로 클릭하고 **requirements.txt 생성**을 선택하여 필요한 파일을 만듭니다. 파일이 이미 있는 경우 업데이트 방법을 묻는 메시지가 표시됩니다.

    ![requirements.txt 옵션 업데이트](media/environments/environments-requirements-txt-replace.png)

  - **전체 파일 바꾸기**는 존재하는 모든 항목, 주석 및 옵션이 제거됩니다.
  - **기존 항목 새로 고침**은 패키지 요구 사항을 검색하고 버전 지정자를 현재 설치된 버전에 맞게 업데이트합니다.
  - **항목 업데이트 및 추가**는 확인된 요구 사항을 새로 고치고 모든 다른 패키지를 파일 끝에 추가합니다.

*requirements.txt* 파일은 환경의 요구 사항을 동결하기 위해 작성된 것이므로 모든 설치된 패키지가 정확한 버전으로 작성됩니다. 정확한 버전을 사용하면 다른 컴퓨터에서 사용자 환경을 쉽게 재현할 수 있습니다. 패키지는 다른 패키지의 종속성으로 버전 범위로 되거나 pip 이외의 설치 관리자로 설치된 경우에도 포함됩니다.

pip로 패키지를 설치할 수 없고 *requirements.txt* 파일에 나타나는 경우 전체 설치에 실패합니다. 이 경우 이 패키지를 제외하도록 수동으로 파일을 편집하거나 패키지의 설치 가능한 버전을 참조하도록 [pip의 옵션](https://pip.readthedocs.org/en/latest/reference/pip_install.html#requirements-file-format)을 사용합니다. 예를 들어 [`pip wheel`](https://pip.readthedocs.org/en/latest/reference/pip_wheel.html)을 사용하여 종속성을 컴파일하고 `--find-links <path>` 옵션을 사용자의 *requirements.txt*에 추가하는 것이 좋습니다.

```output
C:\Project>pip wheel azure
Downloading/unpacking azure
    Running setup.py (path:C:\Project\env\build\azure\setup.py) egg_info for package azure

Building wheels for collected packages: azure
    Running setup.py bdist_wheel for azure
    Destination directory: c:\project\wheelhouse
Successfully built azure
Cleaning up...

C:\Project>type requirements.txt
--find-links wheelhouse
--no-index
azure==0.8.0

C:\Project>pip install -r requirements.txt -v
Downloading/unpacking azure==0.8.0 (from -r requirements.txt (line 3))
    Local files found: C:/Project/wheelhouse/azure-0.8.0-py3-none-any.whl
Installing collected packages: azure
Successfully installed azure
Cleaning up...
    Removing temporary dir C:\Project\env\build...
```

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 Python 환경 관리](managing-python-environments-in-visual-studio.md)
- [프로젝트의 인터프리터 선택](selecting-a-python-environment-for-a-project.md)
- [검색 경로](search-paths.md)
- [Python 환경 창 참조](python-environments-window-tab-reference.md)

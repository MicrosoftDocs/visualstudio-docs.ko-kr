---
title: 컨테이너에 대한 알려진 문제
description: Windows 컨테이너에 Visual Studio Build Tools를 설치할 경우 발생할 수 있는 알려진 문제에 대해 자세히 알아봅니다.
ms.date: 02/18/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a864f1ef623197a44c7d816b051efd0106e86ece
ms.sourcegitcommit: b873fce7ba40d825fcb59555360c002bbfcecd9e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77611135"
---
# <a name="known-issues-for-containers"></a>컨테이너에 대한 알려진 문제

Visual Studio를 Docker 컨테이너에 설치하는 데 몇 가지 문제가 있습니다.

## <a name="windows-container"></a>Windows 컨테이너

다음 알려진 문제는 Windows 컨테이너에 Visual Studio Build Tools를 설치할 경우 발생합니다.

::: moniker range="vs-2017"

* 이미지 microsoft/windowsservercore:10.0.14393.1593에 기반한 컨터이너에는 Visual Studio를 설치할 수 없습니다. 10.0.14393 이전 또는 이후 Windows 버전으로 태그가 지정된 이미지가 작동해야 합니다.

* Windows SDK 버전 10.0.14393 또는 이전 버전을 설치할 수 없습니다. 특정 패키지는 설치되지 않으며 이러한 패키지에 종속된 워크로드는 작동하지 않습니다.

::: moniker-end

* 이미지 빌드 시 `-m 2GB`(또는 이상)를 전달합니다. 일부 워크로드는 설치 시 기본 1GB 이상의 메모리가 필요합니다.
* 기본값 20GB보다 큰 디스크를 사용하도록 Docker를 구성합니다.
* 명령줄에서 `--norestart`를 전달합니다. 이 문서 작성 당시, 컨테이너 내부에서 Windows 컨테이너를 다시 시작하려면 `ERROR_TOO_MANY_OPEN_FILES`가 호스트여야 합니다.
* microsoft/windowsservercore에 이미지를 직접 베이스하는 경우 .NET Framework는 제대로 설치되지 않을 수 있으며 설치 오류가 표시되지 않습니다. 관리 코드는 설치가 완료된 후 실행되지 않을 수 있습니다. 대신, [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) 이상에서 이미지를 베이스합니다. 예를 들어 다음과 유사한 MSBuild로 빌드할 때 오류가 표시될 수 있습니다.

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): 오류 MSB6003: 지정된 작업 실행 파일 "csc.exe"를 실행할 수 없습니다. 파일이나 어셈블리 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' 또는 여기에 종속되어 있는 파일이나 어셈블리 중 하나를 로드할 수 없습니다. 지정한 파일을 찾을 수 없습니다.

::: moniker range="vs-2017"

* mcr.microsoft.com/windows/servercore:1809 이상에는 Visual Studio 2017 버전 15.8 또는 이전 버전(모든 제품)을 설치할 수 없습니다. 자세한 내용은 https://aka.ms/setup/containers/servercore1809 를 참조하세요.

::: moniker-end

## <a name="build-tools-container"></a>빌드 도구 컨테이너

빌드 도구 컨테이너를 사용하는 경우 다음과 같은 알려진 문제가 발생할 수 있습니다. 문제가 해결되었는지 또는 다른 알려진 문제가 있는지 확인하려면 [https://developercommunity.visualstudio.com](https://developercommunity.visualstudio.com )에 방문하세요.

* IntelliTrace는 컨테이너 내의 [일부 시나리오](https://github.com/Microsoft/vstest/issues/940)에서 작동하지 않을 수 있습니다.
* 이전 버전의 Windows용 Docker에서는 기본 컨테이너 이미지가 20GB 뿐이므로 빌드 도구에 맞지 않습니다. [이미지 크기 변경 지침](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits)에 따라 127GB 이상으로 확장하세요.
디스크 공간 문제를 확인하려면 로그 파일에서 자세한 내용을 확인하세요. 디스크 공간이 부족한 경우 `vslogs\dd_setup_<timestamp>_errors.log` 파일에 다음이 포함됩니다. 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [Build Tools를 컨테이너에 설치](build-tools-container.md)
* [고급 컨테이너 예제](advanced-build-tools-container.md)
* [Visual Studio Build Tools 워크로드 및 구성 요소 ID](workload-component-id-vs-build-tools.md)

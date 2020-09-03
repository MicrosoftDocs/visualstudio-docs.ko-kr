---
title: 확장 찾기 및 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: df6219a66b0f6c85e197b209741706abc7ce3d06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655871"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Visual Studio 확장명 찾기 및 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 확장은 Visual Studio 내에서 실행되고 새로운 기능 또는 향상된 Visual Studio 기능을 제공하는 코드 패키지입니다. Visual Studio 확장에 대한 자세한 정보는 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)에서 찾을 수 있습니다.

 **확장 및 업데이트** 대화 상자를 사용하여 웹 사이트 및 다른 위치에서 Visual Studio 확장과 샘플을 설치를 할 수 있으며 사용, 사용 안 함, 업데이트 또는 제거를 할 수 있습니다. (**도구/확장 및 업데이트**또는 **빠른 실행** 창에 **확장** 을 입력 합니다.) 대화 상자에는 설치된 샘플 및 확장의 업데이트도 표시됩니다. 확장을 웹 사이트에서 다운로드하거나 다른 개발자에게서 얻을 수도 있습니다.

> [!NOTE]
> Visual Studio 2015부터 Visual Studio 갤러리에서 호스트된 확장이 자동으로 업데이트됩니다.  **확장 및 업데이트** 대화 상자를 통해 이 설정을 변경할 수 있습니다.  자세한 내용은 아래에서 **자동 확장 업데이트** 에 대한 단원을 참조하세요.

## <a name="finding-visual-studio-extensions"></a>Visual Studio 확장 찾기
 Microsoft 웹 사이트의 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 또는 [샘플 갤러리](https://code.msdn.microsoft.com/vstudio) 에서 확장을 설치할 수 있습니다. 확장은 Visual Studio에 기능을 추가하는 제어, 샘플, 템플릿 또는 기타 구성 요소일 수 있습니다. Visual Studio는 VSIX 패키지 형식에서 프로젝트 템플릿, 항목 템플릿, **도구 상자** 항목, MEF(Managed Extension Framework) 구성 요소 및 VSPackage 등의 확장을 지원합니다. MSI 기반 확장도 다운로드하고 설치할 수 있지만 **확장 및 업데이트** 대화 상자에서 해당 확장을 사용하거나 사용하지 않도록 설정할 수 없습니다. Visual Studio 갤러리에는 VSIX 및 MSI 확장이 모두 포함되어 있습니다.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Visual Studio 확장 설치 또는 제거
 **확장 및 업데이트**에서 설치하려는 확장을 찾습니다. 확장명의 이름 또는 일부를 알고 있는 경우 **Visual Studio 갤러리 검색** 창에서 검색할 수 있습니다. **다운로드**, **설치**를 차례로 클릭 합니다. 확장을 로드하려면 Visual Studio를 다시 시작해야 합니다.

 종속성이 포함된 확장을 설치하려고 하면 설치 관리자에서 이미 설치가 되었는지 여부를 확인합니다. 설치가 되어 있지 않으면, **확장 및 업데이트** 대화 상자 목록은 확장을 설치하기 전에 설치해야 하는 종속성을 나열합니다.

 확장의 사용을 중지하려는 경우 사용하지 않도록 설정하거나 제거합니다. 확장을 사용하지 않으면 설치되어 있지만 로드되지 않습니다. VSIX 확장만 사용하지 않도록 설정할 수 있습니다. MSI를 사용하여 설치된 확장만 제거할 수 있습니다. 확장을 찾고 **제거** 또는 **사용 안 함**을 클릭합니다. 사용하지 않도록 설정된 확장을 언로드하려면 Visual Studio를 다시 시작해야 합니다.

## <a name="per-user-and-administrative-extensions"></a>사용자별 및 관리 확장
 대부분의 확장은 **%LocalAppData%\Microsoft\VisualStudio\\<Visual Studio 버전\>\Extensions\\** 폴더에 설치된 사용자별 확장입니다. 몇 가지 확장은 관리 확장 이며 ** \<Visual Studio installation folder> \Common7\IDE\Extensions \\ ** 폴더에 설치 됩니다.

 오류 또는 악의적인 코드를 포함할 수 있는 확장으로부터 시스템을 보호하기 위해, Visual Studio가 일반 사용자 권한으로 실행되는 경우에만 로드되도록 사용자별 확장을 제한할 수 있습니다. 이는 Visual Studio가 관리자 권한으로 실행되는 경우에는 사용자별 확장을 사용하지 않도록 설정됨을 의미합니다. 이 작업을 수행하려면 **확장 및 업데이트** 옵션 페이지로 이동합니다(**도구 / 옵션**, **환경**, **확장 및 업데이트**로 이동하거나 **빠른 실행** 창에서 **확장** 을 입력함). **관리자로 실행할 때 사용자 확장별 로드** 확인란을 선택 취소한 다음 Visual Studio를 다시 시작합니다.

## <a name="automatic-extension-updates"></a>자동 확장 업데이트
 Visual Studio 갤러리에서 새 버전을 사용할 수 있으면 사용자 단위 확장이 자동으로 업데이트됩니다.  새 버전의 확장이 검색되어 백그라운드로 설치되면 다음에 Visual Studio를 다시 시작할 때 새 버전의 확장이 실행됩니다.

 사용자 단위 확장만 자동으로 업데이트됩니다.  모든 사용자에 대해 설치되는 관리 확장은 업데이트되지 않으므로 새 버전을 계속 **확장 및 업데이트** 대화 상자 **업데이트** 노드를 통해 수동으로 설치합니다. **확장 및 업데이트** 대화 상자의 확장 세부 정보 창에서 자동으로 업데이트되는 확장을 볼 수 있습니다.

 자동 업데이트를 사용하지 않도록 설정하려는 경우 해당 기능을 모든 확장에 대해 사용하지 않도록 설정할 수도 있고 특정 확장에 대해서만 사용하지 않도록 설정할 수도 있습니다.

- 모든 확장에 대해 자동 업데이트를 사용하지 않도록 설정하려면 **확장 및 업데이트** 대화 상자에서 **확장 및 업데이트 설정 변경** 을 클릭하고 **자동으로 확장 업데이트**의 선택을 취소합니다.

- 특정 확장에 대해 자동 업데이트를 사용하지 않도록 설정하려면 **확장 및 업데이트** 대화 상자 오른쪽에 있는 확장 세부 정보 창에서 **자동으로 이 확장 업데이트** 의 선택을 취소합니다.

> [!NOTE]
> Visual Studio 2015 업데이트 2부터 사용자별 확장, 모든 사용자 확장 또는 둘 다 (기본 설정)에 대해 자동 업데이트를 사용할지 여부를 **도구/옵션/환경/확장 및 업데이트**에서 지정할 수 있습니다.

## <a name="sample-master-copies-and-working-copies"></a>샘플 마스터 복사본 및 작업 복사본
 온라인 샘플을 설치하면 솔루션은 다음 두 위치에 저장됩니다.

- 작업 복사본은 **새 프로젝트** 대화 상자에 지정된 위치에 저장됩니다.

- 별도의 마스터 복사본은 컴퓨터에 저장됩니다.

  **확장 및 업데이트** 대화 상자를 사용하여 이러한 샘플 관련 작업을 수행할 수 있습니다.

- 설치한 샘플의 마스터 복사본을 나열합니다.

- 샘플의 마스터 복사본을 사용하지 않거나 제거합니다.

- 기술이나 기능과 관련된 샘플의 모음인 샘플 팩을 설치합니다.

- 개별 온라인 샘플을 설치합니다. ( **새 프로젝트** 대화 상자에서도 할 수 있습니다.)

- 설치된 샘플에 대해 소스 코드 변경 내용이 게시되면 업데이트 알림을 봅니다.

- 업데이트 알림이 있는 경우 설치된 샘플의 마스터 복사본을 업데이트합니다.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>확장 및 업데이트 대화 상자를 사용하지 않고 설치
 .vsix 파일에 패키지된 확장은 Visual Studio Gallery 이외의 위치에서 사용될 수 있습니다. **확장명 및 업데이트** 대화 상자는 이러한 파일을 검색할 수 없지만, .vsix 파일을 두 번 클릭 하거나 파일을 선택 하 고 enter 키를 눌러 설치할 수 있습니다. 그런 다음, 지침을 따르세요. 확장이 설치되면 **확장 및 업데이트** 대화 상자를 사용하여 사용, 사용 안 함으로 설정하거나 제거할 수 있습니다.

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>확장 및 업데이트 대화 상자에서 지원되지 않는 확장 형식
 Visual Studio에서는 Microsoft Installer(MSI)에 의해 설치되는 확장은 계속 지원하지만 수정 없이 **확장 및 업데이트** 대화 상자를 통해 설치되는 확장은 지원하지 않습니다.

> [!TIP]
> MSI 기반 확장은 extension.vsixmanifest 파일을 포함하는 경우 **확장 및 업데이트** 대화 상자에 나타납니다.

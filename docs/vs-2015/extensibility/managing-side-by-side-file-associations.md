---
title: Side-by-side 파일 연결 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b8ca68aec180c51a170fd6ecce58237a5b306705
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194386"
---
# <a name="managing-side-by-side-file-associations"></a>병렬 파일 연결 관리

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage에서 파일 연결을 제공 하는 경우 파일을 열기 위해 특정 버전의를 호출 해야 하는 side-by-side 설치를 처리 하는 방법을 결정 해야 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 호환 되지 않는 파일 형식이 문제의 조합입니다.

사용자는 새 버전의 제품이 이전 버전과 호환 될 것으로 간주 하므로 데이터가 손실 되지 않고 새 버전으로 기존 파일을 로드할 수 있습니다. 이상적으로 VSPackage는 이전 버전의 파일 형식을 로드 하 고 저장할 수 있습니다. 그렇지 않은 경우을 (를) 제공 하 여 파일 형식을 VSPackage의 새 버전으로 업그레이드 해야 합니다. 이 방법의 단점은 업그레이드 된 파일을 이전 버전에서 열 수 없다는 것입니다.

이 문제를 방지 하기 위해 파일 형식이 호환 되지 않을 때 확장을 변경할 수 있습니다. 예를 들어 VSPackage의 버전 1은 mypkg10 확장을 사용할 수 있으며, 버전 2는 mypkg20 확장명을 사용할 수 있습니다. 이 차이는 특정 파일을 여는 VSPackage을 식별 합니다. 이전 확장과 연결 된 프로그램 목록에 최신 Vspackage를 추가 하는 경우 사용자가 파일을 마우스 오른쪽 단추로 클릭 하 고 최신 VSPackage에서 열도록 선택할 수 있습니다. 이 시점에서 VSPackage은 파일을 새 형식으로 업그레이드 하거나 파일을 열고 이전 버전의 VSPackage와의 호환성을 유지 하도록 제공할 수 있습니다.

> [!NOTE]
> 이러한 방법을 결합할 수 있습니다. 예를 들어 이전 파일을 로드 하 여 이전 버전과의 호환성을 제공 하 고, 사용자가 파일을 저장할 때 파일 형식을 업그레이드 하도록 제공할 수 있습니다.

## <a name="facing-the-problem"></a>문제 발생

여러 side-by-side Vspackage가 동일한 확장명을 사용 하도록 하려면 확장과 연결 된 버전을 선택 해야 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 다음은 두 가지 대안입니다.

- 사용자의 컴퓨터에 설치 된 최신 버전의에서 파일을 엽니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

   이 방법에서는 설치 관리자가 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 파일 연결을 위해 작성 된 레지스트리 항목에 포함 된 최신 버전을 확인 해야 합니다. Windows Installer 패키지에서 사용자 지정 작업을 포함 하 여 최신 버전의를 나타내는 속성을 설정할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

  > [!NOTE]
  > 이 컨텍스트에서 "최신"은 "지원 되는 최신 버전"을 의미 합니다. 이러한 설치 관리자 항목은의 후속 릴리스를 자동으로 감지 하지 않습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . [시스템 요구 사항](../extensibility/internals/detecting-system-requirements.md) 및 [설치 후 실행 해야 하는 명령을](../extensibility/internals/commands-that-must-be-run-after-installation.md) 검색 하는 항목은 여기에 제시 된 것과 비슷하며,의 추가 버전을 지 원하는 데 필요 합니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

   CustomAction 테이블의 다음 행은 [설치 후 실행 해야 하는 명령](../extensibility/internals/commands-that-must-be-run-after-installation.md)에 설명 된 appsearch 및 reglocator 테이블에 의해 설정 된 속성으로 DEVENV_EXE_LATEST 속성을 설정 합니다. InstallExecuteSequence 테이블의 행은 실행 시퀀스의 초기에 사용자 지정 작업을 예약 합니다. 조건 열의 값은 논리 작업을 수행 합니다.

  - 최신 버전인 경우 Visual Studio .NET 2002이 최신 버전입니다.

  - Visual Studio .NET 2003은 있는 경우에만 최신 버전이 며 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 존재 하지 않습니다.

  - [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 현재 버전이 면 최신 버전입니다.

    결과적으로 DEVENV_EXE_LATEST에는 최신 버전의 devenv.exe 경로가 포함 됩니다.

  **최신 버전의 Visual Studio를 결정 하는 테이블 행 CustomAction**

  |작업|형식|원본|대상|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **최신 버전의 Visual Studio를 결정 하는 InstallExecuteSequence 테이블 행**

  |작업|조건|순서|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 (DEVENV_EXE_2003 또는 DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Windows Installer 패키지의 레지스트리 테이블에서 DEVENV_EXE_LATEST 속성을 사용 하 여 HKEY_CLASSES_ROOT*ProgId*ShellOpenCommand 키의 기본값, [DEVENV_EXE_LATEST] "%1"을 (를) 쓸 수 있습니다.

- 사용 가능한 VSPackage 버전에서 가장 적합 한 옵션을 선택할 수 있는 공유 시작 관리자 프로그램을 실행 합니다.

   개발자는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이 접근 방식을 선택 하 여 여러 버전의에서 생성 되는 여러 형식의 솔루션 및 프로젝트에 대 한 복잡 한 요구 사항을 처리 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 했습니다. 이 방법에서는 시작 관리자 프로그램을 확장 처리기로 등록 합니다. 시작 관리자는 파일을 검사 하 고 VSPackage에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 해당 특정 파일을 처리할 수 있는 버전을 결정 합니다. 예를 들어 사용자가 특정 버전의 VSPackage에서 마지막으로 저장 한 파일을 여는 경우 시작 관리자는 일치 하는 버전의에서 해당 VSPackage를 시작할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 또한 사용자는 항상 최신 버전을 시작 하도록 시작 관리자를 구성할 수 있습니다. 또한 시작 관리자는 사용자에 게 파일 형식을 업그레이드할지 묻는 메시지를 표시할 수 있습니다. 파일 형식에 버전 번호가 포함 되어 있는 경우 설치 관리자에서 파일 형식이 설치 된 Vspackage 중 하나 이상에 해당 하는 버전의 파일 인지 여부를 사용자에 게 알릴 수 있습니다.

   시작 관리자는 VSPackage의 모든 버전에서 공유 되는 Windows Installer 구성 요소에 있어야 합니다. 이 프로세스를 통해 최신 버전이 항상 설치 되 고 VSPackage의 모든 버전이 제거 될 때까지 제거 되지 않습니다. 이러한 방식으로 VSPackage의 한 버전을 제거 하더라도 시작 관리자 구성 요소의 파일 연결 및 기타 레지스트리 항목은 유지 됩니다.

## <a name="uninstall-and-file-associations"></a>제거 및 파일 연결

파일 연결에 대 한 레지스트리 항목을 기록 하는 VSPackage을 제거 하면 파일 연결이 제거 됩니다. 따라서 확장에는 연결 된 프로그램이 없습니다. Windows Installer는 VSPackage가 설치 될 때 추가 된 레지스트리 항목을 "복구" 하지 않습니다. 사용자의 파일 연결을 수정 하는 몇 가지 방법은 다음과 같습니다.

- 앞에서 설명한 대로 공유 시작 관리자 구성 요소를 사용 합니다.

- 사용자가 파일 연결을 소유 하려는 VSPackage 버전의 복구를 실행 하도록 사용자에 게 지시 합니다.

- 적절 한 레지스트리 항목을 다시 작성 하는 별도의 실행 프로그램을 제공 합니다.

- 사용자가 파일 연결을 선택 하 고 손실 된 연결을 회수할 수 있는 구성 옵션 페이지 또는 대화 상자를 제공 합니다. 제거 후 사용자에 게 실행 하도록 지시 합니다.

## <a name="see-also"></a>관련 항목

[Side-by-side 배포](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) 
 를 위한 파일 이름 확장명 등록 [파일 이름 확장명에 대 한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md)

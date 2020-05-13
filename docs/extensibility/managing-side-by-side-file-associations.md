---
title: 나란히 파일 연결 관리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702755"
---
# <a name="manage-side-by-side-file-associations"></a>나란히 파일 연결 관리

VSPackage파일 연결을 제공하는 경우 파일을 열려면 특정 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 설치를 호출해야 하는 병렬 설치를 처리하는 방법을 결정해야 합니다. 호환되지 않는 파일 형식이 문제를 복잡하게 합니다.

사용자는 새 버전의 제품이 이전 버전과 호환되기를 기대하므로 데이터를 잃지 않고 기존 파일을 새 버전으로 로드할 수 있습니다. 이상적으로 는 VSPackage 로드 하 고 이전 버전의 파일 형식을 저장할 수 있습니다. 그렇지 않은 경우 파일 형식을 VSPackage의 새 버전으로 업그레이드해야 합니다. 이 방법의 단점은 업그레이드된 파일을 이전 버전에서 열 수 없다는 것입니다.

이 문제를 방지하려면 파일 형식이 호환되지 않는 경우 확장프로그램을 변경할 수 있습니다. 예를 들어 VSPackage의 버전 1은 확장인 *.mypkg10을*사용할 수 있으며 버전 2는 확장인 *.mypkg20을*사용할 수 있습니다. 이 차이는 특정 파일을 여는 VSPackage를 식별합니다. 이전 확장명과 연결된 프로그램 목록에 최신 VSPackage를 추가하는 경우 사용자는 파일을 마우스 오른쪽 단추로 클릭하고 최신 VSPackage에서 열도록 선택할 수 있습니다. 이 시점에서 VSPackage는 파일을 새 형식으로 업그레이드하거나 파일을 열고 이전 버전의 VSPackage와의 호환성을 유지하도록 제안할 수 있습니다.

> [!NOTE]
> 이러한 방법을 결합할 수 있습니다. 예를 들어 이전 파일을 로드하여 이전 버전과의 호환성을 제공하고 사용자가 파일을 저장할 때 파일 형식을 업그레이드하도록 제안할 수 있습니다.

## <a name="face-the-problem"></a>문제 해결

여러 개의 나란히 VSPackage가 동일한 확장을 사용하려면 확장과 연결된 버전을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 선택해야 합니다. 다음은 두 가지 대안입니다.

- 사용자의 컴퓨터에 설치된 최신 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 버전의 파일을 엽니다.

   이 방법에서 설치 관리자는 파일 연결을 위해 작성된 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 레지스트리 항목에 최신 버전을 포함하여 최신 버전을 결정할 책임이 있습니다. Windows 설치 관리자 패키지에 최신 버전을 나타내는 속성을 설정하는 사용자 지정 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]작업을 포함할 수 있습니다.

  > [!NOTE]
  > 이 컨텍스트에서 "최신"은 "최신 지원 버전"을 의미합니다. 이러한 설치 관리자 항목은 의 후속 릴리스를 자동으로 검색하지 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]않습니다. 시스템 [요구 사항 검색](../extensibility/internals/detecting-system-requirements.md) 및 [설치 후 실행해야 하는 명령의](../extensibility/internals/commands-that-must-be-run-after-installation.md) 항목은 여기에 제시된 항목과 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]유사하며 추가 버전의 을 지원하는 데 필요합니다.

   CustomAction 테이블의 다음 행은 설치 [후 실행해야 하는 명령에서](../extensibility/internals/commands-that-must-be-run-after-installation.md)설명하는 AppSearch 및 RegLocator 테이블에서 설정한 속성으로 DEVENV_EXE_LATEST 속성을 설정합니다. InstallExecuteSequence 테이블의 행은 실행 시퀀스의 초기에 사용자 지정 작업을 예약합니다. 조건 열의 값은 논리를 작동시게 합니다.

  - Visual Studio .NET 2002는 현재 버전만 있는 최신 버전입니다.

  - Visual Studio .NET 2003은 현재 존재하고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 존재하지 않는 경우에만 최신 버전입니다.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]이 유일한 현재 버전인 경우 최신 버전입니다.

    그 결과 DEVENV_EXE_LATEST devenv.exe의 최신 버전의 경로를 포함합니다.

  **Visual Studio의 최신 버전을 결정하는 사용자 지정 작업 테이블 행**

  |작업|형식|원본|대상|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|【DEVENV_EXE_2002】|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|【DEVENV_EXE_2003】|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|【DEVENV_EXE_2005】|

  **설치ExecuteSequence 비주얼 스튜디오의 최신 버전을 결정 하는 테이블 행**

  |작업|조건|시퀀스|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 및 하지 (DEVENV_EXE_2003 또는 DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 AND NOT DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   Windows Installer 패키지의 레지스트리 테이블에서 DEVENV_EXE_LATEST 속성을 사용하여 ***ProgId*ShellOpenCommand** 키의 기본값인 [DEVENV_EXE_LATEST] "%1"을 HKEY_CLASSES_ROOT 작성할 수 있습니다.

- 사용 가능한 VSPackage 버전에서 최상의 선택을 할 수 있는 공유 런처 프로그램을 실행합니다.

   개발자는 여러 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 발생하는 여러 형식의 솔루션 및 프로젝트의 복잡한 요구 사항을 처리하기 위해 이 방법을 선택했습니다. 이 방법에서는 런처 프로그램을 확장 처리기로 등록합니다. 런처는 파일을 검사하고 VSPackage가 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 해당 특정 파일을 처리할 수 있는 버전과 버전을 결정합니다. 예를 들어 사용자가 VSPackage의 특정 버전에서 마지막으로 저장한 파일을 여는 경우 런처는 해당 VSPackage를 일치 하는 버전에서 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]시작할 수 있습니다. 또한 사용자는 항상 최신 버전을 시작하도록 런처를 구성할 수 있습니다. 또한 런처는 사용자에게 파일 형식을 업그레이드하라는 메시지를 표시할 수도 있습니다. 파일 형식에 버전 번호가 포함된 경우 실행 프로그램은 설치된 VSPackage 중 하나 이상 인 버전에서 파일 형식인 경우 사용자에게 알릴 수 있습니다.

   런처는 VSPackage의 모든 버전과 공유되는 Windows 설치 관리자 구성 요소에 있어야 합니다. 이 프로세스를 통해 VSPackage의 모든 버전이 제거될 때까지 최신 버전이 항상 설치되고 제거되지 않습니다. 이러한 방식으로 VSPackage의 한 버전이 제거된 경우에도 실행 프로그램 구성 요소의 파일 연결 및 기타 레지스트리 항목이 유지됩니다.

## <a name="uninstall-and-file-associations"></a>제거 및 파일 연결

파일 연결에 대한 레지스트리 항목을 작성하는 VSPackage를 제거하면 파일 연결이 제거됩니다. 따라서 확장에는 연결된 프로그램이 없습니다. WINDOWS 설치 관리자는 VSPackage를 설치할 때 추가된 레지스트리 항목을 "복구"하지 않습니다. 다음은 사용자의 파일 연결을 해결하는 몇 가지 방법입니다.

- 앞서 설명한 대로 공유 런처 구성 요소를 사용합니다.

- 사용자가 파일 연결을 소유하려는 VSPackage 버전의 복구를 실행하도록 사용자에게 지시합니다.

- 적절한 레지스트리 항목을 다시 작성하는 별도의 실행 프로그램을 제공합니다.

- 사용자가 파일 연결을 선택하고 손실된 연결을 회수할 수 있는 구성 옵션 페이지 또는 대화 상자를 제공합니다. 제거 한 후 실행 하도록 사용자를 지시 합니다.

## <a name="see-also"></a>참조

- [나란히 배포할 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [파일 이름 확장명에 대한 동사 등록](../extensibility/registering-verbs-for-file-name-extensions.md)

---
title: ClickOnce 배포의 보안/버전 관리/매니페스트 문제
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb2ec5229132265feb1095c9ee921d73a1568dd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66745599"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>ClickOnce 배포의 보안, 버전 관리 및 매니페스트 문제

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포에 성공 하지 못할 수 있는 보안, 응용 프로그램 버전 관리 및 매니페스트 구문과 의미 체계에는 여러 가지 문제가 있습니다.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce 및 Windows Vista 사용자 계정 컨트롤

에서 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] 현재 사용자가 관리자 권한이 있는 계정으로 로그인 하는 경우에도 기본적으로 응용 프로그램은 표준 사용자로 실행 됩니다. 응용 프로그램에서 관리자 권한이 필요한 작업을 수행 해야 하는 경우 운영 체제에서 사용자에 게 관리자 자격 증명을 입력 하 라는 메시지를 표시 합니다. UAC (사용자 계정 컨트롤) 라는이 기능을 사용 하면 응용 프로그램에서 사용자의 명시적인 승인 없이 전체 운영 체제에 영향을 줄 수 있는 변경 작업을 수행할 수 없습니다. Windows 응용 프로그램은 `requestedExecutionLevel` `trustInfo` 응용 프로그램 매니페스트의 섹션에서 특성을 지정 하 여이 권한 상승이 필요 함을 선언 합니다.

응용 프로그램이 보안 권한 상승 공격에 노출 될 위험이 있으므로 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 클라이언트에 대해 UAC를 사용 하도록 설정한 경우 응용 프로그램은 권한 상승을 요청할 수 없습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]특성을 또는로 설정 하려고 시도 하는 모든 응용 프로그램 `requestedExecutionLevel` `requireAdministrator` `highestAvailable` 은에 설치 되지 않습니다 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] .

일부 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에는의 설치 관리자 검색 논리로 인해 응용 프로그램이 관리자 권한으로 실행을 시도할 수 있습니다 [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] . 이 경우 `requestedExecutionLevel` 응용 프로그램 매니페스트의 특성을로 설정할 수 있습니다 `asInvoker` . 이렇게 하면 응용 프로그램 자체는 권한 상승을 제외 하 고 실행 됩니다. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 는이 특성을 모든 응용 프로그램 매니페스트에 자동으로 추가 합니다.

응용 프로그램의 전체 수명 동안 관리자 권한이 필요한 응용 프로그램을 개발 하는 경우에는 MSI (Windows Installer) 기술을 사용 하 여 응용 프로그램을 배포 하는 것이 좋습니다. 자세한 내용은 [Windows Installer 기본 사항](../extensibility/internals/windows-installer-basics.md)을 참조 하세요.

## <a name="online-application-quotas-and-partial-trust-applications"></a>온라인 응용 프로그램 할당량 및 부분 신뢰 응용 프로그램

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]응용 프로그램이 설치를 통하지 않고 온라인으로 실행 되는 경우에는 온라인 응용 프로그램에 대해 별도로 설정 된 할당량 내에 있어야 합니다. 또한 제한 된 보안 권한 집합을 사용 하는 경우와 같이 부분 신뢰로 실행 되는 네트워크 응용 프로그램은 할당량 크기의 절반 보다 클 수 없습니다.

자세한 내용 및 온라인 응용 프로그램 할당량을 변경 하는 방법에 대 한 지침은 [ClickOnce 캐시 개요](../deployment/clickonce-cache-overview.md)를 참조 하세요.

## <a name="versioning-issues"></a>버전 관리 문제

어셈블리에 강력한 이름을 할당 하 고 어셈블리 버전 번호를 증가 시켜 응용 프로그램 업데이트를 반영 하는 경우 문제가 발생할 수 있습니다. 강력한 이름의 어셈블리에 대 한 참조를 사용 하 여 컴파일된 모든 어셈블리는 자신을 다시 컴파일해야 합니다. 그렇지 않으면 어셈블리가 이전 버전을 참조 합니다. 어셈블리가 바인딩 요청에서 이전 버전 값을 사용 하 고 있기 때문에이를 시도 합니다.

예를 들어, 버전이 1.0.0.0 인 자체 프로젝트에 강력한 이름의 어셈블리가 있다고 가정 합니다. 어셈블리를 컴파일한 후에는 주 응용 프로그램을 포함 하는 프로젝트에 대 한 참조로 어셈블리를 추가 합니다. 어셈블리를 업데이트 하는 경우 버전을 1.0.0.1로 증분 하 고 응용 프로그램을 다시 컴파일하지 않고 배포 하면 응용 프로그램에서 런타임에 어셈블리를 로드할 수 없게 됩니다.

이 오류는 매니페스트를 수동으로 편집 하는 경우에만 발생할 수 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Visual Studio를 사용 하 여 배포를 생성 하는 경우이 오류가 발생 하지 않습니다.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>매니페스트에서 개별 .NET Framework 어셈블리를 지정 합니다.

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]이전 버전의 .NET Framework 어셈블리를 참조 하도록 배포를 수동으로 편집한 경우 응용 프로그램을 로드할 수 없습니다. 예를 들어, 매니페스트에 지정 된 버전 보다 이전 버전의 .NET Framework에 대 한 참조를 System.Net 어셈블리에 추가한 경우 오류가 발생 합니다. 일반적으로 응용 프로그램이 실행 되는 .NET Framework 버전이 응용 프로그램 매니페스트에서 종속성으로 지정 되므로 개별 .NET Framework 어셈블리에 대 한 참조를 지정 하지 않아야 합니다.

## <a name="manifest-parsing-issues"></a>매니페스트 구문 분석 문제

에서 사용 하는 매니페스트 파일은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] xml 파일이 며 올바른 형식 이어야 하 고 올바른 형식 이어야 합니다. 즉, xml 구문 규칙을 준수 해야 하며 관련 xml 스키마에 정의 된 요소와 특성만 사용 해야 합니다.

매니페스트 파일에서 문제를 일으킬 수 있는 작업은 단일 또는 큰따옴표와 같이 특수 문자를 포함 하는 응용 프로그램의 이름을 선택 하는 것입니다. 응용 프로그램의 이름은 id의 일부입니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서는 현재 특수 문자를 포함 하는 id를 구문 분석 하지 않습니다. 응용 프로그램을 활성화 하는 데 실패 한 경우 이름에 영문자 및 숫자만 사용 하 고 있는지 확인 하 고 다시 배포 해 보십시오.

배포 또는 응용 프로그램 매니페스트를 수동으로 편집한 경우 실수로 손상 했을 수 있습니다. 매니페스트가 손상 되 면 올바른 설치를 방지할 수 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 있습니다. **ClickOnce 오류** 대화 상자에서 **세부 정보** 를 클릭 하 고 로그의 오류 메시지를 읽으면 런타임에 이러한 오류를 디버그할 수 있습니다. 로그에 다음 메시지 중 하나가 나열 됩니다.

- 구문 오류에 대 한 설명 및 오류가 발생 한 줄 번호 및 문자 위치입니다.

- 매니페스트의 스키마를 위반 하는 데 사용 되는 요소나 특성의 이름입니다. 매니페스트에 XML을 수동으로 추가한 경우에는 추가 내용을 매니페스트 스키마와 비교 해야 합니다. 자세한 내용은 [clickonce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md) 및 [clickonce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)를 참조 하세요.

- ID가 충돌 합니다. 배포 및 응용 프로그램 매니페스트의 종속성 참조는 및 특성에서 모두 고유 해야 합니다 `name` `publicKeyToken` . 두 특성이 매니페스트 내의 두 요소 사이에 일치 하는 경우 매니페스트 구문 분석이 실패 합니다.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>매니페스트 또는 응용 프로그램을 수동으로 변경 하는 경우의 예방 조치

응용 프로그램 매니페스트를 업데이트 하는 경우 응용 프로그램 매니페스트와 배포 매니페스트 모두에 다시 서명 해야 합니다. 배포 매니페스트에는 해당 파일의 해시 및 해당 디지털 서명이 포함 된 응용 프로그램 매니페스트에 대 한 참조가 포함 되어 있습니다.

### <a name="precautions-with-deployment-provider-usage"></a>배포 공급자 사용 시 예방 조치

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]배포 매니페스트에는 `deploymentProvider` 응용 프로그램을 설치 하 고 서비스 해야 하는 위치의 전체 경로를 가리키는 속성이 있습니다.

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

이 경로는에서 응용 프로그램을 만들 때 설정 되며 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 설치 된 응용 프로그램에 강제 적용 됩니다. 경로는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 설치 관리자가 응용 프로그램을 설치 하 고 업데이트를 검색 하는 표준 위치를 가리킵니다. **Xcopy** 명령을 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 다른 위치에 복사 하지만 속성을 변경 하지 않는 경우는 `deploymentProvider` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 여전히 응용 프로그램 다운로드를 시도할 때 원래 위치를 다시 참조 합니다.

응용 프로그램을 이동 하거나 복사 하려면 `deploymentProvider` 클라이언트가 새 위치에서 실제로 설치 되도록 경로도 업데이트 해야 합니다. 응용 프로그램을 설치한 경우에는이 경로를 업데이트 하는 것이 주로 중요 합니다. 항상 원래 URL을 통해 시작 되는 온라인 응용 프로그램의 경우를 설정 하는 `deploymentProvider` 것은 선택 사항입니다. `deploymentProvider`이 설정 되 면이 설정이 적용 됩니다. 그렇지 않으면 응용 프로그램을 시작 하는 데 사용 되는 url이 응용 프로그램 파일을 다운로드 하는 기준 url로 사용 됩니다.

> [!NOTE]
> 매니페스트를 업데이트할 때마다 다시 서명 해야 합니다.

## <a name="see-also"></a>추가 정보

[ClickOnce 배포](../deployment/troubleshooting-clickonce-deployments.md) 
 문제 해결 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md) 
 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)

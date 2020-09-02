---
title: 여러 서비스 구성을 사용하여 Azure 프로젝트 구성 | Microsoft Docs
description: ServiceDefinition.csdef, ServiceConfiguration.Local.cscfg 및 ServiceConfiguration.Cloud.cscfg 파일을 변경하여 Azure 클라우드 서비스 프로젝트를 구성하는 방법에 대해 알아봅니다.
author: ghogen
manager: jillfra
assetId: a4fb79ed-384f-4183-9f74-5cac257206b9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 59996180661806eee60d18ab4b7b5fd26f4a2e7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89312745"
---
# <a name="configuring-your-azure-project-in-visual-studio-to-use-multiple-service-configurations"></a>여러 서비스 구성을 사용하여 Visual Studio에서 Azure 프로젝트 구성

Visual Studio의 Azure 클라우드 서비스 프로젝트에는 `ServiceDefinition.csdef`, `ServiceConfiguration.Local.cscfg` 및 `ServiceConfiguration.Cloud.cscfg`와 같은 세 개의 구성 파일이 포함되어 있습니다.

- `ServiceDefinition.csdef`는 클라우드 서비스 및 해당 역할의 요구 사항을 설명하고 모든 인스턴스에 적용되는 설정을 제공하기 위해 Azure에 배포됩니다. 설정은 Azure 서비스 호스팅 런타임 API를 사용하여 런타임에서 읽을 수 있습니다. 이 파일은 클라우드 서비스를 중지하는 경우에만 Azure에서 업데이트할 수 있습니다.
- `ServiceConfiguration.Local.cscfg` 및 `ServiceConfiguration.Cloud.cscfg`는 정의 파일의 설정에 대한 값을 제공하고, 각 역할에 대해 실행할 인스턴스 수를 지정합니다. “Local” 파일은 로컬 디버깅에 사용되는 값을 포함하고, “Cloud” 파일은 `ServiceConfiguration.cscfg`로 Azure에 배포되고 서버 환경에 대한 설정을 제공합니다. 클라우드 서비스가 Azure에서 실행되는 동안 이 파일을 업데이트할 수 있습니다.

구성 설정은 Visual Studio에서 해당 역할에 대한 속성 페이지를 사용하여 관리되고 수정됩니다(역할을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택하거나 역할을 두 번 클릭). 변경 내용은 **서비스 구성** 드롭다운에서 선택한 구성으로 지정될 수 있습니다. 웹 및 작업자 역할에 대한 속성은 다음 섹션에 설명된 것을 제외하고는 비슷합니다.

![VS_Solution_Explorer_Roles_Properties](./media/vs-azure-tools-multiple-services-project-configurations/IC784076.png)

서비스 정의 및 서비스 구성 파일의 기본 스키마에 대한 자세한 내용은 [.csdef XML 스키마](/azure/cloud-services/schema-csdef-file) 및 [.cscfg XML 스키마](/azure/cloud-services/schema-cscfg-file) 문서를 참조하세요. 서비스 구성에 대한 자세한 내용은 [Cloud Services 구성 방법](/azure/cloud-services/cloud-services-how-to-configure-portal)을 참조하세요.

## <a name="configuration-page"></a>구성 페이지

### <a name="service-configuration"></a>서비스 구성

변경 내용의 영향을 받는 `ServiceConfiguration.*.cscfg` 파일을 선택합니다. 기본적으로 로컬 및 클라우드 변형이 있으며, **관리...** 명령을 사용하여 구성 파일을 복사, 이름 바꾸기 및 제거할 수 있습니다. 이러한 파일은 클라우드 서비스 프로젝트에 추가되고 **솔루션 탐색기**에 표시됩니다. 그러나 이 컨트롤에서만 구성의 이름을 바꾸거나 제거할 수 있습니다.

### <a name="instances"></a>인스턴스

**인스턴스** 횟수 속성을 이 역할에 대해 서비스를 실행해야 하는 인스턴스 수로 설정합니다.

**VM 크기** 속성을 **매우 작음**, **작음**, **보통**, **큼** 또는 **매우 큼**으로 설정합니다.  자세한 내용은 [Cloud Services의 크기](/azure/cloud-services/cloud-services-sizes-specs)를 참조 하세요.

### <a name="startup-action-web-role-only"></a>시작 작업(웹 역할만)

디버깅을 시작할 때 Visual Studio가 HTTP 엔드포인트 또는 HTTPS 엔드포인트 또는 모두에 대한 웹 브라우저를 시작하도록 이 속성을 설정합니다.

**Https 끝점** 옵션은 사용자의 역할에 대 한 https 끝점을 이미 정의한 경우에만 사용할 수 있습니다. **엔드포인트** 속성 페이지에서 HTTPS 엔드포인트를 정의할 수 있습니다.

HTTPS 엔드포인트를 이미 추가한 경우, HTTPS 엔드포인트 옵션은 기본적으로 사용되고 HTTP 엔드포인트에 대한 브라우저 외에도 디버깅을 시작하면 Visual Studio에서 이 엔드포인트에 대한 브라우저를 시작합니다(둘 다 시작 옵션이 활성화되어 있다고 가정).

### <a name="diagnostics"></a>진단

기본적으로 웹 역할에 대한 진단이 사용됩니다. Azure 클라우드 서비스 프로젝트 및 스토리지 계정은 로컬 스토리지 에뮬레이터를 사용하도록 설정됩니다. Azure에 배포할 준비가 되면 대신 Azure Storage를 사용하도록 작성기 단추(**...**)를 선택할 수 있습니다. 요청 시 또는 자동으로 예약된 간격으로 스토리지 계정에 진단 데이터를 전송할 수 있습니다. Azure 진단에 대한 자세한 내용은 [Azure Cloud Services 및 Virtual Machines에서 진단 사용](/azure/cloud-services/cloud-services-dotnet-diagnostics)을 참조하세요.

## <a name="settings-page"></a>설정 페이지

**설정** 페이지에서 설정을 구성에 이름-값 쌍으로 추가할 수 있습니다. 역할에서 실행되는 코드는 [Azure 관리 라이브러리](/previous-versions/azure/dn602775(v=azure.11))에서 제공하는 클래스를 사용하여 런타임에서 구성 설정 값을 읽을 수 있습니다(특히 [GetConfigurationSettingValue](/previous-versions/azure/reference/ee772857(v=azure.100)) 메서드).

### <a name="configuring-a-connection-string-for-a-storage-account"></a>스토리지 계정에 대한 연결 문자열 구성

연결 문자열은 스토리지 에뮬레이터 또는 Azure Storage 계정에 대한 연결 및 인증 정보를 제공하는 설정입니다. 역할의 코드가 Azure Storage(blob, 큐 또는 테이블)에 액세스할 때마다 연결 문자열이 필요합니다.

> [!Note]
> Azure Storage 계정에 대한 연결 문자열은 정의된 형식을 사용해야 합니다([Azure Storage 연결 문자열 구성](/azure/storage/common/storage-configure-connection-string) 참조).

필요한 경우 로컬 스토리지를 사용하도록 연결 문자열을 설정한 다음, 애플리케이션을 클라우드 서비스에 배포할 때 Azure Storage 계정으로 설정할 수 있습니다. 연결 문자열을 제대로 설정하지 못하면 사용자의 역할이 시작되지 않거나 상태 초기화 중, 사용 중 및 중지 중 간에 전환될 수 있습니다.

연결 문자열을 만들려면 **설정 추가**를 선택하고 **형식**을 “연결 문자열”로 설정합니다.

기존 또는 새 연결 문자열의 경우 **값** 필드 오른쪽에 있는 **...** \*을 선택하여 **스토리지 연결 문자열 만들기** 대화 상자를 엽니다.

1. **연결 방법**에서 구독에서 스토리지 계정을 선택하는 **구독** 옵션을 선택합니다. 그런 다음 Visual Studio에서 자동으로 `.publishsettings` 파일에서 스토리지 계정 자격 증명을 획득합니다.
1. **수동으로 입력한 자격 증명**을 선택하면 Azure Portal의 정보를 사용하여 계정 이름 및 키를 직접 지정할 수 있습니다. 계정 키를 복사하려면:
    1. Azure Portal에서 스토리지 계정으로 이동하고 **키 관리**를 선택합니다.
    1. 계정 키를 복사하려면 Azure Portal에서 스토리지 계정으로 이동하고 **설정 &gt; 액세스 키**를 선택한 다음, 복사 단추를 사용하여 기본 액세스 키를 클립보드에 복사합니다.
1. 연결 옵션 중 하나를 선택합니다. **사용자 지정 엔드포인트 지정**에서 blob, 테이블 및 큐에 대한 특정 URL을 지정하라는 메시지가 표시됩니다. 사용자 지정 엔드포인트를 사용하면 [사용자 지정 도메인](/azure/storage/blobs/storage-custom-domain-name)을 사용하고 액세스를 더 정확하게 제어할 수 있습니다. [Azure Storage 연결 문자열 구성](/azure/storage/common/storage-configure-connection-string)을 참조하세요.
1. **확인**을 선택한 다음, **파일 > 저장**을 선택하여 새 연결 문자열로 구성을 업데이트합니다.

다시 Azure에 애플리케이션을 게시하는 경우 연결 문자열에 대한 Azure Storage 계정이 포함된 서비스 구성을 선택합니다. 애플리케이션을 게시한 후, 애플리케이션이 Azure Storage 서비스에 대해 예상대로 작동하는지 확인합니다.

서비스 구성을 업데이트하는 방법에 대한 자세한 내용은 [Storage 계정에 대한 연결 문자열 관리](vs-azure-tools-configure-roles-for-cloud-service.md#manage-connection-strings-for-storage-accounts) 섹션을 참조하세요.

## <a name="endpoints-page"></a>엔드포인트 페이지

웹 역할은 일반적으로 포트 80에서 단일 HTTP 엔드포인트를 가집니다. 반면 작업자 역할에는 임의 개수의 HTTP, HTTPS 또는 TCP 엔드포인트가 있을 수 있습니다. 엔드포인트는 외부 클라이언트에 사용할 수 있는 입력된 엔드포인트 또는 서비스에서 실행 되는 다른 역할에 사용할 수 있는 내부 엔드포인트일 수 있습니다.

- 외부 클라이언트와 웹 브라우저에서 HTTP 엔드포인트를 사용할 수 있도록 하려면 엔드포인트 유형을 입력으로 변경하고 이름 및 공용 포트 번호를 지정합니다.
- 외부 클라이언트와 웹 브라우저에서 HTTP 엔드포인트를 사용할 수 있도록 하려면 엔드포인트 유형을 **입력**으로 변경하고 이름, 공용 포트 번호 및 관리 인증서 이름을 지정합니다. 관리 인증서를 지정하려면 먼저 **인증서** 속성 페이지에 인증서를 정의해야 합니다.
- 클라우드 서비스의 다른 역할에서 내부 액세스에 대해 엔드포인트를 사용할 수 있도록 하려면 엔드포인트 유형을 내부로 변경하고 이 엔드포인트에 대한 이름 및 가능한 프라이빗 포트를 지정합니다.

## <a name="local-storage-page"></a>로컬 스토리지 페이지

**로컬 스토리지** 속성 페이지를 사용하여 역할에 대한 하나 이상의 로컬 스토리지 리소스를 예약할 수 있습니다. 로컬 스토리지 리소스는 역할의 인스턴스가 실행 중인 Azure 가상 컴퓨터의 파일 시스템에서 예약된 디렉터리입니다.

## <a name="certificates-page"></a>인증서 페이지

**인증서** 속성 페이지는 서비스 구성 인증서에 대한 정보를 추가합니다. 인증서는 서비스와 함께 패키징되지 않습니다. [Azure Portal](https://portal.azure.com)을 통해 Azure에 별도로 인증서를 업로드해야 합니다.

여기서는 인증서를 추가하여 서비스 구성에 대한 인증서의 정보를 추가합니다. 인증서는 서비스와 함께 패키징되지 않습니다. Azure Portal을 통해 별도로 인증서를 업로드해야 합니다.

인증서를 역할에 연결하려면 인증서에 대한 이름을 입력합니다. 이 이름을 사용하여 **엔드포인트** 페이지에서 HTTPS 끝점을 구성할 때 인증서를 참조합니다. 그런 다음 인증서 저장소가 **로컬 컴퓨터** 또는 **현재 사용자** 및 저장소의 이름인지를 지정합니다. 마지막으로, 인증서의 손도장을 입력합니다. 인증서가 현재 사용자\개인(나의) 저장소에 있는 경우 채워진 목록에서 인증서를 선택하여 인증서의 손도장을 입력할 수 있습니다. 다른 위치에 상주하는 경우 손도장 값을 직접 입력합니다.

인증서 저장소에서 인증서를 추가하면 모든 중간 인증서가 구성 설정에 자동으로 추가됩니다. 또한 이러한 중간 인증서는 SSL에 대한 서비스를 올바르게 구성하기 위해 Azure에 업로드해야 합니다.

서비스와 연결하는 모든 관리 인증서는 클라우드에서 실행되는 경우에만 서비스에 적용됩니다. 서비스는 로컬 개발 환경에서 실행 중인 경우에 컴퓨팅 에뮬레이터에서 관리되는 표준 인증서를 사용합니다.

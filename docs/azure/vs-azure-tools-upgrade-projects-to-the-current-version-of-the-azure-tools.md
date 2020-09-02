---
title: 프로젝트를 Azure 도구의 현재 버전으로 업그레이드
description: Azure 프로젝트를 Visual Studio에서 현재 버전의 Azure 도구로 업그레이드하는 방법을 알아봅니다.
author: ghogen
manager: jillfra
assetId: 1d64070a-078d-468a-87f4-e6715de6475f
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: ece853aacc2af48ec89af510a055486b9dded7ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66260588"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>프로젝트를 현재 버전의 Visual Studio 용 Azure 도구로 업그레이드하는 방법
## <a name="overview"></a>개요
Azure 도구의 현재 릴리스 (또는 1.6 이후 버전인 이전 릴리스)를 설치한 후에 1.6 (2011년 11월) 버전 전에 Azure 도구를 사용하여 생성된 모든 프로젝트는 여는 즉시 자동으로 업그레이드됩니다. 도구의 1.6 버전 (2011년 11월) 릴리스를 사용하여 프로젝트를 생성하고 여전히 그 릴리스가 설치되어 있는 경우 이전 릴리스에서 해당 프로젝트를 열고 나중에 업그레이드 여부를 결정할 수 있습니다.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>업그레이드 시 프로젝트의 변경 내용
프로젝트가 자동으로 업그레이드되거나 업그레이드하려고 지정한 경우 프로젝트는 특정 어셈블리의 현재 버전을 사용하여 작업하도록 수정되고 일부 속성도 이 섹션에 설명된 것처럼 변경됩니다. 프로젝트가 도구의 새로운 버전과 호환되기 위한 다른 변경을 필요로 할 경우 수동으로 해당 변경을 진행해야 합니다.

* 웹 역할에 대한 web.config 파일 및 작업자 역할에 대한 app.config 파일은 최신 버전의 Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll을 참조하도록 업데이트됩니다.
* Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll 및 Microsoft.WindowsAzure.ServiceRuntime.dll 어셈블리가 새 버전으로 업그레이드됩니다.
* Azure 프로젝트 파일 (.ccproj)에 저장된 게시 프로필은 **게시** 하위 디렉터리에서 확장명 .azurePubXml로 별도 파일에 이동됩니다.
* 게시 프로필의 일부 속성은 새로운 기능과 변경된 기능을 지원하도록 업데이트됩니다. 배포된 클라우드 서비스를 동시에 업데이트하거나 증분식으로 업데이트할 수 있으므로 **AllowUpgrade**는 **DeploymentReplacementMethod**로 대체됩니다.
* 디버깅에 사용되는 웹 서버가 자동으로 IIS(인터넷 정보 서비스)에서 IIS Express로 변경되지 않도록 **UseIISExpressByDefault** 속성이 추가되고 false 값으로 설정됩니다. IIS Express는 최신 버전의 도구를 사용하여 만든 프로젝트에 대한 기본 웹 서버입니다.
* Azure 캐싱이 하나 이상의 프로젝트 역할에서 호스팅되는 경우 프로젝트를 업그레이드할 때 서비스 구성 (.cscfg 파일) 및 서비스 정의 (.csdef 파일)의 일부 속성이 변경됩니다. 프로젝트가 Azure 캐싱 NuGet 패키지를 사용하는 경우 프로젝트는 패키지의 가장 최신 버전으로 업그레이드됩니다. Web.config 파일을 열고 업그레이드 프로세스 중에 클라이언트 구성이 올바르게 유지되었는지 확인해야 합니다. NuGet 패키지를 사용하지 않고 Azure 캐싱 클라이언트 어셈블리에 대한 참조를 추가한 경우 어셈블리는 업데이트되지 않습니다. 참조는 새 버전으로 수동 업데이트해야 합니다.

> [!IMPORTANT]
> F# 프로젝트의 경우 Azure 어셈블리에 대한 참조를 수동으로 업데이트하여 어셈블리의 최신 버전을 참조할 수 있도록 해야 합니다.
>
>

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Azure 프로젝트를 현재 릴리스로 업그레이드하는 방법
1. 업그레이드된 프로젝트에 대해 사용하려는 Visual Studio의 설치에 Azure 도구의 현재 버전을 설치하고 업그레이드할 프로젝트를 엽니다. 1.6 이전 (2011년 11월)의 Azure 도구 릴리스로 프로젝트를 만든 경우 프로젝트는 현재 버전으로 자동으로 업그레이드됩니다. 2011년 11월 릴리스를 사용하여 프로젝트를 만들고 해당 릴리스가 여전히 설치되어 있는 경우 프로젝트는 해당 릴리스에서 열립니다.
2. 솔루션 탐색기에서 프로젝트 노드에 대한 바로 가기 메뉴를 열고 **속성**을 선택한 다음, 나타나는 대화 상자의 **애플리케이션** 탭을 선택합니다.

    **응용 프로그램** 탭에 프로젝트와 관련된 도구 버전이 표시됩니다. Azure 도구의 현재 버전이 표시된 경우 프로젝트가 이미 업그레이드된 것입니다. 탭에 표시되는 것보다 최신 버전의 도구를 설치한 경우 **업그레이드** 단추가 나타납니다.
3. **업그레이드** 단추를 선택하여 프로젝트를 최신 버전의 도구로 업그레이드합니다.
4. 프로젝트를 빌드한 후 API 변경으로 인해 발생하는 오류를 해결합니다. 새 버전에 대한 코드를 수정하는 방법에 대한 자세한 내용은 특정 API에 대한 설명서를 참조하세요.

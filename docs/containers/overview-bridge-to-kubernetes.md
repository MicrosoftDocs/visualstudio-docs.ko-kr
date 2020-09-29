---
title: Bridge to Kubernetes 작동 방식
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Bridge to Kubernetes를 사용하여 개발 컴퓨터를 Kubernetes 클러스터에 연결하는 프로세스에 대해 설명합니다.
keywords: Bridge to Kubernetes, Docker, Kubernetes, Azure, 컨테이너
monikerRange: '>=vs-2019'
manager: jillfra
author: ghogen
ms.author: ghogen
ms.openlocfilehash: fbb3cfe6453c68079cb4b4cc6b57f8494f45c0cc
ms.sourcegitcommit: f9179a3a6d74fbd871f62b72491e70b9e7b05637
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90845950"
---
# <a name="how-bridge-to-kubernetes-works"></a>Bridge to Kubernetes 작동 방식

Bridge to Kubernetes를 사용하면 나머지 애플리케이션 또는 서비스가 포함된 Kubernetes 클러스터에 연결된 상태로 개발 컴퓨터에서 코드를 실행하고 디버그할 수 있습니다. 예를 들어 많은 상호 종속적 서비스 및 데이터베이스를 포함하는 대규모 마이크로 서비스 아키텍처가 있는 경우 이러한 종속성을 개발 컴퓨터에 복제하기 어려울 수 있습니다. 또한 내부 루프 개발 중에 각 코드 변경을 위한 코드를 빌드하여 Kubernetes 클러스터에 배포하는 작업은 속도가 느리고 시간이 오래 걸리고 디버거와 함께 사용하기 어려울 수 있습니다.

Bridge to Kubernetes를 사용하면 코드를 빌드하여 클러스터에 배포할 필요 없이 개발 컴퓨터와 클러스터 간에 직접 연결할 수 있습니다. 디버그하는 동안 개발 컴퓨터를 클러스터에 연결하면 Docker 또는 Kubernetes 구성을 만들지 않고도 전체 애플리케이션의 컨텍스트에서 서비스를 신속하게 테스트하고 개발할 수 있습니다.

Bridge to Kubernetes는 연결된 Kubernetes 클러스터와 개발 컴퓨터 간에 트래픽을 리디렉션합니다. 이러한 트래픽 리디렉션을 통해 Kubernetes 클러스터에서 실행되는 서비스와 개발 컴퓨터의 코드가 동일한 Kubernetes 클러스터에 있는 것처럼 통신할 수 있습니다. Bridge to Kubernetes는 Kubernetes 클러스터의 Pod에서 사용할 수 있는 환경 변수 및 탑재 볼륨을 개발 컴퓨터에 복제하는 방법도 제공합니다. 개발 컴퓨터의 환경 변수 및 탑재 볼륨에 대한 액세스를 제공함으로써 해당 종속성을 수동으로 복제하지 않고도 코드 작업을 빠르게 수행할 수 있습니다.

> [!WARNING]
> Bridge to Kubernetes는 개발 및 테스트 시나리오에서만 사용하도록 되어 있으며, 프로덕션 클러스터 또는 활성 상태 라이브 서비스에 사용하기에는 적합하지 않거나 지원되지 않습니다.

## <a name="using-bridge-to-kubernetes"></a>Bridge to Kubernetes 사용

Visual Studio에서 Bridge to Kubernetes를 사용하려면 ‘ASP.NET 및 웹 개발’ 워크로드와 [Bridge to Kubernetes 확장][btk-extension]이 설치되어 있는 Windows 10에서 실행되는 [Visual Studio 2019][visual-studio] 버전 16.7 미리 보기 4 이상이 필요합니다. Bridge to Kubernetes를 사용하여 Kubernetes 클러스터에 연결하는 경우 클러스터의 기존 Pod로 들어오고 나가는 모든 트래픽을 개발 컴퓨터로 리디렉션할 수 있습니다.

> [!NOTE]
> Bridge to Kubernetes를 사용하는 경우 개발 컴퓨터로 리디렉션할 서비스의 이름을 묻는 메시지가 표시됩니다. 이 옵션은 리디렉션에 사용할 Pod를 확인하는 편리한 방법입니다. Kubernetes 클러스터와 개발 컴퓨터 간의 모든 리디렉션은 Pod에 적용됩니다.

Bridge to Kubernetes는 클러스터에 대한 연결을 설정할 때 다음 작업을 수행합니다.

* 클러스터에서 바꿀 서비스, 코드에 사용할 개발 컴퓨터의 포트, 일회성 작업인 코드 시작 작업을 구성하라는 메시지를 표시합니다.
* 클러스터의 Pod에 있는 컨테이너를 트래픽이 개발 컴퓨터로 리디렉션되는 원격 에이전트 컨테이너로 바꿉니다.
* 개발 컴퓨터에서 [kubectl port-forward][kubectl-port-forward]를 실행하여 개발 컴퓨터의 트래픽을 클러스터에서 실행되는 원격 에이전트로 전달합니다.
* 원격 에이전트를 사용하여 클러스터에서 환경 정보를 수집합니다. 이 환경 정보에는 환경 변수, 표시되는 서비스, 볼륨 탑재, 비밀 탑재가 포함됩니다.
* 개발 컴퓨터의 서비스가 클러스터에서 실행되는 것처럼 동일한 변수에 액세스할 수 있도록 Visual Studio에서 환경을 설정합니다.  
* hosts 파일을 업데이트하여 클러스터의 서비스를 개발 컴퓨터의 로컬 IP 주소에 매핑합니다. 이러한 hosts 파일 항목을 사용하면 개발 컴퓨터에서 실행되는 코드를 통해 클러스터에서 실행되는 다른 서비스에 요청을 수행할 수 있습니다. hosts 파일을 업데이트하기 위해 Bridge to Kubernetes는 클러스터에 연결할 때 개발 컴퓨터에 대한 관리자 액세스 권한을 요청합니다.
* 개발 컴퓨터에서 코드 실행 및 디버깅을 시작합니다. 필요한 경우 Bridge to Kubernetes는 현재 개발 컴퓨터에서 필요한 포트를 사용 중인 서비스나 프로세스를 중지하여 필요한 포트를 해제합니다.

클러스터에 연결한 후에는 컨테이너화하지 않고 컴퓨터에서 기본적으로 코드를 실행하고 디버그할 수 있으며, 코드가 클러스터의 나머지 부분과 직접 상호 작용할 수 있습니다. 기본적으로 실행되는 코드가 트래픽을 수락하고 처리할 수 있도록 원격 에이전트가 수신하는 모든 네트워크 트래픽이 연결 중에 지정한 로컬 포트로 리디렉션됩니다. 개발 컴퓨터에서 실행되는 코드가 클러스터의 환경 변수, 볼륨, 비밀을 사용할 수 있습니다. 또한 Bridge to Kubernetes를 통해 개발자 컴퓨터에 추가되는 hosts 파일 항목 및 포트 전달 기능 때문에 코드에 클러스터의 서비스 이름을 사용하여 네트워크 트래픽을 클러스터에서 실행되는 서비스로 보낼 수 있으며, 해당 트래픽은 클러스터에서 실행되는 서비스로 전달됩니다. 연결된 시간 동안 계속해서 개발 컴퓨터와 클러스터 간에 트래픽이 라우팅됩니다.

또한 Bridge to Kubernetes를 사용하면 `KubernetesLocalProcessConfig.yaml` 파일을 통해 개발 컴퓨터에서 클러스터의 Pod에 사용 가능한 환경 변수 및 탑재된 파일을 복제할 수 있습니다. 이 파일을 사용하여 새 환경 변수 및 볼륨 탑재를 만들 수도 있습니다.

> [!NOTE]
> 클러스터에 연결하는 시간(및 추가로 15분) 동안 Bridge to Kubernetes는 로컬 컴퓨터에 대한 관리자 권한이 있는 *EndpointManager*라는 프로세스를 실행합니다.

## <a name="additional-configuration-with-kuberneteslocalprocessconfigyaml"></a>KubernetesLocalProcessConfig.yaml을 사용하는 추가 구성

`KubernetesLocalProcessConfig.yaml` 파일을 사용하면 클러스터의 Pod에 사용할 수 있는 환경 변수 및 탑재된 파일을 복제할 수 있습니다. 추가 구성 옵션에 대한 자세한 내용은 [Bridge to Kubernetes 구성][using-config-yaml]을 참조하세요.

## <a name="using-routing-capabilities-for-developing-in-isolation"></a>격리 상태로 개발하기 위한 라우팅 기능 사용

기본적으로 Bridge to Kubernetes는 서비스의 모든 트래픽을 개발 컴퓨터로 리디렉션합니다. 하위 도메인에서 시작되는 서비스에 대한 요청만 개발 컴퓨터로 리디렉션하는 라우팅 기능을 사용할 수도 있습니다. 해당 라우팅 기능을 사용하면 Bridge to Kubernetes를 사용하여 격리 상태로 개발하고 클러스터의 다른 트래픽이 중단되지 않도록 할 수 있습니다.

다음 애니메이션에서는 동일한 클러스터에서 두 명의 개발자가 격리 상태로 작업하는 상황을 보여 줍니다.

![격리를 보여 주는 애니메이션 GIF](media/bridge-to-kubernetes/btk-graphic-isolated.gif)

격리 상태로 작업하도록 설정하면 Bridge to Kubernetes가 Kubernetes 클러스터에 연결하는 것 외에도 다음과 같은 작업을 수행합니다.

* Kubernetes 클러스터에 Azure Dev Spaces가 사용하도록 설정되지 않았는지 확인합니다.
* 클러스터에서 동일한 네임스페이스의 원하는 서비스를 복제하고 *routing.visualstudio.io/route-from=SERVICE_NAME* 레이블 및 *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME* 주석을 추가합니다.
* Kubernetes 클러스터에서 동일한 네임스페이스의 라우팅 관리자를 구성하고 시작합니다. 라우팅 관리자는 네임스페이스에서 라우팅을 구성할 때 레이블 선택기를 사용해 *routing.visualstudio.io/route-from=SERVICE_NAME* 레이블 및 *routing.visualstudio.io/route-on-header=kubernetes-route-as: GENERATED_NAME* 주석을 찾습니다.

Bridge to Kubernetes가 Kubernetes 클러스터에서 Azure Dev Spaces가 사용되는 것을 검색하는 경우 Bridge to Kubernetes를 사용하려면 Azure Dev Spaces를 사용하지 않도록 설정하라는 메시지가 표시됩니다.

라우팅 관리자는 시작될 때 다음을 수행합니다.
* 하위 도메인에 대해 *GENERATED_NAME*을 사용하여 네임스페이스의 모든 수신 내용을 복제합니다. 
* *GENERATED_NAME* 하위 도메인을 사용하여 복제된 수신 내용과 관련된 각 서비스에 대한 envoy pod를 만듭니다.
* 격리 상태로 작업 중인 서비스에 대한 추가 envoy pod를 만듭니다. 이렇게 하면 해당 하위 도메인이 포함된 요청이 개발 컴퓨터로 라우팅됩니다.
* 각 envoy pod가 하위 도메인을 포함하여 서비스 라우팅을 처리하도록 라우팅 규칙을 구성합니다.

다음 다이어그램은 Bridge to Kubernetes가 클러스터에 연결되기 이전 Kubernetes 클러스터를 보여 줍니다.

![Bridge to Kubernetes가 없는 클러스터의 다이어그램](media/bridge-to-kubernetes/kubr-cluster.svg)

다음 다이어그램은 격리 모드에서 Bridge to Kubernetes가 사용되는 동일한 클러스터를 보여 줍니다. 여기에서 격리 상태에서 라우팅을 지원하는 중복 서비스 및 envoy pod를 볼 수 있습니다.

![Bridge to Kubernetes가 사용되는 클러스터의 다이어그램](media/bridge-to-kubernetes/kubr-cluster-devcomputer.svg)

*GENERATED_NAME* 하위 도메인이 포함된 요청이 클러스터에서 수신되면 *kubernetes-route-as=GENERATED_NAME* 헤더가 요청에 추가됩니다. envoy pod는 클러스터에서 해당 서비스에 대한 요청을 라우팅하는 작업을 처리합니다. 요청이 격리 상태로 작업 중인 서비스로 라우팅되는 경우, 원격 에이전트가 이 요청을 개발 컴퓨터로 리디렉션합니다.

*GENERATED_NAME* 하위 도메인이 포함되지 않은 요청이 클러스터에서 수신되면 헤더가 요청에 추가되지 않습니다. envoy pod는 클러스터에서 해당 서비스에 대한 요청을 라우팅하는 작업을 처리합니다. 요청이 바꿀 예정인 서비스로 라우팅되는 경우 이 요청은 원격 에이전트가 아닌 원래 서비스로 라우팅됩니다.

> [!IMPORTANT]
> 클러스터의 각 서비스는 추가 요청을 수행할 때 *kubernetes-route-as=GENERATED_NAME* 헤더를 전달해야 합니다. 예를 들어 *serviceA*가 요청을 수신하면 응답을 반환하기 전에 *serviceB*를 요청합니다. 이 예제의 경우 *serviceA*는 *serviceB* 요청에서 *kubernetes-route-as=GENERATED_NAME* 헤더를 전달해야 합니다. [ASP.NET][asp-net-header]과 같은 일부 언어에는 헤더 전파를 처리하는 메서드가 있을 수도 있습니다.

클러스터와 연결을 끊으면 기본적으로 Bridge to Kubernetes가 모든 envoy pod 및 중복 서비스를 제거합니다. 

> [!NOTE]
> 라우팅 관리자 배포 및 서비스는 네임스페이스에서 계속 실행됩니다. 배포 및 서비스를 제거하려면 네임스페이스에 대해 다음 명령을 실행합니다.
>
> ```azurecli
> kubectl delete deployment routingmanager-deployment -n NAMESPACE
> kubectl delete service routingmanager-service -n NAMESPACE
> ```

## <a name="diagnostics-and-logging"></a>진단 및 로깅

Bridge to Kubernetes를 사용하여 클러스터에 연결하는 경우 클러스터의 진단 로그가 개발 컴퓨터의 *TEMP* 디렉터리에서 *Bridge to Kubernetes* 폴더에 기록됩니다.

## <a name="limitations"></a>제한 사항

Bridge to Kubernetes에는 다음과 같은 제한 사항이 있습니다.

* 단일 Pod의 지원을 받는 서비스에만 연결할 수 있습니다. 복제본이 있는 서비스와 같이 여러 개의 Pod가 있는 서비스에는 연결할 수 없습니다.
* Bridge to Kubernetes가 성공적으로 연결하려면 Pod에 단일 컨테이너만 실행되고 있어야 합니다. Bridge to Kubernetes는 서비스 메시를 통해 삽입된 사이드카 컨테이너와 같은 추가 컨테이너를 포함하는 Pod가 있는 서비스에 연결할 수 없습니다.
* 개발 컴퓨터에서 Bridge to Kubernetes를 실행하려면 hosts 파일을 편집하기 위해 관리자 권한이 필요합니다.
* Bridge to Kubernetes는 Azure Dev Spaces가 사용하도록 설정된 클러스터에서는 사용할 수 없습니다.

### <a name="bridge-to-kubernetes-and-clusters-with-azure-dev-spaces-enabled"></a>Bridge to Kubernetes 및 Azure Dev Spaces가 사용되는 클러스터

Azure Dev Spaces가 사용하도록 설정된 클러스터에서는 Bridge to Kubernetes를 사용할 수 없습니다. Azure Dev Spaces가 사용하도록 설정된 클러스터에서 Bridge to Kubernetes를 사용하려면 Azure Dev Spaces를 사용하지 않도록 설정한 후에 클러스터에 연결해야 합니다.

## <a name="next-steps"></a>다음 단계

Bridge to Kubernetes를 사용하여 로컬 개발 컴퓨터를 클러스터에 연결하려면 [Bridge to Kubernetes 사용](bridge-to-kubernetes.md)을 참조하세요.

[asp-net-header]: https://www.nuget.org/packages/Microsoft.AspNetCore.HeaderPropagation/
[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[using-config-yaml]: configure-bridge-to-kubernetes.md
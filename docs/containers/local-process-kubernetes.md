---
title: Visual Studio에서 Kubernetes와 함께 로컬 프로세스를 사용(미리 보기)
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Visual Studio에서 Kubernetes와 함께 로컬 프로세스를 사용하여 개발 컴퓨터를 Kubernetes 클러스터에 연결하는 방법을 알아봅니다.
keywords: Kubernetes와 함께 로컬 프로세스 사용, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, 컨테이너
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: 29a3c8563660507a2378a58595ba5ea64788b417
ms.sourcegitcommit: e359b93c93c6ca316c0d8b86c2b6e566171fd1ea
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507900"
---
# <a name="use-local-process-with-kubernetes-preview"></a>Kubernetes와 함께 로컬 프로세스 사용(미리 보기)

Kubernetes와 함께 로컬 프로세스를 사용하면 나머지 애플리케이션 또는 서비스가 포함된 Kubernetes 클러스터에 연결된 상태로 개발 컴퓨터에서 코드를 실행하고 디버그할 수 있습니다. 예를 들어 많은 상호 종속적 서비스 및 데이터베이스를 포함하는 대규모 마이크로 서비스 아키텍처가 있는 경우 이러한 종속성을 개발 컴퓨터에 복제하기 어려울 수 있습니다. 또한 내부 루프 개발 중에 각 코드 변경을 위한 코드를 빌드하여 Kubernetes 클러스터에 배포하는 작업은 속도가 느리고 시간이 오래 걸리고 디버거와 함께 사용하기 어려울 수 있습니다.

Kubernetes와 함께 로컬 프로세스를 사용하면 코드를 빌드하여 클러스터에 배포할 필요 없이 개발 컴퓨터와 클러스터 간에 직접 연결할 수 있습니다. 디버그하는 동안 개발 컴퓨터를 클러스터에 연결하면 Docker 또는 Kubernetes 구성을 만들지 않고도 전체 애플리케이션의 컨텍스트에서 서비스를 신속하게 테스트하고 개발할 수 있습니다.

Kubernetes와 함께 로컬 프로세스를 사용하면 연결된 Kubernetes 클러스터와 개발 컴퓨터 간에 트래픽이 리디렉션됩니다. 이러한 트래픽 리디렉션을 통해 Kubernetes 클러스터에서 실행되는 서비스와 개발 컴퓨터의 코드가 동일한 Kubernetes 클러스터에 있는 것처럼 통신할 수 있습니다. Kubernetes와 함께 로컬 프로세스를 사용하면 Kubernetes 클러스터의 Pod에서 사용할 수 있는 환경 변수 및 탑재 볼륨을 개발 컴퓨터에 복제할 수도 있습니다. 개발 컴퓨터의 환경 변수 및 탑재 볼륨에 대한 액세스를 제공함으로써 해당 종속성을 수동으로 복제하지 않고도 코드 작업을 빠르게 수행할 수 있습니다.

이 가이드에서는 Kubernetes와 함께 로컬 프로세스를 사용하여 개발 컴퓨터에서 실행되는 코드와 Kubernetes 클러스터 간에 트래픽을 리디렉션하는 방법을 설명합니다. Kubernetes 클러스터에 여러 개의 마이크로 서비스를 포함하여 대규모 애플리케이션 예제를 배포하는 스크립트도 제공됩니다.

> [!IMPORTANT]
> 이 기능은 현재 미리 보기로 제공됩니다. [부속 사용 약관][preview-terms]에 동의하면 미리 보기를 사용할 수 있습니다. 이 기능의 몇 가지 측면은 일반 공급(GA) 전에 변경될 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전 주의 사항

이 가이드에서는 [자전거 공유 애플리케이션 예제][bike-sharing-github]를 사용하여 개발 컴퓨터를 Kubernetes 클러스터에 연결하는 방법을 보여 줍니다. 사용자 고유의 애플리케이션이 Kubernetes 클러스터에서 이미 실행 중인 경우에도 아래 단계를 수행하고 해당 서비스의 이름을 사용할 수 있습니다.

### <a name="prerequisites"></a>필수 조건

* Azure 구독 Azure 구독이 없는 경우 [체험 계정](https://azure.microsoft.com/free)을 만들 수 있습니다.
* [Azure CLI 설치][azure-cli]
* ‘Azure 개발’ 워크로드가 설치되어 있는 Windows 10에서 실행되는 [Visual Studio 2019][visual-studio] 버전 16.7 미리 보기 4 이상
* [로컬 프로세스 Kubernetes 확장 설치][lpk-extension].

.NET 콘솔 애플리케이션의 경우 *Microsoft.VisualStudio.Azure.Kubernetes.Tools.Targets* NuGet 패키지도 설치합니다.

## <a name="create-a-kubernetes-cluster"></a>Kubernetes 클러스터 만들기

[지원되는 지역][supported-regions]에 AKS 클러스터를 만듭니다. 아래 명령은 *MyResourceGroup*이라는 리소스 그룹과 *MyAKS*라는 AKS 클러스터를 만듭니다.

```azurecli-interactive
az group create \
    --name MyResourceGroup \
    --location eastus

az aks create \
    --resource-group MyResourceGroup \
    --name MyAKS \
    --location eastus \
    --node-count 3 \
    --generate-ssh-keys
```

## <a name="install-the-sample-application"></a>애플리케이션 예제 설치

제공된 스크립트를 사용하여 클러스터에 애플리케이션 예제를 설치합니다. [Azure Cloud Shell][azure-cloud-shell]을 사용하여 이 스크립트를 실행할 수 있습니다.

```azurecli-interactive
git clone https://github.com/Microsoft/mindaro
cd mindaro
chmod +x ./local-process-quickstart.sh
./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
```

설치 스크립트 출력에 표시된 공용 URL을 열어 클러스터를 실행하는 애플리케이션 예제로 이동합니다.

```console
$ ./local-process-quickstart.sh -g MyResourceGroup -n MyAKS
Defaulting Dev spaces repository root to current directory : ~/mindaro
Setting the Kube context
...
To try out the app, open the url:
bikeapp.bikesharingweb.EXTERNAL_IP.nip.io
```

위 예제에서 공용 URL은 `bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`입니다.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>클러스터에 연결 및 서비스 디버그

개발 컴퓨터에서 [az aks get-credentials][az-aks-get-credentials]를 사용하여 Kubernetes CLI를 다운로드하고 Kubernetes 클러스터에 연결되도록 구성합니다.

```azurecli
az aks get-credentials --resource-group MyResourceGroup --name MyAKS
```

Visual Studio에서 [자전거 공유 애플리케이션 예제][bike-sharing-github]의 *mindaro/samples/BikeSharingApp/ReservationEngine/app.csproj*를 엽니다.

프로젝트에서 아래 그림과 같이 시작 설정 드롭다운을 통해 ‘Kubernetes와 함께 로컬 프로세스 사용’을 선택합니다.

![Kubernetes와 함께 로컬 프로세스 사용 선택](media/local-process-kubernetes/choose-local-process.png)

‘Kubernetes와 함께 로컬 프로세스 사용’ 옆에 있는 시작 단추를 클릭합니다. ‘Kubernetes와 함께 로컬 프로세스 사용’ 대화 상자에서 다음을 수행합니다.

* 구독을 선택합니다.
* 클러스터로 *MyAKS*를 선택합니다.
* 네임스페이스로 *dev*를 선택합니다.
* 리디렉션할 서비스로 *reservationengine*을 선택합니다.
* 시작 프로필로 *app*을 선택합니다.
* 브라우저를 시작할 URL로 `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`를 선택합니다.

![Kubernetes 클러스터와 함께 로컬 프로세스 사용 선택](media/local-process-kubernetes/choose-local-process-cluster.png)

> [!IMPORTANT]
> 단일 Pod가 있는 서비스만 리디렉션할 수 있습니다.

‘저장 및 디버깅 시작’을 클릭합니다.

*reservationengine* 서비스에 대한 Kubernetes 클러스터의 모든 트래픽이 개발 컴퓨터에서 실행되는 애플리케이션 버전으로 리디렉션됩니다. 또한 Kubernetes와 함께 로컬 프로세스를 사용하면 애플리케이션의 모든 아웃바운드 트래픽이 Kubernetes 클러스터로 다시 라우팅됩니다.

> [!NOTE]
> *KubernetesDNSManager*가 관리자 권한으로 실행되고 hosts 파일을 수정할 수 있게 허용하라는 메시지가 표시됩니다.

상태 표시줄에 *reservationengine* 서비스에 연결되었다고 표시되면 개발 컴퓨터가 연결된 것입니다.

![개발 컴퓨터 연결됨](media/local-process-kubernetes/development-computer-connected.png)

> [!NOTE]
> 이후에 시작할 때는 ‘Kubernetes와 함께 로컬 프로세스 사용’ 대화 상자가 표시되지 않습니다. 이러한 설정은 프로젝트 속성의 ‘디버그’ 창에서 업데이트합니다.

개발 컴퓨터가 연결되면 바꾸려는 서비스에 대한 트래픽이 개발 컴퓨터로 리디렉션되기 시작합니다.

## <a name="set-a-break-point"></a>중단점 설정

[BikesHelper.cs][bikeshelper-cs-breakpoint]를 열고 줄 26에서 아무 곳이나 클릭하여 커서를 놓습니다. *F9* 키를 누르거나 ‘디버그’, ‘중단점 설정/해제’를 차례로 클릭하여 중단점을 설정합니다.

공용 URL을 열어 애플리케이션 예제로 이동합니다. 사용자로 ‘Aurelia Briggs(고객)’를 선택하고 대여할 자전거를 선택합니다. ‘자전거 대여’를 클릭합니다. Visual Studio로 돌아가서 줄 26이 강조 표시된 것을 확인합니다. 설정한 중단점으로 인해 서비스가 줄 26에서 일시 중지되었습니다. 서비스를 다시 시작하려면 *F5* 키를 누르거나 *디버그*, *계속*을 차례로 클릭합니다. 브라우저로 돌아가서 자전거를 대여했다고 페이지에 표시되는지 확인합니다.

`BikesHelper.cs`에서 줄 26에 커서를 놓고 *F9* 키를 눌러 중단점을 제거합니다.

> [!NOTE]
> 기본적으로 디버깅 작업을 중지하면 Kubernetes 클러스터에서 개발 컴퓨터의 연결이 끊어집니다. 디버깅 옵션의 ‘Kubernetes 디버깅 도구’ 섹션에서 ‘디버깅 후 연결 끊기’를 *false*로 변경하면 이 동작을 변경할 수 있습니다. 이 설정을 업데이트하면 디버깅을 중지하고 시작할 때 개발 컴퓨터가 연결된 상태를 유지합니다. 클러스터에서 개발 컴퓨터의 연결을 끊으려면 도구 모음에서 ‘연결 끊기’ 단추를 클릭합니다.
>
> Visual Studio가 갑자기 종료되거나 클러스터 연결을 종료할 경우 리디렉션 중인 서비스가 Kubernetes와 함께 로컬 프로세스를 사용하여 연결하기 전의 원래 상태로 복원되지 않을 수 있습니다. 이 문제를 해결하려면 [문제 해결 가이드][troubleshooting]를 참조하세요.

## <a name="additional-configuration"></a>추가 구성

Kubernetes와 함께 로컬 프로세스를 사용하면 추가 구성 없이 라우팅 트래픽을 처리하고 환경 변수를 복제할 수 있습니다. Kubernetes 클러스터의 컨테이너에 탑재된 파일(예: ConfigMap 파일)을 다운로드해야 하는 경우 `KubernetesLocalProcessConfig.yaml`을 만들어 해당 파일을 개발용 컴퓨터에 다운로드할 수 있습니다. 자세한 내용은 [KubernetesLocalProcessConfig.yaml을 사용하여 Kubernetes용 로컬 프로세스 추가 구성][kubernetesLocalProcessConfig-yaml]을 참조하세요.

## <a name="using-logging-and-diagnostics"></a>로깅 및 진단 사용

[개발 컴퓨터의 *TEMP* 디렉터리][azds-tmp-dir]에 있는 `Azure Dev Spaces` 디렉터리에서 진단 로그를 찾을 수 있습니다.

## <a name="remove-the-sample-application-from-your-cluster"></a>클러스터에서 애플리케이션 예제 제거

제공된 스크립트를 사용하여 클러스터에서 애플리케이션 예제를 제거합니다.

```azurecli-interactive
./local-process-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>다음 단계

로컬 프로세스 Kubernetes의 작동 방식을 알아봅니다.

> [!div class="nextstepaction"]
> [Kubernetes와 함께 로컬 프로세스를 사용하는 경우의 작동 방식](overview-local-process-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-local-process-with-kubernetes.md
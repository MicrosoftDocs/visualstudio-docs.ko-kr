---
title: Visual Studio에서 Bridge to Kubernetes 사용
titleSuffix: ''
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: how-to
description: Visual Studio에서 Bridge to Kubernetes를 사용하여 개발 컴퓨터를 Kubernetes 클러스터에 연결하는 방법을 알아봅니다.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, 컨테이너
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jillfra
ms.openlocfilehash: c7d046ca63af5aa65f5cd286e9a6199afc6c2947
ms.sourcegitcommit: f9179a3a6d74fbd871f62b72491e70b9e7b05637
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90845954"
---
# <a name="use-bridge-to-kubernetes"></a>Bridge to Kubernetes 사용

Bridge to Kubernetes를 사용하여 개발 컴퓨터에서 실행되는 코드와 Kubernetes 클러스터 간에 트래픽을 리디렉션할 수 있습니다. Kubernetes 클러스터에 여러 개의 마이크로 서비스를 포함하여 대규모 애플리케이션 예제를 배포하는 스크립트도 제공됩니다.

## <a name="before-you-begin"></a>시작하기 전 주의 사항

이 가이드에서는 [자전거 공유 애플리케이션 예제][bike-sharing-github]를 사용하여 개발 컴퓨터를 Kubernetes 클러스터에 연결하는 방법을 보여 줍니다. 사용자 고유의 애플리케이션이 Kubernetes 클러스터에서 이미 실행 중인 경우에도 아래 단계를 수행하고 해당 서비스의 이름을 사용할 수 있습니다.

### <a name="prerequisites"></a>필수 조건

* Azure 구독 Azure 구독이 없는 경우 [체험 계정](https://azure.microsoft.com/free)을 만들 수 있습니다.
* [Azure CLI 설치][azure-cli]
* ‘Azure 개발’ 워크로드가 설치되어 있는 Windows 10에서 실행되는 [Visual Studio 2019][visual-studio] 버전 16.7 미리 보기 4 이상
* [Bridge to Kubernetes 확장 설치][btk-extension]

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
chmod +x ./bridge-quickstart.sh
./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
```

설치 스크립트 출력에 표시된 공용 URL을 열어 클러스터를 실행하는 애플리케이션 예제로 이동합니다.

```console
$ ./bridge-quickstart.sh -g MyResourceGroup -n MyAKS
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

GitHub의 [자전거 공유 애플리케이션 예제][bike-sharing-github] 리포지토리에서 녹색 **코드** 단추의 드롭다운을 사용하고 **Visual Studio에서 열기**를 선택하여 리포지토리를 로컬에서 복제하고 Visual Studio에서 폴더를 엽니다. 그런 다음, **파일** > **프로젝트 열기**를 사용하여 *samples/BikeSharingApp/ReservationEngine* 폴더의 **app.csproj** 프로젝트를 엽니다.

프로젝트에서 아래 그림과 같이 시작 설정 드롭다운에서 **Bridge to Kubernetes**를 선택합니다.

![Bridge to Kubernetes 선택](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

*Bridge to Kubernetes* 옆에 있는 시작 단추를 클릭합니다. **Bridge to Kubernetes의 프로필 만들기** 대화 상자에서 다음을 수행합니다.

* 구독을 선택합니다.
* 클러스터로 *MyAKS*를 선택합니다.
* 네임스페이스로 *bikeapp*을 선택합니다.
* 리디렉션할 서비스로 *reservationengine*을 선택합니다.
* 시작 프로필로 *app*을 선택합니다.
* 브라우저를 시작할 URL로 `http://bikeapp.bikesharingweb.EXTERNAL_IP.nip.io`를 선택합니다.

![Bridge to Kubernetes 클러스터 선택](media/bridge-to-kubernetes/choose-bridge-cluster2.png)

> [!IMPORTANT]
> 단일 Pod가 있는 서비스만 리디렉션할 수 있습니다.

클러스터를 사용하는 다른 사용자가 변경 내용의 영향을 받지 않는 격리된 상태로 실행할지 여부를 선택합니다. 해당 격리 모드는 영향을 받는 각 서비스의 복사본으로 요청을 라우팅하고 다른 모든 트래픽을 정상적으로 라우팅하는 방식으로 수행됩니다. 해당 작업을 수행하는 방법에 관한 자세한 설명은 [Bridge to Kubernetes 작동 방식][btk-overview-routing]을 참조하세요.

‘저장 및 디버깅 시작’을 클릭합니다.

*reservationengine* 서비스에 대한 Kubernetes 클러스터의 모든 트래픽이 개발 컴퓨터에서 실행되는 애플리케이션 버전으로 리디렉션됩니다. 또한 Bridge to Kubernetes는 애플리케이션의 모든 아웃바운드 트래픽을 Kubernetes 클러스터로 다시 라우팅합니다.

> [!NOTE]
> *EndpointManager*가 관리자 권한으로 실행되고 hosts 파일을 수정할 수 있게 허용하라는 메시지가 표시됩니다.

상태 표시줄에 `reservationengine` 서비스에 연결되었다고 표시되면 개발 컴퓨터가 연결된 것입니다.

![개발 컴퓨터 연결됨](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> 이후 시작 시 **Bridge to Kubernetes의 프로필 만들기** 대화 상자가 표시됩니다. 해당 설정은 프로젝트 속성의 **디버그** 창에서 업데이트합니다.

개발 컴퓨터가 연결되면 바꾸려는 서비스에 대한 트래픽이 개발 컴퓨터로 리디렉션되기 시작합니다.

## <a name="set-a-break-point"></a>중단점 설정

[BikesHelper.cs][bikeshelper-cs-breakpoint]를 열고 줄 26에서 아무 곳이나 클릭하여 커서를 놓습니다. *F9* 키를 누르거나 **디버그** > **중단점 설정/해제**를 선택하여 중단점을 설정합니다.

공용 URL을 열어 애플리케이션 예제로 이동합니다. 사용자로 ‘Aurelia Briggs(고객)’를 선택하고 대여할 자전거를 선택합니다. **자전거 대여**를 선택합니다. Visual Studio로 돌아가서 줄 26이 강조 표시된 것을 확인합니다. 설정한 중단점으로 인해 서비스가 줄 26에서 일시 중지되었습니다. 서비스를 다시 시작하려면 **F5** 키를 누르거나 **디버그** > **계속**을 클릭합니다. 브라우저로 돌아가서 자전거를 대여했다고 페이지에 표시되는지 확인합니다.

`BikesHelper.cs`에서 줄 26에 커서를 놓고 **F9** 키를 눌러 중단점을 제거합니다.

> [!NOTE]
> 기본적으로 디버깅 작업을 중지하면 Kubernetes 클러스터에서 개발 컴퓨터의 연결이 끊어집니다. 디버깅 옵션의 ‘Kubernetes 디버깅 도구’ 섹션에서 ‘디버깅 후 연결 끊기’를 false`false`로 변경하면 이 동작을 변경할 수 있습니다. 이 설정을 업데이트하면 디버깅을 중지하고 시작할 때 개발 컴퓨터가 연결된 상태를 유지합니다. 클러스터에서 개발 컴퓨터의 연결을 끊으려면 도구 모음에서 ‘연결 끊기’ 단추를 클릭합니다.

## <a name="additional-configuration"></a>추가 구성

Bridge to Kubernetes는 추가 구성 없이 트래픽 라우팅 및 환경 변수 복제를 처리할 수 있습니다. Kubernetes 클러스터의 컨테이너에 탑재된 파일(예: ConfigMap 파일)을 다운로드해야 하는 경우 `KubernetesLocalProcessConfig.yaml`을 만들어 해당 파일을 개발용 컴퓨터에 다운로드할 수 있습니다. 자세한 내용은 [Bridge to Kubernetes의 추가 구성에 KubernetesLocalProcessConfig.yaml 사용][kubernetesLocalProcessConfig-yaml]을 참조하세요.

## <a name="using-logging-and-diagnostics"></a>로깅 및 진단 사용

개발 컴퓨터의 *TEMP* 디렉터리에 있는 `Bridge to Kubernetes` 디렉터리에서 진단 로그를 찾을 수 있습니다. 

## <a name="remove-the-sample-application-from-your-cluster"></a>클러스터에서 애플리케이션 예제 제거

제공된 스크립트를 사용하여 클러스터에서 애플리케이션 예제를 제거합니다.

```azurecli-interactive
./bridge-quickstart.sh -c -g MyResourceGroup -n MyAKS
```

## <a name="next-steps"></a>다음 단계

Bridge to Kubernetes 작동 방식을 알아봅니다.

> [!div class="nextstepaction"]
> [Bridge to Kubernetes 작동 방식](overview-bridge-to-kubernetes.md)

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-vs-code]: https://marketplace.visualstudio.com/items?itemName=azuredevspaces.azds
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-lates&preserve-view=true
[azure-cloud-shell]: /azure/cloud-shell/w.md
[az-aks-get-credentials]: /cli/azure/aks?view=azure-cli-latest&preserve-view=true#az-aks-get-credentials
[az-aks-vs-code]: https://marketplace.visualstudio.com/items?itemName=ms-kubernetes-tools.vscode-aks-tools
[bike-sharing-github]: https://github.com/Microsoft/mindaro
[preview-terms]: https://azure.microsoft.com/support/legal/preview-supplemental-terms/
[bikeshelper-cs-breakpoint]: https://github.com/Microsoft/mindaro/blob/master/samples/BikeSharingApp/ReservationEngine/BikesHelper.cs#L26
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
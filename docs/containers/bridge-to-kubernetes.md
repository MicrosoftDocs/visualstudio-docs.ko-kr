---
title: Visual Studio에서 Bridge to Kubernetes 사용
titleSuffix: ''
ms.technology: vs-azure
ms.date: 03/24/2021
ms.topic: quickstart
description: Visual Studio에서 Bridge to Kubernetes를 사용하여 개발 컴퓨터를 Kubernetes 클러스터에 연결하는 방법을 알아봅니다.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, 컨테이너
monikerRange: '>=vs-2019'
ms.author: ghogen
author: ghogen
manager: jmartens
ms.openlocfilehash: fdcf31d062fe2be72709979f0892e6a7f535024a
ms.sourcegitcommit: 2049ec99f1439ec91d002853226934b067b1ee70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105635050"
---
# <a name="use-bridge-to-kubernetes"></a>Bridge to Kubernetes 사용

Bridge to Kubernetes를 사용하여 개발 컴퓨터에서 실행되는 코드와 Kubernetes 클러스터 간에 트래픽을 리디렉션할 수 있습니다. Kubernetes 클러스터에 여러 개의 마이크로 서비스를 포함하여 대규모 애플리케이션 예제를 배포하는 스크립트도 제공됩니다.

## <a name="before-you-begin"></a>시작하기 전 주의 사항

이 가이드에서는 [TODO 애플리케이션 샘플][todo-app-github]을 사용하여 개발 컴퓨터를 Kubernetes 클러스터에 연결하는 방법을 보여 줍니다. 사용자 고유의 애플리케이션이 Kubernetes 클러스터에서 이미 실행 중인 경우에도 아래 단계를 수행하고 해당 서비스의 이름을 사용할 수 있습니다.

이 샘플에서는 Bridge to Kubernetes를 사용하여 Kubernetes 클러스터에서 간단한 TODO 애플리케이션의 마이크로 서비스 버전을 개발하는 방법을 보여 줍니다. Visual Studio를 사용하는 이 샘플은 [TodoMVC](http://todomvc.com)에서 제공하는 코드를 수정한 것입니다. 다음 단계는 어떤 Kubernetes 클러스터에서도 작동할 것입니다.

TODO 애플리케이션 샘플은 프런트 엔드와 영구 저장소를 제공하는 백 엔드로 구성됩니다. 이 확장 샘플에서는 통계 구성 요소를 추가하고 애플리케이션을 여러 마이크로 서비스로 분할합니다.

- 프런트 엔드는 database-api를 호출하여 할 일 항목을 유지 및 업데이트합니다.
- database-api 서비스는 Mongo 데이터베이스를 사용하여 할 일 항목을 유지합니다.
- 프런트 엔드는 RabbitMQ 큐에 추가, 완료 및 삭제 이벤트를 씁니다.
- 통계 작업자는 RabbitMQ 큐에서 이벤트를 수신하고 Redis 캐시를 업데이트합니다.
- 통계 API는 프런트 엔드가 표시할 캐시된 통계를 노출합니다.

결국, 이 확장된 TODO 애플리케이션은 6개의 상호 관련된 구성 요소로 구성됩니다.

### <a name="prerequisites"></a>필수 구성 요소

- Kubernetes 클러스터
- Windows 10에서 실행되는 [Visual Studio 2019][visual-studio] 버전 16.7 미리 보기 4 이상
- [Bridge to Kubernetes 확장 설치][btk-extension]

## <a name="check-the-cluster"></a>클러스터 확인

명령 프롬프트를 열고 kubectl이 경로에 설치되어 있는지, 사용하려는 클러스터가 사용 가능하고 준비된 상태인지, 컨텍스트가 해당 클러스터로 설정되었는지 확인합니다.

```cmd
kubectl cluster-info
kubectl config use-context {context-name}
```

여기서 {context-name}은 TODO 애플리케이션 샘플에 사용하려는 클러스터의 컨텍스트 이름입니다.

## <a name="deploy-the-application"></a>애플리케이션 배포

[mindaro 리포지토리](https://github.com/Microsoft/mindaro)를 복제하고 *samples/todo-app* 을 현재 작업 폴더로 하여 명령 창을 엽니다.

샘플을 위한 네임스페이스를 만듭니다.

```cmd
kubectl create namespace todo-app
```

그런 다음 배포 매니페스트를 적용합니다.

```cmd
kubectl apply -n todo-app -f deployment.yaml
```

이는 `LoadBalancer` 유형의 서비스를 사용하여 프런트 엔드를 노출하는 간단한 배포입니다. 모든 Pod가 실행 중이고 `frontend` 서비스의 외부 IP를 사용할 수 있을 때까지 기다립니다.

MiniKube를 사용하여 테스트하는 경우에는 `minikube tunnel`을 사용하여 외부 IP를 확인해야 합니다. AKS 또는 다른 클라우드 기반 Kubernetes 공급자를 사용하는 경우에는 외부 IP가 자동으로 할당됩니다. 다음 명령을 사용하여 `frontend` 서비스를 모니터링하여 서비스가 실행될 때까지 기다립니다.

```output
kubectl get service -n todo-app frontend --watch

NAME       TYPE           CLUSTER-IP    EXTERNAL-IP     PORT(S)        AGE
frontend   LoadBalancer   10.0.245.78   20.73.226.228   80:31910/TCP   6m26s
```

외부 IP 및 로컬 포트(포트 열의 첫 번째 숫자)를 사용하여 애플리케이션으로 이동합니다.

```
http://{external-ip}:{local-port}
```

브라우저에서 실행 중인 애플리케이션을 테스트합니다. 할 일 항목을 추가, 완료 및 삭제하면 통계 페이지가 예상된 메트릭을 사용하여 업데이트됩니다.

## <a name="connect-to-your-cluster-and-debug-a-service"></a>클러스터에 연결 및 서비스 디버그

Visual Studio에서 *samples\todo-app\database-api\database-api.csproj* 를 엽니다. 아래 그림과 같이 프로젝트의 시작 설정 드롭다운에서 **Bridge to Kubernetes** 를 선택합니다.

![Bridge to Kubernetes 선택](media/bridge-to-kubernetes/choose-bridge-to-kubernetes.png)

*Bridge to Kubernetes* 옆에 있는 시작 단추를 클릭합니다. **Bridge to Kubernetes의 프로필 만들기** 대화 상자에서 다음을 수행합니다.

- 클러스터 이름을 선택합니다.
- 네임스페이스로 *todo-app* 을 선택합니다.
- 리디렉션할 서비스로 *database-api* 를 선택합니다.
- 이전에 브라우저를 시작하는 데 사용한 것과 동일한 URL(http://{external-ip}:{local-port})을 선택합니다.

![Bridge to Kubernetes 클러스터 선택](media/bridge-to-kubernetes/configure-bridge-debugging.png)

클러스터를 사용하는 다른 사용자가 변경 내용의 영향을 받지 않는 격리된 상태로 실행할지 여부를 선택합니다. 해당 격리 모드는 영향을 받는 각 서비스의 복사본으로 요청을 라우팅하고 다른 모든 트래픽을 정상적으로 라우팅하는 방식으로 수행됩니다. 해당 작업을 수행하는 방법에 관한 자세한 설명은 [Bridge to Kubernetes 작동 방식][btk-overview-routing]을 참조하세요.

**확인** 을 클릭합니다. *database-api* 서비스에 대한 Kubernetes 클러스터의 모든 트래픽이 개발 컴퓨터에서 실행되는 애플리케이션 버전으로 리디렉션됩니다. 또한 Bridge to Kubernetes는 애플리케이션의 모든 아웃바운드 트래픽을 Kubernetes 클러스터로 다시 라우팅합니다.

> [!NOTE]
> *EndpointManager* 가 관리자 권한으로 실행되고 hosts 파일을 수정할 수 있게 허용하라는 메시지가 표시됩니다.

상태 표시줄에 `database-api` 서비스에 연결되었다고 표시되면 개발 컴퓨터가 연결된 것입니다.

![개발 컴퓨터 연결됨](media/bridge-to-kubernetes/development-computer-connected.png)

> [!NOTE]
> 이후 시작 시 **Bridge to Kubernetes의 프로필 만들기** 대화 상자가 표시됩니다. 해당 설정은 프로젝트 속성의 **디버그** 창에서 업데이트합니다.

개발 컴퓨터가 연결되면 바꾸려는 서비스에 대한 트래픽이 개발 컴퓨터로 리디렉션되기 시작합니다.

> [!NOTE]
> 다른 Kubernetes 서비스를 사용하여 테스트하려는 경우 예를 들어 디버그 프로필을 나중에 편집하려면 **디버그** > **디버그 속성** 을 선택하고 **변경** 단추를 클릭합니다.

## <a name="set-a-break-point"></a>중단점 설정

MongoHelper.cs를 열고 CreateTask 메서드의 줄 68에서 어딘가를 클릭하여 커서를 놓습니다. *F9* 키를 누르거나 **디버그** > **중단점 설정/해제** 를 선택하여 중단점을 설정합니다.

공용 URL(프런트 엔드 서비스의 외부 IP 주소)을 열어서 샘플 애플리케이션으로 이동합니다. 서비스를 다시 시작하려면 **F5** 키를 누르거나 **디버그** > **계속** 을 클릭합니다.

커서를 줄 위에 놓고 **F9** 키를 눌러 중단점을 제거합니다.

> [!NOTE]
> 기본적으로 디버깅 작업을 중지하면 Kubernetes 클러스터에서 개발 컴퓨터의 연결이 끊어집니다. **도구** > **옵션** 대화 상자의 **Kubernetes 디버깅 도구** 섹션에서 **디버깅 후 연결 끊기** 를 `false`로 변경하면 이 동작을 변경할 수 있습니다. 이 설정을 업데이트하면 디버깅을 중지하고 시작할 때 개발 컴퓨터가 연결된 상태를 유지합니다. 클러스터에서 개발 컴퓨터의 연결을 끊으려면 도구 모음에서 ‘연결 끊기’ 단추를 클릭합니다.
>
>![Kubernetes 디버깅 옵션의 스크린샷](media/bridge-to-kubernetes/kubernetes-debugging-options.png)

## <a name="additional-configuration"></a>추가 구성

Bridge to Kubernetes는 추가 구성 없이 트래픽 라우팅 및 환경 변수 복제를 처리할 수 있습니다. Kubernetes 클러스터의 컨테이너에 탑재된 파일(예: ConfigMap 파일)을 다운로드해야 하는 경우 `KubernetesLocalProcessConfig.yaml`을 만들어 해당 파일을 개발용 컴퓨터에 다운로드할 수 있습니다. 자세한 내용은 [Bridge to Kubernetes의 추가 구성에 KubernetesLocalProcessConfig.yaml 사용][kubernetesLocalProcessConfig-yaml]을 참조하세요.

## <a name="using-logging-and-diagnostics"></a>로깅 및 진단 사용

개발 컴퓨터의 *TEMP* 디렉터리에 있는 `Bridge to Kubernetes` 디렉터리에서 진단 로그를 찾을 수 있습니다.

## <a name="next-steps"></a>다음 단계

Bridge to Kubernetes 작동 방식을 알아봅니다.

> [!div class="nextstepaction"]
> [Bridge to Kubernetes 작동 방식](overview-bridge-to-kubernetes.md)

[todo-app-github]: https://github.com/Microsoft/mindaro
[supported-regions]: https://azure.microsoft.com/global-infrastructure/services/?products=kubernetes-service
[troubleshooting]: /azure/dev-spaces/troubleshooting#fail-to-restore-original-configuration-of-deployment-on-cluster
[visual-studio]: https://www.visualstudio.com/vs/
[btk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
[kubernetesLocalProcessConfig-yaml]: configure-bridge-to-kubernetes.md
[btk-overview-routing]: overview-bridge-to-kubernetes.md#using-routing-capabilities-for-developing-in-isolation
---
title: Bridge to Kubernetes의 추가 구성에 KubernetesLocalProcessConfig.yaml 사용
services: azure-dev-spaces
ms.date: 07/28/2020
ms.topic: conceptual
description: KubernetesLocalProcessConfig.yaml을 사용한 Bridge to Kubernetes의 추가 구성 옵션을 설명합니다.
keywords: Bridge to Kubernetes, Azure Dev Spaces, Dev Spaces, Docker, Kubernetes, Azure, AKS, Azure Kubernetes Service, 컨테이너
monikerRange: '>=vs-2019'
author: ghogen
ms.author: ghogen
manager: jillfra
ms.openlocfilehash: bd28921b7812689554e1dd707c500434bb021c9c
ms.sourcegitcommit: f9179a3a6d74fbd871f62b72491e70b9e7b05637
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90845955"
---
# <a name="configure-bridge-to-kubernetes"></a>Bridge to Kubernetes 구성

`KubernetesLocalProcessConfig.yaml` 파일을 사용하면 AKS 클러스터의 Pod에 사용할 수 있는 환경 변수 및 탑재된 파일을 복제할 수 있습니다. `KubernetesLocalProcessConfig.yaml` 파일에서 다음 작업을 지정할 수 있습니다.

* 볼륨을 다운로드하고 해당 볼륨의 경로를 환경 변수로 설정합니다.
* 클러스터에서 실행되는 서비스를 개발용 컴퓨터에서 실행 중인 프로세스에서 사용할 수 있도록 합니다.
* 상수 값을 사용하여 환경 변수를 만듭니다.

기본 `KubernetesLocalProcessConfig.yaml` 파일은 자동으로 생성되지 않으므로 프로젝트의 루트에서 수동으로 파일을 만들어야 합니다.

## <a name="download-a-volume"></a>볼륨 다운로드

*env*에서 다운로드하려는 각 볼륨에 대해 *name* 및 *value*를 지정합니다. *name*은 개발용 컴퓨터에서 사용할 환경 변수입니다. *value*는 볼륨의 이름과 개발용 컴퓨터의 경로입니다. *value* 값은 *$(volumeMounts:VOLUME_NAME)/PATH/TO/FILES* 형식입니다.

예를 들어:

```yaml
version: 0.1
env:
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
```

위의 예제에서는 컨테이너에서 *allow-list* 볼륨을 다운로드하고 해당 위치 및 환경 변수 *ALLOW_LIST_PATH*에 대한 경로를 설정합니다. 기본 동작은 개발 컴퓨터의 임시 디렉터리에서 지정한 경로에 파일을 다운로드하는 것입니다. 위의 예제에서 *ALLOW_LIST_PATH*는 `/TEMPORARY_DIR/allow-list`로 설정되어 있습니다. 

> [!NOTE]
> 볼륨을 다운로드하면 설정한 경로에 관계없이 해당 볼륨의 전체 콘텐츠가 다운로드됩니다. 이 경로는 개발용 컴퓨터에서 사용할 환경 변수를 설정하는 데만 사용됩니다. 토큰의 끝에 */allow-list* 또는 */path/to/files*를 추가하는 것은 실제로 볼륨이 유지되는 위치에 영향을 주지 않습니다. 환경 변수는 앱이 해당 볼륨 내의 특정 파일에 대한 참조를 필요로 하는 경우 사용하기 위한 편의 기능일 뿐입니다.

임시 디렉터리를 사용하는 대신 개발 컴퓨터에 볼륨 탑재를 다운로드할 위치를 지정하는 방법도 있습니다. *volumeMounts*에서 각 특정 위치에 대한 *name* 및 *localPath*를 지정합니다. *name*은 일치시키려는 볼륨 이름이고 *localPath*는 개발 컴퓨터의 절대 경로입니다. 예를 들어:

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
```

위의 예제에서는 *env*의 항목을 사용하여 *default-token-1111* 또는 *default-token-1234-5678-90abcdef*와 같이 *default-token-\** 과 일치하는 볼륨을 다운로드합니다. 여러 볼륨이 일치하는 경우 첫 번째 일치하는 볼륨이 사용됩니다. 모든 파일은 *volumeMounts*의 항목을 사용하여 개발용 컴퓨터의 `/var/run/secrets/kubernetes.io/serviceaccount`에 다운로드됩니다. *KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE* 환경 변수는 `/var/run/secrets/kubernetes.io/serviceaccount`로 설정되어 있습니다.

## <a name="make-a-service-available"></a>서비스를 사용할 수 있도록 설정

*env*에서 개발용 컴퓨터에서 사용할 수 있도록 설정할 각 서비스에 대해 *name* 및 *value*를 지정합니다. *name*은 개발용 컴퓨터에서 사용할 환경 변수입니다. *value*는 클러스터의 서비스 이름과 경로입니다. *value* 값은 *$(services:SERVICE_NAME)/PATH* 형식입니다.

예를 들어:

```yaml
version: 0.1
env:
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
```

위의 예제에서는 *myapp1* 서비스를 개발용 컴퓨터에서 사용할 수 있도록 설정하며, *MYAPP1_SERVICE_HOST* 환경 변수를 경로가 `/api/v1`인 *myapp1* 서비스의 로컬 IP 주소(즉 `127.1.1.4/api/v1`)로 설정합니다. *myapp1* 서비스는 환경 변수 *myapp1* 또는 *myapp1.svc.cluster.local*을 사용하여 액세스할 수 있습니다.

> [!NOTE]
> 서비스를 개발용 컴퓨터에서 사용할 수 있도록 설정하면 설정된 경로에 관계없이 전체 서비스를 사용할 수 있게 됩니다. 이 경로는 개발용 컴퓨터에서 사용할 환경 변수를 설정하는 데만 사용됩니다.
*$(services:SERVICE_NAME.NAMESPACE_NAME)* 을 사용하여 특정 Kubernetes 네임스페이스의 서비스를 사용할 수 있도록 설정할 수도 있습니다. 예를 들어:

```yaml
version: 0.1
env:
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
```

위의 예제에서는 *mynamespace*의 *myapp2*를 개발용 컴퓨터에서 사용할 수 있도록 설정하며 *MYAPP2_SERVICE_HOST* 환경 변수를 *mynamespace* 네임스페이스의 *myapp2*의 로컬 IP 주소로 설정합니다.

## <a name="create-an-environment-variable-with-a-constant-value"></a>상수 값을 사용하여 환경 변수 만들기

*env*에서 개발용 컴퓨터에 생성하려는 각 환경 변수에 대해 *name* 및 *value*를 지정합니다. *name*은 개발 컴퓨터에서 사용할 환경 변수이고 *value*는 값입니다. 예를 들어:

```yaml
version: 0.1
env:
  - name: DEBUG_MODE
    value: "true"
```

위의 예제에서는 *true* 값을 사용하여 *DEBUG_MODE*라는 환경 변수를 만듭니다.

## <a name="example-kuberneteslocalprocessconfigyaml"></a>Example KubernetesLocalProcessConfig.yaml

전체 `KubernetesLocalProcessConfig.yaml` 파일의 예는 다음과 같습니다.

```yaml
version: 0.1
volumeMounts:
  - name: default-token-*
    localPath: /var/run/secrets/kubernetes.io/serviceaccount
env:
  - name: KUBERNETES_IN_CLUSTER_CONFIG_OVERRIDE
    value: $(volumeMounts:default-token-*)
  - name: ALLOW_LIST_PATH
    value: $(volumeMounts:allow-list)/allow-list
  - name: MYAPP1_SERVICE_HOST
    value: $(services:myapp1)/api/v1/
  - name: MYAPP2_SERVICE_HOST
    value: $(services:myapp2.mynamespace)
  - name: DEBUG_MODE 
    value: "true"
```

## <a name="next-steps"></a>다음 단계

Bridge to Kubernetes를 사용하여 클러스터에 로컬 개발용 컴퓨터를 연결하려면 [Visual Studio Code에서 Bridge to Kubernetes 사용][bridge-to-kubernetes-vs-code] 및 [Visual Studio에서 Bridge to Kubernetes 사용][bridge-to-kubernetes-vs]을 참조하세요.

[bridge-to-kubernetes-vs-code]: https://code.visualstudio.com/docs/containers/bridge-to-kubernetes
[bridge-to-kubernetes-vs]: bridge-to-kubernetes.md

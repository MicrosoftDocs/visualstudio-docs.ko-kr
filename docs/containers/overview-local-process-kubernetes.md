---
title: Kubernetes를 사용하는 로컬 프로세스의 작동 방식
ms.technology: vs-azure
ms.date: 06/02/2020
ms.topic: conceptual
description: Kubernetes와 함께 로컬 프로세스를 사용하여 개발 컴퓨터를 Kubernetes 클러스터에 연결하는 프로세스에 대해 설명합니다.
keywords: Kubernetes와 함께 로컬 프로세스 사용, Docker, Kubernetes, Azure, 컨테이너
monikerRange: '>=vs-2019'
ms.openlocfilehash: adde9d8ecab93bdb6f0aebbd74730ef60bd80cf6
ms.sourcegitcommit: 510a928153470e2f96ef28b808f1d038506cce0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86454374"
---
# <a name="how-local-process-with-kubernetes-works"></a>Kubernetes를 사용하는 로컬 프로세스의 작동 방식

Kubernetes와 함께 로컬 프로세스를 사용하면 나머지 애플리케이션 또는 서비스가 포함된 Kubernetes 클러스터에 연결된 상태로 개발 컴퓨터에서 코드를 실행하고 디버그할 수 있습니다. 예를 들어 많은 상호 종속적 서비스 및 데이터베이스를 포함하는 대규모 마이크로 서비스 아키텍처가 있는 경우 이러한 종속성을 개발 컴퓨터에 복제하기 어려울 수 있습니다. 또한 내부 루프 개발 중에 각 코드 변경을 위한 코드를 빌드하여 Kubernetes 클러스터에 배포하는 작업은 속도가 느리고 시간이 오래 걸리고 디버거와 함께 사용하기 어려울 수 있습니다.

Kubernetes와 함께 로컬 프로세스를 사용하면 코드를 빌드하여 클러스터에 배포할 필요 없이 개발 컴퓨터와 클러스터 간에 직접 연결할 수 있습니다. 디버그하는 동안 개발 컴퓨터를 클러스터에 연결하면 Docker 또는 Kubernetes 구성을 만들지 않고도 전체 애플리케이션의 컨텍스트에서 서비스를 신속하게 테스트하고 개발할 수 있습니다.

Kubernetes와 함께 로컬 프로세스를 사용하면 연결된 Kubernetes 클러스터와 개발 컴퓨터 간에 트래픽이 리디렉션됩니다. 이러한 트래픽 리디렉션을 통해 Kubernetes 클러스터에서 실행되는 서비스와 개발 컴퓨터의 코드가 동일한 Kubernetes 클러스터에 있는 것처럼 통신할 수 있습니다. Kubernetes와 함께 로컬 프로세스를 사용하면 Kubernetes 클러스터의 Pod에서 사용할 수 있는 환경 변수 및 탑재 볼륨을 개발 컴퓨터에 복제할 수도 있습니다. 개발 컴퓨터의 환경 변수 및 탑재 볼륨에 대한 액세스를 제공함으로써 해당 종속성을 수동으로 복제하지 않고도 코드 작업을 빠르게 수행할 수 있습니다.

## <a name="using-local-process-with-kubernetes"></a>Kubernetes와 함께 로컬 프로세스를 사용

Visual Studio에서 Kubernetes와 함께 로컬 프로세스를 사용하려면 ‘ASP.NET 및 웹 개발’ 워크로드와 [로컬 프로세스 Kubernetes 확장][lpk-extension]이 설치되어 있는 Windows 10에서 실행되는 [Visual Studio 2019][visual-studio] 버전 16.7 미리 보기 4 이상이 필요합니다. Kubernetes와 함께 로컬 프로세스를 사용하여 Kubernetes 클러스터에 연결하는 경우 클러스터의 기존 Pod로 들어오고 나가는 모든 트래픽을 개발 컴퓨터로 리디렉션할 수 있습니다.

> [!NOTE]
> Kubernetes와 함께 로컬 프로세스를 사용하는 경우 개발 컴퓨터로 리디렉션할 서비스의 이름을 묻는 메시지가 표시됩니다. 이 옵션은 리디렉션에 사용할 Pod를 확인하는 편리한 방법입니다. Kubernetes 클러스터와 개발 컴퓨터 간의 모든 리디렉션은 Pod에 적용됩니다.

Kubernetes와 함께 로컬 프로세스를 사용하여 클러스터에 연결하는 경우 프로세스에서 다음 작업을 수행합니다.

* 클러스터에서 바꿀 서비스, 코드에 사용할 개발 컴퓨터의 포트, 일회성 작업인 코드 시작 작업을 구성하라는 메시지를 표시합니다.
* 클러스터의 Pod에 있는 컨테이너를 트래픽이 개발 컴퓨터로 리디렉션되는 원격 에이전트 컨테이너로 바꿉니다.
* 개발 컴퓨터에서 [kubectl port-forward][kubectl-port-forward]를 실행하여 개발 컴퓨터의 트래픽을 클러스터에서 실행되는 원격 에이전트로 전달합니다.
* 원격 에이전트를 사용하여 클러스터에서 환경 정보를 수집합니다. 이 환경 정보에는 환경 변수, 표시되는 서비스, 볼륨 탑재, 비밀 탑재가 포함됩니다.
* 개발 컴퓨터의 서비스가 클러스터에서 실행되는 것처럼 동일한 변수에 액세스할 수 있도록 Visual Studio에서 환경을 설정합니다.  
* hosts 파일을 업데이트하여 클러스터의 서비스를 개발 컴퓨터의 로컬 IP 주소에 매핑합니다. 이러한 hosts 파일 항목을 사용하면 개발 컴퓨터에서 실행되는 코드를 통해 클러스터에서 실행되는 다른 서비스에 요청을 수행할 수 있습니다. Kubernetes와 함께 로컬 프로세스를 사용하는 경우 hosts 파일을 업데이트하기 위해 클러스터에 연결할 때 개발 컴퓨터에 대한 관리자 액세스 권한이 요청됩니다.
* 개발 컴퓨터에서 코드 실행 및 디버깅을 시작합니다. Kubernetes와 함께 로컬 프로세스를 사용하는 경우 필요하다면 현재 개발 컴퓨터에서 필요한 포트를 사용 중인 서비스나 프로세스를 중지하여 해당 포트를 해제합니다.

클러스터에 연결한 후에는 컨테이너화하지 않고 컴퓨터에서 기본적으로 코드를 실행하고 디버그할 수 있으며, 코드가 클러스터의 나머지 부분과 직접 상호 작용할 수 있습니다. 기본적으로 실행되는 코드가 트래픽을 수락하고 처리할 수 있도록 원격 에이전트가 수신하는 모든 네트워크 트래픽이 연결 중에 지정한 로컬 포트로 리디렉션됩니다. 개발 컴퓨터에서 실행되는 코드가 클러스터의 환경 변수, 볼륨, 비밀을 사용할 수 있습니다. 또한 Kubernetes와 함께 로컬 프로세스를 사용하는 경우 개발자 컴퓨터에 추가되는 hosts 파일 항목 및 포트 전달 기능 때문에 코드에 클러스터의 서비스 이름을 사용하여 네트워크 트래픽을 클러스터에서 실행되는 서비스로 보낼 수 있으며, 해당 트래픽은 클러스터에서 실행되는 서비스로 전달됩니다. 연결된 시간 동안 계속해서 개발 컴퓨터와 클러스터 간에 트래픽이 라우팅됩니다.

## <a name="diagnostics-and-logging"></a>진단 및 로깅

Kubernetes와 함께 로컬 프로세스를 사용하여 클러스터에 연결하는 경우 클러스터의 진단 로그가 개발 컴퓨터의 [임시 디렉터리][azds-tmp-dir]에 기록됩니다.

## <a name="limitations"></a>제한 사항

Kubernetes와 함께 로컬 프로세스를 사용하는 경우 다음과 같은 제한 사항이 있습니다.

* Kubernetes와 함께 로컬 프로세스를 사용하는 경우 단일 서비스의 트래픽이 개발 컴퓨터로 리디렉션됩니다. Kubernetes와 함께 로컬 프로세스를 사용하여 여러 서비스를 동시에 리디렉션할 수는 없습니다.
* 단일 Pod의 지원을 받는 서비스에만 연결할 수 있습니다. 복제본이 있는 서비스와 같이 여러 개의 Pod가 있는 서비스에는 연결할 수 없습니다.
* Kubernetes와 함께 로컬 프로세스를 사용하여 성공적으로 연결하려면 Pod에 단일 컨테이너만 실행되고 있어야 합니다. 서비스 메시를 통해 삽입된 사이드카 컨테이너와 같은 추가 컨테이너를 포함하는 Pod가 있는 서비스의 경우 Kubernetes와 함께 로컬 프로세스를 사용하여 연결할 수 없습니다.
* 개발 컴퓨터에서 Kubernetes와 함께 로컬 프로세스를 실행하려면 hosts 파일을 편집하기 위해 관리자 권한이 필요합니다.

## <a name="next-steps"></a>다음 단계

Kubernetes와 함께 로컬 프로세스를 사용하여 로컬 개발 컴퓨터를 클러스터에 연결하려면 [Kubernetes와 함께 로컬 프로세스 사용](local-process-kubernetes.md)을 참조하세요.

[azds-cli]: /azure/dev-spaces/how-to/install-dev-spaces#install-the-client-side-tools
[azds-tmp-dir]: /azure/dev-spaces/troubleshooting#before-you-begin
[azure-cli]: /cli/azure/install-azure-cli?view=azure-cli-latest
[local-process-kubernetes-vs]: local-process-kubernetes.md
[kubectl-port-forward]: https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#port-forward
[visual-studio]: https://visualstudio.microsoft.com/downloads/
[lpk-extension]: https://marketplace.visualstudio.com/items?itemName=ms-azuretools.mindaro
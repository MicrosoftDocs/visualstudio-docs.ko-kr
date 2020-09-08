---
title: Docker 자습서 - 다음 단계
description: Cloud Native Computing Foundation 프로젝트를 사용하여 오케스트레이션으로 Docker 앱을 확장하는 옵션을 설명합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f93185641a0814797b66eae90714e04cac83f7e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176791"
---
# <a name="whats-next"></a>새로운 기능

자습서를 완료했지만 컨테이너에 대해 알아 두어야 할 사항이 아직 많습니다.
여기서 자세히 설명하지는 않지만, 아래 몇 개의 영역을 다음 단계에서 살펴볼 수 있습니다.

## <a name="container-orchestration"></a>컨테이너 오케스트레이션

프로덕션 환경에서 컨테이너를 실행하는 것은 매우 어렵습니다. 머신에 로그인하지 않고 `docker run` 또는 `docker-compose up`만 실행하고 싶을 수도 있습니다. 이유는 무엇입니까? 컨테이너 작동이 중단되면 어떻게 될까요? 여러 머신에 걸쳐 스케일링하는 방법은 무엇일까요? 컨테이너 오케스트레이션을 통해 이 문제를 해결할 수 있습니다. Kubernetes, Swarm, Nomad, AKS와 같은 도구는 모두 조금씩 다른 방식으로 이 문제의 해결을 지원합니다.

일반적으로 **예상 상태**를 받는 “관리자”가 있다고 가정합니다. 이 상태는 “웹앱 인스턴스 2개를 실행하고 포트 80을 노출하려고 합니다.”일 수 있습니다. 관리자는 클러스터의 모든 머신을 확인하고 “작업자” 노드에 작업을 위임합니다. 관리자는 컨테이너 종료 등의 변경 내용을 감시하고 **실제 상태**가 예상 상태를 반영하게 합니다.

## <a name="cloud-native-computing-foundation-projects"></a>Cloud Native Computing Foundation 프로젝트

CNCF는 Kubernetes, 프로메테우스, Prometheus, Envoy, Linkerd, NATS 등을 포함하여 다양한 오픈 소스 프로젝트의 공급업체 중립적 홈입니다. [종료된 프로젝트 및 신규 프로젝트](https://www.cncf.io/projects/)와 전체 [CNCF 환경](https://landscape.cncf.io/)을 볼 수 있습니다. 모니터링, 로깅, 보안, 이미지 레지스트리, 메시징 등과 관련된 문제 해결에 도움이 되는 많은 프로젝트가 있습니다.

컨테이너 환경과 클라우드 네이티브 애플리케이션 개발을 처음 사용하시는 분도 모두 환영합니다. 커뮤니티에 연결해서 궁금한 사항을 묻고 새로운 지식을 습득하세요! 방문해 주셔서 감사합니다.

## <a name="working-with-docker-in-vs-code"></a>VS Code에서 Docker 작업

VS Code Docker 확장을 사용하는 방법을 자세히 알아봅니다.

- [VS Code Docker 확장 개요](https://code.visualstudio.com/docs/containers/overview)
- [Node.js 시작](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Python 시작](https://code.visualstudio.com/docs/containers/quickstart-python)
- [.NET Core 시작](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [컨테이너화된 앱 디버그](https://code.visualstudio.com/docs/containers/debug-common)

---
title: Docker 자습서-다음 단계
description: Cloud Native 컴퓨팅 기반 프로젝트를 사용 하 여 오케스트레이션을 사용 하 여 Docker 앱을 확장 하는 옵션을 설명 합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f93185641a0814797b66eae90714e04cac83f7e5
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176791"
---
# <a name="whats-next"></a>새로운 기능

자습서를 완료 했지만 컨테이너에 대해 더 자세히 알아볼 수 있습니다.
여기서 자세히 알아볼 수는 없지만 다음 몇 가지 영역에서 살펴볼 수 있습니다.

## <a name="container-orchestration"></a>컨테이너 오케스트레이션

프로덕션 환경에서 컨테이너를 실행 하는 것은 매우 어렵습니다. 컴퓨터에 로그인 하지 않고 또는를 실행 합니다 `docker run` `docker-compose up` . 이유는 무엇입니까? 컨테이너가 죽을 경우 어떻게 되나요? 여러 컴퓨터에서 크기를 조정 하는 방법 컨테이너 오케스트레이션이이 문제를 해결 합니다. Kubernetes, Swarm, Nomad 및 AKS와 같은 도구는 모두 약간 다른 방식으로이 문제를 해결 하는 데 도움이 됩니다.

일반적인 개념은 **예상 된 상태**를 받는 "관리자"가 있다는 것입니다. 이 상태는 "웹 앱의 두 인스턴스를 실행 하 고 포트 80을 노출 하려고 합니다." 일 수 있습니다. 그런 다음 관리자는 클러스터의 모든 컴퓨터를 확인 하 고 "작업자" 노드에 작업을 위임 합니다. 관리자는 컨테이너를 종료 하는 등의 변경 내용을 감시 한 다음 **실제 상태가** 예상 상태를 반영 하도록 합니다.

## <a name="cloud-native-computing-foundation-projects"></a>클라우드 네이티브 컴퓨팅 기반 프로젝트

CNCF는 Kubernetes, 프로메테우스, 엔보이, Linkerd, NAT 등을 비롯 한 다양 한 오픈 소스 프로젝트용 공급 업체 중립적 홈입니다. 여기에서 [그라데이션 및 incubated 프로젝트](https://www.cncf.io/projects/) 를 볼 수 있으며 여기에서 전체 [cncf 가로](https://landscape.cncf.io/)를 볼 수 있습니다. 모니터링, 로깅, 보안, 이미지 레지스트리, 메시징 등과 관련 된 문제를 해결 하는 데 도움이 되는 많은 프로젝트가 있습니다.

따라서 컨테이너의 가로 및 클라우드 네이티브 응용 프로그램 개발을 처음 접하는 경우에는 환영 합니다. 커뮤니티에 연결 하 고, 질문 하 고, 계속 학습 하세요! 여러분의 기대를 기대 하 고 있습니다.

## <a name="working-with-docker-in-vs-code"></a>VS Code에서 Docker 작업

VS Code Docker 확장 사용에 대해 자세히 알아보세요.

- [VS Code Docker 확장 개요](https://code.visualstudio.com/docs/containers/overview)
- [Node.js시작 ](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Python 시작](https://code.visualstudio.com/docs/containers/quickstart-python)
- [.NET Core 시작](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [컨테이너 화 된 앱 디버그](https://code.visualstudio.com/docs/containers/debug-common)

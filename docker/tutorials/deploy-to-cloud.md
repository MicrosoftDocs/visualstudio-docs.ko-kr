---
title: 'Docker 자습서-9 부: 클라우드에 배포'
description: 호스팅을 위해 클라우드 서비스에 docker 앱을 배포 합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176859"
---
# <a name="deploy-to-the-cloud"></a>클라우드에 배포

응용 프로그램을 로컬로 실행 했으므로 다른 사용자가 액세스 하 여 사용할 수 있도록 클라우드에서 실행 하는 것을 고려할 수 있습니다. 이렇게 하려면 Docker 컨텍스트를 사용 합니다. 컨텍스트는 현재 컨테이너를 사용 하는 위치입니다. 지금은 "기본" 컨텍스트가 있으므로 클라우드를 추가 하 고 앱을 배포 해야 합니다.

## <a name="create-your-cloud-context"></a>클라우드 컨텍스트 만들기

1. 시작 하려면 Docker 패널의 컨텍스트 섹션을 살펴보면 어떤 컨텍스트가 있는지 확인할 수 있습니다.

   ![기본 컨텍스트를 표시 합니다.](media/defaultcontext.png)

로컬 작업에 대 한 기본 컨텍스트를 확인 해야 합니다.

1. 클라우드에 배포 하려면 새 ACI 컨텍스트를 만들어야 합니다 .이 작업을 수행 하려면 먼저 azure로 인증 하는 데 Azure 계정 확장이 필요 합니다.

   ![Azure 확장 추가](media/addazureextension.png)

아직 없는 경우 Azure 계정을 설정 해야 합니다.

1. 이제 새 ACI 컨텍스트를 만들 수 있습니다. Docker 보기의 **컨텍스트** 섹션에서 더하기 단추를 클릭 하 여이 작업을 수행할 수 있습니다.

   ![ACI 컨텍스트 만들기](media/createnewcontext.png)

그러면 이러한 컨테이너를 실행 하는 데 사용할 리소스 그룹을 묻는 메시지가 표시 됩니다. 화살표 키를 사용 하 여 기존 그룹을 선택 하거나 기본 옵션을 사용 하 여 새 그룹을 사용 합니다.

![리소스 그룹 선택](media/selectresourcegroup.png)

이제 ACI 컨텍스트가 나열 된 것을 확인 하 고 마우스 오른쪽 단추를 클릭 하 여 현재 포커스/사용 컨텍스트로 만들 수 있습니다.

![새 ACI 컨텍스트를 선택할 수 있습니다.](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>클라우드에서 컨테이너 실행

1. 이제 ACI 컨텍스트를 사용 하 고 컨테이너를 실행 합니다.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. 이를 실행 한 후에는 컨텍스트에서 컨테이너를 확인 합니다.

   ![ACI 컨텍스트에서 실행 중인 컨테이너](media/contextcontainer.png)

1. 제대로 작동 하는지 확인 하려면 실행 중인 컨테이너를 마우스 오른쪽 단추로 클릭 하 고 **브라우저에서 보기**를 선택할 수 있습니다.

   ![공용 IP를 사용 하는 ACI의 컨테이너](media/containerinaci.png)

그리고 컨테이너가 공용 IP에서 실행 중이 고 제대로 작동 하 고 있음을 확인할 수 있습니다.

1. 이제 실행 중인 컨테이너를 확인 하 여 작동 방식을 확인할 수 있습니다. 컨테이너 로그를 살펴보면 다음과 같이 시작할 수 있습니다.
 
 ```bash
   docker logs distracted-jackson
   ```

1. 로컬 컨테이너와 마찬가지로 컨테이너로 실행할 수도 있습니다.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. 마지막으로 작업 공간을 정리 하 고 테스트 컨테이너 실행을 계속 하기 위해 요금이 부과 되지 않도록 하려면 실행 중인 컨테이너를 마우스 오른쪽 단추로 클릭 하 고 **제거**를 선택 하면 됩니다.

## <a name="recap"></a>요약

이제 워크 로드를 수행 하 고 처음으로 클라우드에 배포 했습니다. 를 사용 하 여 ACI 컨텍스트 내에서 뿐만 아니라를 사용 하 여 `docker run` `docker compose up` 다중 컨테이너 응용 프로그램을 실행 하는 경우에도 명령줄에서이 모든 작업을 수행할 수 있습니다. 클라우드에서 컨테이너를 실행 하는 방법에 대해 자세히 알아보려면 [ACI 사용에 대](https://docs.docker.com/engine/context/aci-integration/)한 확장 설명서를 참조 하세요.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행 합니다.

> [!div class="nextstepaction"]
> [다음 단계](whats-next.md)

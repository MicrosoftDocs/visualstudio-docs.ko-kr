---
title: 'Docker 자습서 - 9부: 클라우드에 배포'
description: 호스팅을 위해 클라우드 서비스에 Docker 앱을 배포합니다.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 661f9f6833b5ac5d42aacde7f228b042bef00bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176859"
---
# <a name="deploy-to-the-cloud"></a>클라우드에 배포

이제 로컬에서 앱을 실행했으므로, 다른 사용자가 앱에 액세스하여 사용할 수 있도록 클라우드에서 실행하는 방법을 고려할 수 있습니다. 이렇게 하려면 Docker 컨텍스트를 사용합니다. 컨텍스트는 현재 컨테이너를 사용하고 있는 곳입니다. 지금은 “기본” 컨텍스트뿐이므로 클라우드 컨텍스트를 추가하고 해당 컨텍스트에 앱을 배포해야 합니다.

## <a name="create-your-cloud-context"></a>클라우드 컨텍스트 만들기

1. 시작하려면 Docker 패널의 컨텍스트 섹션을 살펴보고 어떤 컨텍스트가 있는지 확인합니다.

   ![기본 컨텍스트만 표시됨](media/defaultcontext.png)

로컬 작업의 기본 컨텍스트만 표시됩니다.

1. 클라우드에 배포하려면 새 ACI 컨텍스트를 만들어야 하지만, 이 작업을 위해 Azure에 인증하려면 먼저 Azure 계정 확장이 필요합니다.

   ![Azure 확장 추가](media/addazureextension.png)

아직 없으면 Azure 계정을 설정해야 합니다.

1. 이제 새 ACI 컨텍스트를 만들 수 있습니다. Docker 뷰의 **컨텍스트** 섹션에서 더하기 단추를 클릭하면 됩니다.

   ![ACI 컨텍스트 만들기](media/createnewcontext.png)

해당 컨테이너를 실행하는 데 사용할 리소스 그룹을 묻는 메시지가 표시됩니다. 화살표 키를 사용하여 기존 그룹을 선택하거나 기본 옵션으로 새 그룹을 사용합니다.

![리소스 그룹 선택](media/selectresourcegroup.png)

해당 ACI 컨텍스트가 나열되는 것을 확인할 수 있으며, 마우스 오른쪽 단추로 클릭하여 현재 포커스/사용 중인 컨텍스트로 만들 수 있습니다.

![새 ACI 컨텍스트를 선택할 수 있음](media/listofcontexts.png)

## <a name="run-containers-in-the-cloud"></a>클라우드에서 컨테이너 실행

1. 해당 ACI 컨텍스트를 사용하여 컨테이너를 실행합니다.

   ```bash
   docker context use myacicontext
   docker run  -dp 3000:3000 <username>/getting-started
   ```

1. 컨테이너를 실행한 후 해당 컨텍스트에서 컨테이너를 살펴봅니다.

   ![해당 ACI 컨텍스트에서 실행되는 컨테이너](media/contextcontainer.png)

1. 모두 제대로 작동하는지 확인하려면 실행 중인 컨테이너를 마우스 오른쪽 단추로 클릭하고 **브라우저에서 보기**를 선택할 수 있습니다.

   ![공용 IP를 사용하는 ACI의 컨테이너](media/containerinaci.png)

컨테이너가 공용 IP에서 실행되어 제대로 작동하고 있음을 확인할 수 있습니다.

1. 이제 실행 중인 컨테이너를 살펴보고 작동 방식을 확인할 수 있습니다. 먼저 컨테이너 로그를 살펴볼 수 있습니다.
 
 ```bash
   docker logs distracted-jackson
   ```

1. 로컬 컨테이너와 마찬가지로 컨테이너로 실행할 수도 있습니다.
 
 ```bash
   docker exec -it distracted-jackson sh
   ```

1. 마지막으로, 작업 공간을 정리하고 테스트 컨테이너가 계속 실행되어 요금이 부과되는 경우를 방지하려면 실행 중인 컨테이너를 마우스 오른쪽 단추로 클릭하고 **제거**를 선택합니다.

## <a name="recap"></a>요약

잘하셨습니다. 워크로드를 클라우드에 처음으로 배포하는 데 성공했습니다. `docker run` 및 `docker compose up`(다중 컨테이너 애플리케이션을 실행하는 경우)을 사용하여 해당 ACI 컨텍스트뿐 아니라 명령줄에서도 이 작업을 모두 수행할 수 있습니다. 클라우드에서 컨테이너를 실행하는 방법에 대해 자세히 알아보려면 확장된 [ACI 사용 설명서](https://docs.docker.com/engine/context/aci-integration/)를 참조하세요.

## <a name="next-steps"></a>다음 단계

자습서를 계속 진행합니다.

> [!div class="nextstepaction"]
> [다음 단계](whats-next.md)

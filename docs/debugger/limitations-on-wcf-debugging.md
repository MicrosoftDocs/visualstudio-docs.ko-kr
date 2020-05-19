---
title: WCF 디버깅의 제한 사항 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c70195cdc0a6a03395744c63f556ce8c2970aa30
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731500"
---
# <a name="limitations-on-wcf-debugging"></a>WCF 디버깅의 제한 사항
다음 세 가지 방법으로 WCF 서비스의 디버깅을 시작할 수 있습니다.

- 서비스를 호출하는 클라이언트 프로세스를 디버깅합니다. 디버거가 서비스를 한 단계씩 실행합니다. 서비스가 클라이언트 애플리케이션과 같은 솔루션에 있지 않아도 됩니다.

- 서비스를 요청하는 클라이언트 프로세스를 디버깅합니다. 서비스가 솔루션의 일부여야 합니다.

- **프로세스에 연결**을 사용하여 현재 실행 중인 서비스에 연결합니다. 디버깅이 서비스 내에서 시작됩니다.

  이 항목에서는 이러한 시나리오에 적용되는 제한 사항에 대해 설명합니다.

## <a name="limitations-on-stepping-into-a-service"></a>서비스를 한 단계씩 실행하는 경우의 제한 사항
 디버깅할 클라이언트 애플리케이션에서 서비스를 한 단계씩 실행하려면 다음 조건이 충족되어야 합니다.

- 클라이언트에서 동기 클라이언트 개체를 사용하여 서비스를 호출해야 합니다.

- 계약 작업은 단방향일 수 없습니다.

- 서버가 비동기 상태인 경우 서비스 내에서 코드를 실행하는 동안 전체 호출 스택을 볼 수 없습니다.

- app.config 또는 Web.config 파일에서 다음 코드를 사용하여 디버깅을 사용하도록 설정해야 합니다.

    ```xml
    <system.web>
      <compilation debug="true" />
    </system.web>
    ```

     이 코드는 한 번만 추가하면 됩니다. **프로세스에 연결**을 사용하여 .config 파일을 편집하거나 서비스에 연결하여 이 코드를 추가할 수 있습니다. 서비스에서 **프로세스에 연결**을 사용하면 디버그 코드가 .config 파일에 자동으로 추가됩니다. 그러면 .config 파일을 편집할 필요 없이 서비스를 디버깅하고 한 단계씩 실행할 수 있습니다.

## <a name="limitations-on-stepping-out-of-a-service"></a>서비스를 나가는 경우의 제한 사항
 서비스에서 나가서 클라이언트로 돌아오는 경우에도 위에서 설명한 서비스를 한 단계씩 실행할 때와 동일한 제한 사항이 적용됩니다. 또한 이 경우에는 디버거가 클라이언트에 연결되어야 합니다. 클라이언트를 디버깅하고 서비스를 한 단계씩 실행하는 경우 디버거는 서비스에 연결된 상태로 유지됩니다. 이는 **디버깅 시작**을 사용하여 클라이언트를 시작했는지 또는 **프로세스에 연결**을 사용하여 클라이언트에 연결했는지에 관계없이 적용됩니다. 서비스에 연결하여 디버깅을 시작한 경우에는 디버거는 아직 클라이언트에 연결되지 않은 상태입니다. 이 경우 서비스에서 나가서 클라이언트로 돌아가려면 먼저 **프로세스에 연결**을 사용하여 클라이언트에 수동으로 연결해야 합니다.

## <a name="limitations-on-automatic-attach-to-a-service"></a>서비스에 자동으로 연결하는 경우의 제한 사항
 서비스에 자동으로 연결할 때는 다음과 같은 제한 사항이 적용됩니다.

- 서비스가 디버깅하는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 솔루션의 일부여야 합니다.

- 서비스가 호스팅되어야 합니다. 서비스가 웹 사이트 프로젝트(파일 시스템 및 HTTP), 웹 애플리케이션 프로젝트(파일 시스템 및 HTTP) 또는 WCF 서비스 라이브러리 프로젝트의 일부일 수 있습니다. WCF 서비스 라이브러리 프로젝트는 서비스 라이브러리 또는 워크플로 서비스 라이브러리일 수 있습니다.

- 서비스가 WCF 클라이언트에서 호출되어야 합니다.

- app.config 또는 Web.config 파일에서 다음 코드를 사용하여 디버깅을 사용하도록 설정해야 합니다.

  ```xml
  <system.web>
    <compilation debug="true" />
  <system.web>
  ```

## <a name="self-hosting"></a>자체 호스팅
 *자체 호스팅 서비스*는 IIS, WCF 서비스 호스트 또는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server 내에서 실행되지 않는 WCF 서비스입니다. 셀프 호스티드 서비스를 디버그하는 방법에 관한 자세한 내용은 [방법: 셀프 호스티드 WCF 서비스 디버그](../debugger/how-to-debug-a-self-hosted-wcf-service.md)를 참조하세요.

## <a name="self-hosting"></a>자체 호스팅
 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 또는 3.5 애플리케이션을 디버깅할 수 있으려면 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]를 설치하기 전에 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 또는 3.5를 설치해야 합니다. [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)]가 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 또는 3.5 이전에 설치된 경우 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 또는 3.5 애플리케이션을 디버깅하려고 하면 오류가 발생합니다. 오류 메시지는 "서버에 대해 자동으로 한 단계씩 코드를 실행할 수 없습니다."입니다. 이 문제를 해결하려면 Windows **제어판** > **프로그램 및 기능**을 사용하여 [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] 설치를 복구합니다.

## <a name="see-also"></a>참조
- [WCF 서비스 디버그](../debugger/debugging-wcf-services.md)
- [방법: 자체 호스팅 WCF 서비스 디버그](../debugger/how-to-debug-a-self-hosted-wcf-service.md)

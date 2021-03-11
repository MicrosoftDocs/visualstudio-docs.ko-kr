---
title: 셀프 호스티드 WCF 서비스 디버그 | Microsoft Docs
description: 자체 호스팅 WCF 서비스를 디버그하는 방법을 알아봅니다. 항상 가능하지는 않지만 가장 쉬운 방법은 클라이언트와 서버를 모두 시작하도록 Visual Studio를 구성합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3cd11966347cd90576eb78a59f6c7eb96cc697ef
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155083"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>방법: 자체 호스팅 WCF 서비스 디버그
*자체 호스팅 서비스* 는 IIS, WCF 서비스 호스트 또는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Development Server 내에서 실행되지 않는 WCF 서비스입니다. 셀프 호스티드 WCF를 디버그하는 가장 쉬운 방법은 **디버그** 메뉴에서 **디버깅 시작** 을 선택할 때 클라이언트와 서버를 둘 다 시작하도록 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]를 구성하는 것입니다.

 WCF 서비스가 내부에서 자체 호스트되거나 이 방식으로 시작할 수 없는 프로세스(예: NT 서비스)인 경우에는 이 방법을 사용할 수 없습니다. 대신에, 다음 방법 중 하나를 사용할 수 있습니다.

- 디버거를 호스팅 프로세스에 수동으로 연결합니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.

     — 또는 —

- 클라이언트 디버깅을 시작한 다음, 한 단계씩 서비스 호출을 실행합니다. 이렇게 하려면 app.config 파일에서 디버깅을 사용하도록 설정해야 합니다. 자세한 내용은 [WCF 디버깅에 대한 제한 사항](../debugger/limitations-on-wcf-debugging.md)을 참조하세요.

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Visual Studio에서 클라이언트 및 호스트를 둘 다 시작하려면

1. 클라이언트 및 서버 프로젝트를 둘 다 포함하는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 솔루션을 만듭니다.

2. **디버그** 메뉴에서 **시작** 을 선택할 때 클라이언트 및 서버 프로세스를 둘 다 시작하도록 솔루션을 구성합니다.

   1. **솔루션 탐색기** 에서 솔루션 이름을 마우스 오른쪽 단추로 클릭합니다.

   2. **시작 프로젝트 설정** 을 클릭합니다.

   3. **솔루션 \<name> 속성** 대화 상자에서 **여러 시작 프로젝트** 를 선택합니다.

   4. **여러 개의 시작 프로젝트** 표의 서버 프로젝트에 해당하는 줄에서 **작업** 을 클릭하고 **시작** 을 선택합니다.

   5. 클라이언트 프로젝트에 해당하는 줄에서 **작업** 을 클릭하고 **시작** 을 선택합니다.

   6. **확인** 을 클릭합니다.

## <a name="see-also"></a>참조
- [WCF 서비스 디버그](../debugger/debugging-wcf-services.md)
- [WCF 디버깅의 제한 사항](../debugger/limitations-on-wcf-debugging.md)
- [방법: WCF 서비스 한 단계씩 코드 실행](../debugger/how-to-step-into-wcf-services.md)

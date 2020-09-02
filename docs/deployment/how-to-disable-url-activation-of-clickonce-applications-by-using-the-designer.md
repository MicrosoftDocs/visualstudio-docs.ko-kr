---
title: 디자이너를 사용 하 여 ClickOnce 응용 프로그램의 URL 활성화 사용 안 함
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 818ab634d48fb666ecab5d89464ea017040bd250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382486"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>방법: 디자이너를 사용하여 ClickOnce 애플리케이션의 URL 활성화를 사용하지 않도록 설정
일반적으로 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램은 웹 서버에서 설치 된 직후 자동으로 시작 됩니다. 보안상의 이유로이 동작을 사용 하지 않도록 설정 하 고, 대신 **시작** 메뉴에서 응용 프로그램을 시작 하도록 사용자에 게 지시할 수 있습니다. 다음 절차에서는 URL 활성화를 사용하지 않도록 설정하는 방법에 대해 설명합니다.

 이 방법은 웹 서버에서 사용자 컴퓨터에 설치된 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션에 대해서만 사용할 수 있습니다. URL을 사용해 서만 시작할 수 있는 온라인 전용 응용 프로그램에는 사용할 수 없습니다. 온라인 전용 응용 프로그램과 설치 된 응용 프로그램 간의 차이점에 대 한 자세한 내용은 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)을 참조 하세요.

 이 절차에서는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 를 사용 합니다. 을 사용 하 여이 작업을 수행할 수도 있습니다 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . 자세한 내용은 [방법: ClickOnce 응용 프로그램의 URL 활성화 사용 안 함](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)을 참조 하세요.

## <a name="procedure"></a>프로시저

#### <a name="to-disable-url-activation-for-your-application"></a>애플리케이션의 URL 활성화를 사용하지 않도록 설정하려면

1. **솔루션 탐색기**에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 클릭 합니다.

2. **속성** 페이지에서 **게시** 탭을 클릭 합니다.

3. **옵션**을 클릭합니다.

4. **매니페스트**를 클릭 합니다.

5. **URL을 통해 응용 프로그램을 활성화 하지 않도록 차단**확인란을 선택 합니다.

6. 애플리케이션을 배포합니다.

## <a name="see-also"></a>참조
- [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)
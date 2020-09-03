---
title: '오류: IIS에서 웹 사이트 작업자 프로세스를 종료함 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 787785909cd980176fd9220f58198ae6cc272ea8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185472"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>오류: IIS에서 웹 사이트 작업자 프로세스를 종료했습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

디버거가 웹 사이트에서 코드 실행을 중지했습니다. 이로 인해 IIS(인터넷 정보 서비스)에서는 작업자 프로세스가 응답을 중지한 것으로 가정하여 작업자 프로세스를 종료했습니다.  
  
 디버깅을 계속하려면 작업자 프로세스를 계속하도록 IIS를 구성해야 합니다. 이 오류 메시지는 IIS 7 이전 버전의 IIS에서는 표시되지 않습니다.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>작업자 프로세스를 계속하도록 IIS 7을 구성하려면  
  
1. **관리 도구** 창을 엽니다.  
  
   1. **시작**을 클릭한 다음, **제어판**을 선택합니다.  
  
   2. **제어판**에서 필요한 경우 **클래식 보기로 전환**을 선택한 다음, **관리 도구**를 두 번 클릭합니다.  
  
2. **관리 도구** 창에서 **IIS(인터넷 정보 서비스) 관리자**를 두 번 클릭합니다.  
  
    IIS 관리자가 열립니다.  
  
3. 필요한 경우 **연결** 창에서 \<computer name> 노드를 확장합니다.  
  
4. \<computer name> 노드 아래에서 **애플리케이션 풀**을 클릭합니다.  
  
5. **애플리케이션 풀** 목록에서 애플리케이션을 실행하는 풀의 이름을 마우스 오른쪽 단추로 클릭하고 **고급 설정**을 클릭합니다.  
  
6. **고급 설정** 대화 상자에서 **프로세스 모델** 섹션을 찾아 다음 작업 중 하나를 수행합니다.  
  
   - **Ping 사용**을 **False**로 설정합니다.  
  
   - **Ping 최대 응답 시간**을 90초보다 큰 값으로 설정합니다.  
  
     **Ping 사용**을 **False**로 설정하면 IIS는 작업자 프로세스가 계속 실행되고 있는지 여부를 확인하지 않으며, 사용자가 디버깅된 프로세스를 중지할 때까지 작업자 프로세스가 활성 상태로 유지됩니다. **Ping 최대 응답 시간**을 큰 값으로 설정하면 IIS가 작업자 프로세스를 계속 모니터링할 수 있습니다.  
  
7. **확인**을 클릭하여 **고급 설정** 대화 상자를 닫습니다.  
  
8. IIS 관리자 및 **관리 도구** 창을 닫습니다.  
  
## <a name="see-also"></a>관련 항목  
 [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)

---
title: '오류: 대상 컴퓨터의 Visual Studio 원격 디버거 서비스가이 컴퓨터에 다시 연결할 수 없습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 80a7de83f118b38d9a3c71f1c7e7febf48e0f5bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520512"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>오류: 대상 컴퓨터의 Visual Studio 원격 디버거 서비스가 이 컴퓨터에 다시 연결할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 오류는 디버깅에 사용하려는 컴퓨터에 연결할 때 인증되지 않는 사용자 계정으로 Visual Studio 원격 디버거 서비스가 실행되고 있음을 의미합니다.  
  
 다음 표에는 컴퓨터에 액세스할 수 있는 계정이 나와 있습니다.  
  
|시나리오|LocalSystem 계정|도메인 계정|두 컴퓨터에서 사용자 이름과 암호가 동일한 로컬 계정|  
|-|-|-|-|-|  
|동일한 도메인의 두 컴퓨터|예|예|예|  
|도메인에서 양방향 트러스트가 있는 두 컴퓨터|아니요|아니요|예|  
|작업 그룹의 한 컴퓨터 또는 두 컴퓨터|아니요|아니요|예|  
|서로 다른 도메인의 컴퓨터|아니요|아니요|예|  
  
 이 밖에도 다음 지침을 따릅니다.  
  
- 모든 프로세스를 디버깅할 수 있으려면 Visual Studio 원격 디버거 서비스를 실행하는 데 사용되는 계정이 원격 컴퓨터의 관리자 계정이어야 합니다.  
  
- 또한 계정에는 **로컬 보안 정책** 관리 도구를 사용하는 원격 컴퓨터에 대한 `Log on as a service` 권한이 부여되어야 합니다.  
  
- 로컬 계정을 사용하여 컴퓨터에 액세스하는 경우 Visual Studio 원격 디버거 서비스를 로컬 계정으로 실행해야 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1. 원격 컴퓨터에서 Visual Studio 원격 디버거 서비스가 올바르게 설정되어 있는지 확인합니다. 자세한 내용은 [장치에서 원격 도구 설정](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)을 참조 하세요.  
  
2. 위 표에 나와 있듯이 디버거 호스트 컴퓨터에 액세스할 수 있는 계정으로 원격 디버거 서비스를 실행합니다.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>"서비스로 로그온" 권한을 추가하려면  
  
1. **시작** 메뉴에서 **제어판**을 선택합니다.  
  
2. 필요한 경우 제어판에서 **클래식 보기**를 선택합니다.  
  
3. **관리 도구**를 두 번 클릭합니다.  
  
4. 관리 도구 창에서 **로컬 보안 정책**을 두 번 클릭합니다.  
  
5. **로컬 보안 설정** 창에서 **로컬 정책** 폴더를 확장합니다.  
  
6. **사용자 권한 할당**을 클릭합니다.  
  
7. **P정책** 열에서 **서비스로 로그온**을 두 번 클릭하여 현재 로컬 그룹 정책 할당을 **서비스로 로그온** 대화 상자에 표시합니다.  
  
8. 새 사용자를 추가하려면 **사용자 또는 그룹 추가** 단추를 클릭합니다.  
  
9. 사용자 추가를 마쳤으면 **확인**을 클릭합니다.  
  
### <a name="to-work-around-this-error"></a>이 오류를 해결하려면  
  
- 원격 디버깅 모니터를 서비스가 아닌 애플리케이션으로 실행합니다.  
  
## <a name="see-also"></a>관련 항목  
 [원격 디버깅 오류 및 문제 해결](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)

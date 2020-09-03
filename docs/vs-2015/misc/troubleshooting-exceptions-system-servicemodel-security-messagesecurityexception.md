---
title: '예외 문제 해결: MessageSecurityException | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: troubleshooting
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b8ce3f16c1439d62cfa1e2cff344b70e6724c42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655358"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>예외 문제 해결: System.ServiceModel.Security.MessageSecurityException
에서 <xref:System.ServiceModel.Security.MessageSecurityException> [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 메시지의 보안이 올바르게 설정 되지 않았거나 변조 되었는지 확인 하는 경우 예외가 throw 됩니다. 이 오류는 다음 조건에 모두 해당될 때 가장 자주 발생합니다.

- 원격 데스크톱 연결 또는 터미널 서비스 등의 원격 연결을 통해 WCF 서비스 참조를 사용하여 웹 사이트 또는 웹 애플리케이션 프로젝트의 WCF 서비스(.svc)와 통신합니다.

- 원격 사이트에 대한 관리자 권한이 없습니다.

- 원격 사이트의 로컬 호스트에 대한 요청을 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server에서 처리합니다.

## <a name="associated-tips"></a>관련 팁
 **ASP.Net Development Server를 사용하는 경우 NTLM 인증 문제를 해결하십시오.**
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server에서는 대개 NTLM(Windows NT Challenge/Response) 보안을 사용하지 않으므로 익명 액세스가 허용됩니다. 하지만 터미널 서비스 세션을 실행하거나 원격 연결을 사용하는 경우에는 기본적으로 NTLM 보안이 사용됩니다. NTLM이 사용되면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server를 시작한 사용자 또는 프로세스의 자격 증명과 비교하여 모든 로컬 호스트 요청의 유효성이 검사됩니다. 이를 통해 보안 위협이 감소됩니다. 그러나 WCF에서도 자체 인증을 수행하며 관리자가 아닌 계정에서 WCF 서비스를 사용할 수 없도록 금지합니다.

 원격 사용자가 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server를 통해 웹 사이트를 실행하면서 웹 서비스 또는 WCF 서비스를 함께 사용하는 경우 사용자 지정 서비스 바인딩을 만들거나 NTLM 보안을 해제할 수 있습니다.

> [!IMPORTANT]
> 보안 위협이 발생할 수 있으므로 NTLM 보안을 해제하지 않는 것이 좋습니다.

 사용자 지정 서비스 바인딩을 만들면 NTLM 인증에 따라 계속 보호받을 수 있습니다.

 다음 단계에 따라 WCF 서비스에 대한 사용자 지정 서비스 바인딩을 만듭니다.

#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>ASP.NET Development Server 내에 호스팅된 WCF 서비스에 대한 사용자 지정 서비스 바인딩을 만들려면

1. 예외가 발생한 WCF 서비스에 대한 Web.config 파일을 엽니다.

2. Web.config 파일에 다음 정보를 입력합니다.

   ```
   <bindings>
     <customBinding>
       <binding name="Service1Binding">
         <transactionFlow />
         <textMessageEncoding />
         <httpTransport authenticationScheme="Ntlm" />
       </binding>
     </customBinding>
   </bindings>
   ```

3. Web.config 파일을 저장한 다음 닫습니다.

4. WCF 또는 웹 서비스에 대한 코드에서 엔드포인트 값을 다음과 같이 변경합니다.

   ```
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />
   ```

    이렇게 하면 서비스에 사용자 지정 바인딩이 사용됩니다.

5. 서비스에 액세스하는 웹 애플리케이션에 서비스에 대한 참조를 추가합니다. **서비스 참조 추가** 대화 상자에서 예외가 발생한 원래 서비스에 대해 수행한 것과 같은 방법으로 서비스에 대한 참조를 추가합니다.

   WCF 서비스 참조를 사용하는 경우 다음 단계에 따라 NTLM 보안을 해제할 수 있습니다.

> [!IMPORTANT]
> 보안 위협이 발생할 수 있으므로 NTLM 보안을 해제하지 않는 것이 좋습니다.

#### <a name="to-turn-off-ntlm-security"></a>NTLM 보안을 해제하려면

1. **솔루션 탐색기**에서 웹 사이트 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성 페이지**를 클릭합니다.

2. **시작 옵션**을 선택한 다음 **NTLM 인증** 확인란의 선택을 취소합니다.

3. **확인**을 클릭합니다.

## <a name="see-also"></a>참고 항목
 <xref:System.ServiceModel.Security.MessageSecurityException> [예외 도우미 사용](https://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)
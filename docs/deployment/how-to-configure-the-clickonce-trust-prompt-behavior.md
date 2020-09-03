---
title: 방법-ClickOnce 신뢰 프롬프트 동작 구성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7417f9cdce21dc09aeaf306b55834ad7d3a125a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382551"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>방법: ClickOnce 신뢰 프롬프트 동작 구성
Clickonce 신뢰 프롬프트를 구성 하 여 최종 사용자에 게 Windows Forms 응용 프로그램, Windows Presentation Foundation 응용 프로그램, 콘솔 응용 프로그램, WPF 브라우저 응용 프로그램, Office 솔루션 등의 ClickOnce 응용 프로그램 설치 옵션을 제공할지 여부를 제어할 수 있습니다. 각 최종 사용자의 컴퓨터에서 레지스트리 키를 설정 하 여 신뢰 프롬프트를 구성 합니다.

 다음 표에서는 각각의 5 개 영역 (Internet, UnMyComputer Sites,, LocalIntranet 및 사이트)에 적용할 수 있는 구성 옵션을 보여 줍니다.

|옵션|레지스트리 설정 값|설명|
|------------|----------------------------|-----------------|
|신뢰 프롬프트를 사용 하도록 설정 합니다.|`Enabled`|최종 사용자가 ClickOnce 응용 프로그램에 신뢰를 부여할 수 있도록 ClickOnce 신뢰 프롬프트가 표시 됩니다.|
|신뢰 프롬프트를 제한 합니다.|`AuthenticodeRequired`|Clickonce 신뢰 프롬프트는 ClickOnce 응용 프로그램이 게시자를 식별 하는 인증서로 서명 된 경우에만 표시 됩니다.|
|신뢰 프롬프트를 사용 하지 않도록 설정 합니다.|`Disabled`|명시적으로 신뢰할 수 있는 인증서로 서명 되지 않은 ClickOnce 응용 프로그램에 대해서는 ClickOnce 신뢰 프롬프트가 표시 되지 않습니다.|

 다음 표에서는 각 영역에 대 한 기본 동작을 보여 줍니다. 응용 프로그램 열은 Windows Forms 응용 프로그램, Windows Presentation Foundation 응용 프로그램, WPF 브라우저 응용 프로그램 및 콘솔 응용 프로그램을 나타냅니다.

|영역|애플리케이션|Office 솔루션|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 ClickOnce 신뢰 프롬프트를 사용, 제한 또는 사용 하지 않도록 설정 하 여 이러한 설정을 재정의할 수 있습니다.

## <a name="enable-the-clickonce-trust-prompt"></a>ClickOnce 신뢰 프롬프트 사용
 최종 사용자에 게 해당 영역에서 제공 하는 ClickOnce 응용 프로그램을 설치 하 고 실행할 수 있는 옵션을 제공 하려는 경우 영역에 대 한 신뢰 프롬프트를 사용 하도록 설정 합니다.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>레지스트리 편집기를 사용 하 여 ClickOnce 신뢰 프롬프트를 사용 하도록 설정 하려면

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. **열기** 상자에를 입력 한 `regedit` 다음 **확인**을 클릭 합니다.

2. 다음 레지스트리 키를 찾습니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     키가 없으면 새로 만듭니다.

3. 다음 하위 키가 아직 없는 경우 다음 표에 나와 있는 연결 된 값을 사용 하 여 **문자열 값**으로 추가 합니다.

    |문자열 값 하위 키|값|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Office 솔루션의 경우의 `Internet` 기본값은이 `AuthenticodeRequired` 고 `UntrustedSites` 값은 `Disabled` 입니다. 다른 모든 경우에는 `Internet` 기본값을 갖습니다 `Enabled` .

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>ClickOnce 신뢰 프롬프트를 프로그래밍 방식으로 사용 하도록 설정 하려면

1. Visual Studio에서 Visual Basic 또는 Visual c # 콘솔 응용 프로그램을 만듭니다.

2. 편집할 *프로그램 .vb* 또는 *Program.cs* 파일을 열고 다음 코드를 추가 합니다.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "Enabled")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. 애플리케이션을 빌드 및 실행합니다.

## <a name="restrict-the-clickonce-trust-prompt"></a>ClickOnce 신뢰 프롬프트 제한
 신뢰 확인을 요청 하는 메시지가 사용자에 게 표시 되기 전에 알려진 id를 가진 Authenticode 인증서로 솔루션을 서명 해야 하도록 신뢰 프롬프트를 제한 합니다.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>레지스트리 편집기를 사용 하 여 ClickOnce 신뢰 프롬프트를 제한 하려면

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. **열기** 상자에를 입력 한 `regedit` 다음 **확인**을 클릭 합니다.

2. 다음 레지스트리 키를 찾습니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     키가 없으면 새로 만듭니다.

3. 다음 하위 키가 아직 없는 경우 다음 표에 나와 있는 연결 된 값을 사용 하 여 **문자열 값**으로 추가 합니다.

    |문자열 값 하위 키|값|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>ClickOnce 신뢰 프롬프트를 프로그래밍 방식으로 제한 하려면

1. Visual Studio에서 Visual Basic 또는 Visual c # 콘솔 응용 프로그램을 만듭니다.

2. 편집할 *프로그램 .vb* 또는 *Program.cs* 파일을 열고 다음 코드를 추가 합니다.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. 애플리케이션을 빌드 및 실행합니다.

## <a name="disable-the-clickonce-trust-prompt"></a>ClickOnce 신뢰 프롬프트 사용 안 함
 최종 사용자에 게 보안 정책에서 아직 신뢰 되지 않은 솔루션을 설치 하는 옵션이 제공 되지 않도록 신뢰 프롬프트를 사용 하지 않도록 설정할 수 있습니다.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>레지스트리 편집기를 사용 하 여 ClickOnce 신뢰 프롬프트를 사용 하지 않도록 설정 하려면

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. **열기** 상자에를 입력 한 `regedit` 다음 **확인**을 클릭 합니다.

2. 다음 레지스트리 키를 찾습니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     키가 없으면 새로 만듭니다.

3. 다음 하위 키가 아직 없는 경우 다음 표에 나와 있는 연결 된 값을 사용 하 여 **문자열 값**으로 추가 합니다.

    |문자열 값 하위 키|값|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>ClickOnce 신뢰 프롬프트를 프로그래밍 방식으로 사용 하지 않도록 설정 하려면

1. Visual Studio에서 Visual Basic 또는 Visual c # 콘솔 응용 프로그램을 만듭니다.

2. 편집할 *프로그램 .vb* 또는 *Program.cs* 파일을 열고 다음 코드를 추가 합니다.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. 애플리케이션을 빌드 및 실행합니다.

## <a name="see-also"></a>추가 정보
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)
- [신뢰할 수 있는 애플리케이션 배포 개요](../deployment/trusted-application-deployment-overview.md)
- [방법: ClickOnce 보안 설정 사용](../deployment/how-to-enable-clickonce-security-settings.md)
- [방법: ClickOnce 응용 프로그램의 보안 영역 설정](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [방법: ClickOnce 응용 프로그램에 대 한 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [방법: 제한된 권한으로 ClickOnce 애플리케이션 디버그](securing-clickonce-applications.md)
- [방법: ClickOnce 애플리케이션의 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [방법: 애플리케이션 및 배포 매니페스트에 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)

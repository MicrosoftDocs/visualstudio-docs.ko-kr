---
title: '방법: 포함 목록 보안 구성'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 459cf3f33197939a916a5f11a94bbaf09e8142e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541637"
---
# <a name="how-to-configure-inclusion-list-security"></a>방법: 포함 목록 보안 구성
  관리자 권한이 있는 경우 신뢰 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 확인을 포함 목록에 저장 하 여 최종 사용자에 게 Office 솔루션을 설치 하는 옵션이 제공 되는지 여부를 제어 하도록 신뢰 프롬프트를 구성할 수 있습니다. 포함 목록에 대 한 자세한 내용은 [포함 목록을 사용 하 여 Office 솔루션 신뢰](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)를 참조 하세요.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 5 개 영역에 있는 솔루션의 경우 다음 옵션을 설정할 수 있습니다.

- [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]신뢰 프롬프트 키와 포함 목록을 사용 하도록 설정 합니다. 최종 사용자가 인증서로 서명 된 Office 솔루션에 신뢰를 부여할 수 있도록 허용할 수 있습니다.

- [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]신뢰 프롬프트 키와 포함 목록을 제한 합니다. 최종 사용자가 게시자를 식별 하는 인증서로 서명 되었지만 아직 신뢰 되지 않은 Office 솔루션을 설치 하도록 허용할 수 있습니다.

- [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]신뢰 프롬프트 키와 포함 목록을 사용 하지 않도록 설정 합니다. 최종 사용자가 명시적으로 신뢰할 수 있는 인증서로 서명 되지 않은 Office 솔루션을 설치 하지 못하게 할 수 있습니다.

## <a name="enable-the-inclusion-list"></a>포함 목록 사용
 최종 사용자에 게 해당 영역에서 제공 하는 Office 솔루션을 설치 하 고 실행할 수 있는 옵션을 제공 하려는 경우 영역에 대 한 포함 목록을 사용 하도록 설정 합니다.

### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>레지스트리 편집기를 사용 하 여 포함 목록을 사용 하도록 설정 하려면

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. **열기** 상자에 **regedt32.exe**를 입력 한 다음 **확인**을 클릭 합니다.

2. 다음 레지스트리 키를 찾습니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     키가 없으면 새로 만듭니다.

3. 다음 하위 키가 아직 없는 경우 **문자열 값**으로 추가 하 고 연결 된 값을 사용 합니다.

    |문자열 값 하위 키|값|
    |-------------------------|-----------|
    |**인터넷**|**AuthenticodeRequired**|
    |**없는 사이트**|**사용 안 함**|
    |**MyComputer**|**사용**|
    |**LocalIntranet**|**사용**|
    |**사이트**|**사용**|

     기본적으로 **인터넷** 에는 AuthenticodeRequired 및 **un** **사이트** 의 값이 **사용 안 함으로 설정**되어 있습니다.

### <a name="to-enable-the-inclusion-list-programmatically"></a>프로그래밍 방식으로 포함 목록을 사용 하도록 설정 하려면

1. Visual Basic 또는 Visual c # 콘솔 응용 프로그램을 만듭니다.

2. 편집할 *프로그램 .vb* 또는 *Program.cs* 파일을 열고 다음 코드를 추가 합니다.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "AuthenticodeRequired")
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

## <a name="restrict-the-inclusion-list"></a>포함 목록 제한
 신뢰 결정을 요구 하는 메시지가 사용자에 게 표시 되기 전에 알려진 id를 가진 Authenticode 인증서로 솔루션에 서명 해야 하는 포함 목록을 제한 합니다.

### <a name="to-restrict-the-inclusion-list"></a>포함 목록을 제한 하려면

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. **열기** 상자에 **regedt32.exe**를 입력 한 다음 **확인**을 클릭 합니다.

2. 다음 레지스트리 키를 찾습니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     키가 없으면 새로 만듭니다.

3. 다음 하위 키가 아직 없는 경우 **문자열 값**으로 추가 하 고 연결 된 값을 사용 합니다.

    |문자열 값 하위 키|값|
    |-------------------------|-----------|
    |**없는 사이트**|**사용 안 함**|
    |**인터넷**|**AuthenticodeRequired**|
    |**MyComputer**|**AuthenticodeRequired**|
    |**LocalIntranet**|**AuthenticodeRequired**|
    |**사이트**|**AuthenticodeRequired**|

     기본적으로 **인터넷** 에는 AuthenticodeRequired 및 **un** **사이트** 의 값이 **사용 안 함으로 설정**되어 있습니다.

### <a name="to-restrict-the-inclusion-list-programmatically"></a>프로그래밍 방식으로 포함 목록을 제한 하려면

1. Visual Basic 또는 Visual c # 콘솔 응용 프로그램을 만듭니다.

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

## <a name="disable-the-inclusion-list"></a>포함 목록 사용 안 함
 최종 사용자가 신뢰할 수 있고 알려진 인증서로 서명 된 솔루션만 설치할 수 있도록 포함 목록을 사용 하지 않도록 설정할 수 있습니다.

### <a name="to-disable-the-inclusion-list"></a>포함 목록을 사용 하지 않도록 설정 하려면

1. 레지스트리 편집기를 엽니다.

    1. **시작**을 클릭한 다음 **실행**을 클릭합니다.

    2. **열기** 상자에 **regedt32.exe**를 입력 한 다음 **확인**을 클릭 합니다.

2. 아직 존재 하지 않는 경우 다음 레지스트리 키를 만듭니다.

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

3. 다음 하위 키가 아직 없는 경우 **문자열 값**으로 추가 하 고 연결 된 값을 사용 합니다.

    |문자열 값 하위 키|값|
    |-------------------------|-----------|
    |**없는 사이트**|**사용 안 함**|
    |**인터넷**|**사용 안 함**|
    |**MyComputer**|**사용 안 함**|
    |**LocalIntranet**|**사용 안 함**|
    |**사이트**|**사용 안 함**|

### <a name="to-disable-the-inclusion-list-programmatically"></a>프로그래밍 방식으로 포함 목록을 사용 하지 않도록 설정 하려면

1. Visual Basic 또는 Visual c # 콘솔 응용 프로그램을 만듭니다.

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
- [포함 목록을 사용 하 여 Office 솔루션 신뢰](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)

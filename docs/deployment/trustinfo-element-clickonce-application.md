---
title: '&lt;trustInfo &gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5873eb18b2f803acfd5aba9444657884b1a24581
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184434"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo&gt; 요소(ClickOnce 애플리케이션)
애플리케이션을 클라이언트 컴퓨터에서 실행하는 데 필요한 최소 보안 권한을 설명합니다.

## <a name="syntax"></a>Syntax

```xml

      <trustInfo>
   <security>
      <applicationRequestMinimum>
         <PermissionSet
            ID
            Unrestricted>
            <IPermission
               class
               version
               Unrestricted
            />
         </PermissionSet>
         <defaultAssemblyRequest
            permissionSetReference
         />
         <assemblyRequest
            name
            permissionSetReference
         />
      </applicationRequestMinimum>
      <requestedPrivileges>
         <requestedExecutionLevel
            level
            uiAccess
         />
      </requestedPrivileges>
   </security>
</trustInfo>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `trustInfo` 요소는 필수이며 `asm.v2` 네임스페이스에 있습니다. 특성이 없으며 다음 요소를 포함합니다.

## <a name="security"></a>security
 필수 요소. 이 요소는 `trustInfo` 요소의 자식입니다. `applicationRequestMinimum` 요소를 포함하며 특성이 없습니다.

## <a name="applicationrequestminimum"></a>applicationRequestMinimum
 필수 요소. 이 요소는 `security` 요소의 자식이며 `PermissionSet`, `assemblyRequest`및 `defaultAssemblyRequest`요소를 포함합니다. 이 요소에는 특성이 없습니다.

## <a name="permissionset"></a>PermissionSet
 필수 요소. 이 요소는 `applicationRequestMinimum` 요소의 자식이며 `IPermission` 요소를 포함합니다. 이 요소에는 다음 특성이 있습니다.

- `ID`

     필수 요소. 권한 집합을 알려 줍니다. 이 특성은 아무 값이나 될 수 있습니다. ID는 `defaultAssemblyRequest` 및 `assemblyRequest` 특성에서 참조됩니다.

- `version`

     필수 요소. 권한의 버전을 알려 줍니다. 일반적으로 이 값은 `1`입니다.

## <a name="ipermission"></a>IPermission
 선택 사항입니다. 이 요소는 `PermissionSet` 요소의 자식입니다. `IPermission`요소는 .NET Framework의 권한 클래스를 완전히 식별 합니다. `IPermission` 요소에는 다음 특성이 있지만 권한 클래스의 속성에 해당하는 추가 특성이 있을 수 있습니다. 특정 권한에 대한 구문을 확인하려면 Security.config 파일에 나열된 예제를 참조하세요.

- `class`

     필수 요소. 강력한 이름으로 권한 클래스를 식별합니다. 예를 들어 다음 코드는 `FileDialogPermission` 유형을 알려 줍니다.

     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

- `version`

     필수 요소. 권한의 버전을 알려 줍니다. 일반적으로 이 값은 `1`입니다.

- `Unrestricted`

     필수 요소. 애플리케이션에 이 권한을 무제한으로 부여할 필요가 있는지 식별합니다. `true`인 경우 권한 부여에 조건이 없습니다. `false`또는 이 특성이 정의되지 않은 경우에는 `IPermission` 태그에 정의된 권한별 특성에 따라 제한됩니다. 다음 권한을 사용합니다.

    ```xml
    <IPermission
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Read="USERNAME" />
    <IPermission
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Unrestricted="true" />
    ```

     이 예제에서 <xref:System.Security.Permissions.EnvironmentPermission> 에 대한 선언은 애플리케이션이 환경 변수 USERNAME만 읽도록 제한하는 반면에 <xref:System.Security.Permissions.FileDialogPermission> 에 대한 선언은 애플리케이션이 모든 <xref:System.Windows.Forms.FileDialog> 클래스를 무제한으로 사용할 수 있도록 합니다.

## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest
 선택 사항입니다. 모든 어셈블리에 부여된 권한 집합을 알려 줍니다. 이 요소는 `applicationRequestMinimum` 요소의 자식이며 다음과 같은 특성이 있습니다.

- `permissionSetReference`

     필수 요소. 기본 권한인 권한 집합의 ID를 알려 줍니다. 권한 집합은 `PermissionSet` 요소에서 선언됩니다.

## <a name="assemblyrequest"></a>assemblyRequest
 선택 사항입니다. 특정 어셈블리에 대한 권한을 알려 줍니다. 이 요소는 `applicationRequestMinimum` 요소의 자식이며 다음과 같은 특성이 있습니다.

- `Name`

     필수 요소. 어셈블리 이름을 알려 줍니다.

- `permissionSetReference`

     필수 요소. 이 어셈블리에서 필요로 하는 권한 집합의 ID를 식별합니다. 권한 집합은 `PermissionSet` 요소에서 선언됩니다.

## <a name="requestedprivileges"></a>requestedPrivileges
 선택 사항입니다. 이 요소는 `security` 요소의 자식이며 `requestedExecutionLevel` 요소를 포함합니다. 이 요소에는 특성이 없습니다.

## <a name="requestedexecutionlevel"></a>requestedExecutionLevel
 선택 사항입니다. 애플리케이션 요청이 실행되는 보안 수준을 알려 줍니다. 이 요소에는 자식이 없으며 다음과 같은 특성이 있습니다.

- `Level`

   필수 요소. 애플리케이션이 요청하는 보안 수준을 나타냅니다. 가능한 값은 다음과 같습니다.

   `asInvoker`, 추가 권한을 요청하지 않습니다. 이 수준에서는 추가 신뢰 프롬프트를 요구하지 않습니다.

   `highestAvailable`, 부모 프로세스에 사용할 수 있는 가장 높은 권한을 요청합니다.

   `requireAdministrator`, 전체 관리자 권한을 요청합니다.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션은 `asInvoker`의 값으로만 설치됩니다. 다른 모든 값을 사용하는 설치는 실패합니다.

- `uiAccess`

   선택 사항입니다. 애플리케이션에서 보호된 사용자 인터페이스 요소에 대한 액세스를 필요로 하는지 여부를 나타냅니다. 값은 `true` 또는 `false`이며, 기본값은 false입니다. 서명된 애플리케이션만 true 값을 가집니다.

## <a name="remarks"></a>설명
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션에서 클라이언트 컴퓨터에서 기본적으로 부여하는 권한보다 많은 권한을 요청하는 경우, 공용 언어 런타임의 트러스트 관리자는 애플리케이션에 이 관리자 권한 수준의 트러스트를 부여할지를 사용자에게 묻습니다. 관리자 권한 수준의 트러스트를 부여하지 않는 경우 애플리케이션은 실행되지 않으며, 부여하는 경우 요청된 권한으로 실행됩니다.

 `defaultAssemblyRequest` 및 `assemblyRequest` 을(를) 사용하여 요청된 모든 권한은 배포 매니페스트에 유효한 트러스트 라이선스가 있는 경우 사용자 프롬프트 없이 부여됩니다.

 권한 상승에 대 한 자세한 내용은 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)을 참조 하세요. 정책 배포에 대한 자세한 내용은 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)의 내용을 를 참조하세요.

## <a name="examples"></a>예제
 다음 세 가지 코드 예제는 `trustInfo` 배포의 애플리케이션 매니페스트에서 사용할 수 있는 기본 명명된 보안 영역(Internet, LocalIntranet, FullTrust)에 대한 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 요소를 설명합니다.

 첫 번째 예제는 Internet 보안 영역에서 사용할 수 있는 기본 권한에 대한 `trustInfo` 요소를 설명합니다.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="Internet">
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Access="Open" />
          <IPermission
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="DomainIsolationByUser"
            UserQuota="10240" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Window="SafeTopLevelWindows"
            Clipboard="OwnClipboard" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="SafePrinting" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="Internet" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
```

 두 번째 예제는 LocalIntranet 보안 영역에서 사용할 수 있는 기본 권한에 대한 `trustInfo` 요소를 설명합니다.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="LocalIntranet">
          <IPermission
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Read="USERNAME" />
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="AssemblyIsolationByUser"
            UserQuota="9223372036854775807"
            Expiry="9223372036854775807"
            Permanent="True" />
          <IPermission
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="ReflectionEmit" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Assertion, Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="DefaultPrinting" />
          <IPermission
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />
      </applicationRequestMinimum>
    </security>
</trustInfo>
```

 세 번째 예제는 FullTrust 보안 영역에서 사용할 수 있는 기본 권한에 대한 `trustInfo` 요소를 설명합니다.

```xml
<trustInfo>
  <security>
    <applicationRequestMinimum>
      <PermissionSet ID="FullTrust" Unrestricted="true" />
      <defaultAssemblyRequest permissionSetReference="FullTrust" />
    </applicationRequestMinimum>
  </security>
</trustInfo>
```

## <a name="see-also"></a>추가 정보
- [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
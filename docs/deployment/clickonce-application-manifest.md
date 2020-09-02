---
title: ClickOnce 응용 프로그램 매니페스트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be9bfe19b92740d6be6c91802d193bf2fc401847
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928970"
---
# <a name="clickonce-application-manifest"></a>ClickOnce 애플리케이션 매니페스트
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]응용 프로그램 매니페스트는를 사용 하 여 배포 되는 응용 프로그램을 설명 하는 XML 파일입니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트에는 다음과 같은 요소와 특성이 있습니다.

| 요소 | 설명 | 특성 |
| - | - | - |
| [\<assembly> 요소](../deployment/assembly-element-clickonce-application.md) | 필수 요소. 최상위 요소입니다. | `manifestVersion` |
| [\<assemblyIdentity> 요소](../deployment/assemblyidentity-element-clickonce-application.md) | 필수 요소. 응용 프로그램의 주 어셈블리를 식별 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo> 요소](../deployment/trustinfo-element-clickonce-application.md) | 애플리케이션 보안 요구 사항을 식별합니다. | 없음 |
| [\<entryPoint> 요소](../deployment/entrypoint-element-clickonce-application.md) | 필수 요소. 응용 프로그램 코드 진입점을 식별 합니다. | `name` |
| [\<dependency> 요소](../deployment/dependency-element-clickonce-application.md) | 필수 요소. 애플리케이션을 실행하는 데 필요한 각 종속성을 식별합니다. 필요에 따라 사전 설치해야 하는 어셈블리를 식별합니다. | 없음 |
| [\<file> 요소](../deployment/file-element-clickonce-application.md) | 선택 사항입니다. 응용 프로그램에서 사용 하는 각 nonassembly 파일을 식별 합니다. 파일에 연결된 COM(구성 요소 개체 모델) 격리 데이터를 포함할 수 있습니다. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation> 요소](../deployment/fileassociation-element-clickonce-application.md) | 선택 사항입니다. 응용 프로그램과 연결할 파일 확장명을 식별 합니다. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>설명
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]응용 프로그램 매니페스트 파일은를 사용 하 여 배포 된 응용 프로그램을 식별 합니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]에 대한 자세한 내용은 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)를 참조하세요.

## <a name="file-location"></a>파일 위치
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]응용 프로그램 매니페스트는 단일 배포 버전에만 적용 됩니다. 이러한 이유로 배포 매니페스트와 별도로 저장 해야 합니다. 일반적인 규칙은 연결 된 버전에 따라 이름이 지정 된 하위 디렉터리에 저장 하는 것입니다.

 응용 프로그램 매니페스트는 항상 배포 전에 서명 해야 합니다. 응용 프로그램 매니페스트를 수동으로 변경 하는 경우 *mage.exe* 를 사용 하 여 응용 프로그램 매니페스트를 다시 서명 하 고, 배포 매니페스트를 업데이트 한 후 배포 매니페스트에 다시 서명 해야 합니다. 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)를 참조 하세요.

## <a name="file-name-syntax"></a>파일 이름 구문
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션 매니페스트 파일의 이름은 `assemblyIdentity` 요소에서 식별한 대로 애플리케이션의 전체 이름 및 *.manifest* 확장명이어야 합니다. 예를 들어 *Example.exe* 응용 프로그램을 참조 하는 응용 프로그램 매니페스트는 다음 파일 이름 구문을 사용 합니다.

 `example.exe.manifest`

## <a name="example"></a>예
 다음 코드 예제에서는 응용 프로그램에 대 한 응용 프로그램 매니페스트를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />
  <application />
  <entryPoint>
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
  <trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />
        <defaultAssemblyRequest permissionSetReference="Custom" />
      </applicationRequestMinimum>
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">
        <!--
          UAC Manifest Options
          If you want to change the Windows User Account Control level replace the
          requestedExecutionLevel node with one of the following.

        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />

         If you want to utilize File and Registry Virtualization for backward
         compatibility then delete the requestedExecutionLevel node.
    -->
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />
      </requestedPrivileges>
    </security>
  </trustInfo>
  <dependency>
    <dependentOS>
      <osVersionInfo>
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
      </osVersionInfo>
    </dependentOS>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />
    </dependentAssembly>
  </dependency>
  <dependency>
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />
      <hash>
        <dsig:Transforms>
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
        </dsig:Transforms>
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
      </hash>
    </dependentAssembly>
  </dependency>
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">
...
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
---
title: '&lt;compatibleFrameworks &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99db3d51414197df469aaa2eabe97e0967c31b05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66746035"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks &gt; 요소 (ClickOnce 배포)
이 애플리케이션이 설치 및 실행할 수 있는 .NET Framework의 버전을 식별합니다.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) `compatibleFrameworks` [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)를 사용 하는 인증서로 이미 서명 된 응용 프로그램 매니페스트를 저장 하는 경우MageUI.exe는 요소를 지원 하지 않습니다. 대신 [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)를 사용 해야 합니다.

## <a name="syntax"></a>Syntax

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `compatibleFrameworks`요소는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET Framework 4 이상에서 제공 하는 런타임을 대상으로 하는 배포 매니페스트에 필요 합니다. 요소에는 `compatibleFrameworks` `framework` 이 응용 프로그램을 실행할 수 있는 .NET Framework 버전을 지정 하는 요소가 하나 이상 포함 되어 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]런타임은이 목록에서 사용할 수 있는 첫 번째 응용 프로그램에서 응용 프로그램을 실행 합니다 `framework` .

 다음 표에서는 요소가 지 원하는 특성을 보여 줍니다 `compatibleFrameworks` .

|특성|설명|
|---------------|-----------------|
|`S` `upportUrl`|선택 사항입니다. 기본 호환 .NET Framework 버전을 다운로드할 수 있는 URL을 지정 합니다.|

## <a name="framework"></a>프레임워크
 필수 요소. 다음 표에서는 요소가 지 원하는 특성을 보여 줍니다 `framework` .

|특성|설명|
|---------------|-----------------|
|`targetVersion`|필수 요소. 대상 .NET Framework의 버전 번호를 지정 합니다.|
|`profile`|필수 요소. 대상 .NET Framework의 프로필을 지정 합니다.|
|`supportedRuntime`|필수 요소. 대상 .NET Framework와 연결 된 런타임의 버전 번호를 지정 합니다.|

## <a name="remarks"></a>설명

## <a name="example"></a>예
 다음 코드 예제에서는 `compatibleFrameworks` 배포 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이 배포는에서 실행할 수 있습니다 [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . .NET Framework 4는의 상위 집합 이므로 실행할 수도 있습니다 [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
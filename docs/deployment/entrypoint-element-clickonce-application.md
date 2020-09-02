---
title: '&lt;entryPoint &gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 615a606dc4d04682a9d5a1a69c91b4d2cd67de15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928619"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint &gt; 요소 (ClickOnce 응용 프로그램)
이 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램이 클라이언트 컴퓨터에서 실행 될 때 실행 되어야 하는 어셈블리를 식별 합니다.

## <a name="syntax"></a>Syntax

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `entryPoint` 요소는 필수이며 `urn:schemas-microsoft-com:asm.v2` 네임스페이스에 있습니다. `entryPoint`응용 프로그램 매니페스트에서는 하나의 요소만 정의할 수 있습니다.

 `entryPoint` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`name`|선택 사항입니다. 이 값은 .NET Framework에서 사용 되지 않습니다.|

 `entryPoint` 에는 다음 요소가 있습니다.

## <a name="assemblyidentity"></a>assemblyIdentity
 필수 요소. `assemblyIdentity`및 해당 특성의 역할은 [ \<assemblyIdentity> 요소](../deployment/assemblyidentity-element-clickonce-application.md)에 정의 되어 있습니다.

 `processorArchitecture`이 요소의 특성과 `processorArchitecture` `assemblyIdentity` 응용 프로그램 매니페스트의 다른 위치에 정의 된 특성이 일치 해야 합니다.

## <a name="commandline"></a>commandLine
 필수 요소. 는 요소의 자식 이어야 합니다 `entryPoint` . 자식 요소가 없으며 다음과 같은 특성이 있습니다.

| 특성 | 설명 |
|--------------| - |
| `file` | 필수 요소. 응용 프로그램의 시작 어셈블리에 대 한 로컬 참조 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 입니다. 이 값에는 슬래시 (/) 또는 백슬래시 ( \\ ) 경로 구분 기호를 사용할 수 없습니다. |
| `parameters` | 필수 요소. 진입점을 사용 하 여 수행할 작업을 설명 합니다. 유일 하 게 유효한 값은입니다 `run` . 빈 문자열을 제공 하면 `run` 가 가정 됩니다. |

## <a name="customhostrequired"></a>customHostRequired
 선택 사항입니다. 포함 하는 경우,이 배포에 사용자 지정 호스트 내에 배포 되는 구성 요소가 포함 되어 있고 독립 실행형 응용 프로그램이 아닌 경우에 지정 합니다.

 이 요소가 있으면 및 요소도 없어야 합니다 `assemblyIdentity` `commandLine` . 인 경우에는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 설치 중에 유효성 검사 오류가 발생 합니다.

 이 요소에는 특성이 없고 자식이 없습니다.

## <a name="customux"></a>customUX
 선택 사항입니다. 사용자 지정 설치 관리자가 응용 프로그램을 설치 및 유지 관리 하 고 시작 메뉴 항목, 바로 가기 또는 프로그램 추가/제거 항목을 만들지 않도록 지정 합니다.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 CustomUX 요소를 포함 하는 응용 프로그램은 클래스를 사용 하 여 설치 작업을 수행 하는 사용자 지정 설치 관리자를 제공 해야 합니다 <xref:System.Deployment.Application.InPlaceHostingManager> . 매니페스트 또는 setup.exe 필수 구성 요소 부트스트래퍼를 두 번 클릭 하 여이 요소를 포함 하는 응용 프로그램을 설치할 수 없습니다. 사용자 지정 설치 관리자는 시작 메뉴 항목, 바로 가기 및 프로그램 추가/제거 항목을 만들 수 있습니다. 사용자 지정 설치 관리자가 프로그램 추가/제거 항목을 만들지 않는 경우 속성에서 제공 하는 구독 식별자를 저장 하 <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> 고 사용자가 나중에 메서드를 호출 하 여 응용 프로그램을 제거할 수 있도록 해야 합니다 <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> . 자세한 내용은 [연습: ClickOnce 응용 프로그램에 대 한 사용자 지정 설치 관리자 만들기](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)를 참조 하세요.

## <a name="remarks"></a>설명
 이 요소는 응용 프로그램의 어셈블리 및 진입점을 식별 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다.

 `commandLine`런타임에 응용 프로그램에 매개 변수를 전달 하는 데를 사용할 수 없습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]응용 프로그램의에서 배포에 대 한 쿼리 문자열 매개 변수에 액세스할 수 있습니다 <xref:System.AppDomain> . 자세한 내용은 [방법: 온라인 ClickOnce 응용 프로그램에서 쿼리 문자열 정보 검색](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)을 참조 하세요.

## <a name="example"></a>예
 다음 코드 예제에서는 응용 프로그램 `entryPoint` 에 대 한 응용 프로그램 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이 코드 예제는 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md) 항목에 대해 제공 되는 더 큰 예제의 일부입니다.

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)

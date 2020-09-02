---
title: '&lt;dependency &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84e26a2d7dae70e0029817d4e6bb6e70dd53bce4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62928948"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;dependency &gt; 요소 (ClickOnce 배포)
설치할 응용 프로그램의 버전과 응용 프로그램 매니페스트의 위치를 식별 합니다.

## <a name="syntax"></a>Syntax

```xml

      <dependency>
   <dependentAssembly
      preRequisite
      visible
      dependencyType
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         publicKeyToken
         processorArchitecture
         language
         type
      />
      <hash>
         <dsig:Transforms>
            <dsig:Transform
                Algorithm
            />
         </dsig:Transforms>
         <dsig:DigestMethod />
         <dsig:DigestValue>
         </dsig:DigestValue>
      </hash>

   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `dependency`요소가 필요 합니다. 특성이 없습니다. 배포 매니페스트에는 여러 요소가 있을 수 있습니다 `dependency` .

 `dependency`요소는 일반적으로 응용 프로그램에 포함 된 어셈블리의 주 응용 프로그램에 대 한 종속성을 나타냅니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Main.exe 응용 프로그램에서 DotNetAssembly.dll 라는 어셈블리를 사용 하는 경우 해당 어셈블리는 종속성 섹션에 나열 되어야 합니다. 그러나 종속성은 특정 버전의 공용 언어 런타임, GAC (전역 어셈블리 캐시)의 어셈블리 또는 COM 개체에 대 한 종속성과 같은 다른 유형의 종속성을 나타낼 수도 있습니다. 이는 터치 없는 배포 기술 이므로는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 이러한 유형의 종속성을 다운로드 하 여 설치할 수 없지만 지정 된 종속성 중 하나 이상이 없는 경우 응용 프로그램이 실행 되지 않도록 합니다.

## <a name="dependentassembly"></a>dependentAssembly
 필수 요소. 이 요소는 요소를 포함 `assemblyIdentity` 합니다. 다음 표에서는에서 지 원하는 특성을 보여 줍니다 `dependentAssembly` .

| 특성 | 설명 |
|------------------| - |
| `preRequisite` | 선택 사항입니다. 이 어셈블리가 GAC에 이미 있어야 함을 지정 합니다. 유효한 값은 `true` 및 `false`입니다. `true`및 지정 된 어셈블리가 GAC에 없으면 응용 프로그램이 실행 되지 않습니다. |
| `visible` | 선택 사항입니다. 종속성을 포함 하 여 최상위 응용 프로그램 id를 식별 합니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]응용 프로그램 저장소 및 활성화를 관리 하기 위해에서 내부적으로 사용 됩니다. |
| `dependencyType` | 필수 요소. 이 종속성과 응용 프로그램 간의 관계입니다. 유효한 값은 다음과 같습니다.<br /><br /> -   `install`. 구성 요소는 현재 응용 프로그램에서 별도의 설치를 나타냅니다.<br />-   `preRequisite`. 구성 요소가 현재 응용 프로그램에 필요 합니다. |
| `codebase` | 선택 사항입니다. 응용 프로그램 매니페스트의 전체 경로입니다. |
| `size` | 선택 사항입니다. 응용 프로그램 매니페스트의 크기 (바이트)입니다. |

## <a name="assemblyidentity"></a>assemblyIdentity
 필수 요소. 이 요소는 `dependentAssembly` 요소의 자식입니다. 의 내용은 `assemblyIdentity` 응용 프로그램 매니페스트에 설명 된 것과 동일 해야 합니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 다음 표에서는 요소의 특성을 보여 줍니다 `assemblyIdentity` .

|특성|설명|
|---------------|-----------------|
|`Name`|필수 요소. 응용 프로그램의 이름을 식별 합니다.|
|`Version`|필수 요소. 응용 프로그램의 버전 번호를 다음 형식으로 지정 합니다. `major.minor.build.revision`|
|`publicKeyToken`|필수 요소. 응용 프로그램 또는 어셈블리가 서명 되는 공개 키의 SHA-1 해시의 마지막 8 바이트를 나타내는 16 자 16 진수 문자열을 지정 합니다. 서명 하는 데 사용 되는 공개 키는 2048 비트 이상 이어야 합니다.|
|`processorArchitecture`|필수 요소. 마이크로프로세서를 지정 합니다. 유효한 값은 `x86` 32 비트 windows 및 64 비트 windows에 대 한 것 `IA64` 입니다.|
|`Language`|선택 사항입니다. 어셈블리의 두 부분으로 구성 된 언어 코드를 식별 합니다. 예를 들어 EN-US는 영어 (미국)를 의미 합니다. 기본값은 `neutral`입니다. 이 요소는 `asmv2` 네임 스페이스에 있습니다.|
|`type`|선택 사항입니다. Windows side-by-side 설치 기술과의 이전 버전과의 호환성을 위한 것입니다. 유일 하 게 허용 되는 값은 `win32` 입니다.|

## <a name="hash"></a>hash
 요소는 `hash` 요소의 선택적 자식 요소입니다 `file` . `hash` 요소에는 특성이 없습니다.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램의 모든 파일에 대 한 알고리즘 해시를 보안 검사로 사용 하 여 배포 후 파일이 변경 되지 않도록 합니다. `hash`요소가 포함 되지 않은 경우에는이 검사가 수행 되지 않습니다. 따라서 요소를 생략 하는 `hash` 것은 권장 되지 않습니다.

## <a name="dsigtransforms"></a>dsig:Transforms
 요소는 `dsig:Transforms` 요소의 필수 자식 요소입니다 `hash` . `dsig:Transforms` 요소에는 특성이 없습니다.

## <a name="dsigtransform"></a>dsig:Transform
 요소는 `dsig:Transform` 요소의 필수 자식 요소입니다 `dsig:Transforms` . 다음 표에서는 요소의 특성을 보여 줍니다 `dsig:Transform` .

| 특성 | 설명 |
|-------------| - |
| `Algorithm` | 이 파일의 다이제스트를 계산 하는 데 사용 되는 알고리즘입니다. 현재에서 사용 되는 유일한 값은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `urn:schemas-microsoft-com:HashTransforms.Identity` 입니다. |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 요소는 `dsig:DigestMethod` 요소의 필수 자식 요소입니다 `hash` . 다음 표에서는 요소의 특성을 보여 줍니다 `dsig:DigestMethod` .

| 특성 | 설명 |
|-------------| - |
| `Algorithm` | 이 파일의 다이제스트를 계산 하는 데 사용 되는 알고리즘입니다. 현재에서 사용 되는 유일한 값은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `http://www.w3.org/2000/09/xmldsig#sha1` 입니다. |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 요소는 `dsig:DigestValue` 요소의 필수 자식 요소입니다 `hash` . `dsig:DigestValue` 요소에는 특성이 없습니다. 해당 텍스트 값은 지정 된 파일에 대해 계산 된 해시입니다.

## <a name="remarks"></a>설명
 일반적으로 배포 매니페스트에는 `assemblyIdentity` 응용 프로그램 매니페스트의 이름 및 버전을 식별 하는 단일 요소가 있습니다.

## <a name="example"></a>예
 다음 코드 예제에서는 `dependency` 배포 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
<!-- Identify the assembly dependencies -->
<dependency>
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>예
 다음 코드 예제에서는 GAC에 이미 설치 된 어셈블리에 대 한 종속성을 지정 합니다.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>예
 다음 코드 예제에서는 특정 버전의 공용 언어 런타임에 대 한 종속성을 지정 합니다.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />
  </dependentAssembly>
</dependency>
```

## <a name="example"></a>예
 다음 코드 예에서는 운영 체제 종속성을 지정 합니다.

```xml
<dependency>
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">
      <osVersionInfo>
         <os majorVersion="4" minorVersion="10" />
      </osVersionInfo>
   </dependentOS>
</dependency>
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
- [\<dependency> 요소인](../deployment/dependency-element-clickonce-application.md)
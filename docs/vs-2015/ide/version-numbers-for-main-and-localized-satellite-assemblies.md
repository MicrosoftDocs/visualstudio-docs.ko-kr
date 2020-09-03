---
title: 주 어셈블리 및 지역화된 위성 어셈블리의 버전 번호 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa064d875d5354ac4ae1fc5fdd8493c5efbbee01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663052"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>주 어셈블리 및 지역화된 위성 어셈블리의 버전 번호
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Resources.SatelliteContractVersionAttribute> 클래스는 리소스 관리자를 통해 지역화된 리소스를 사용하는 주 어셈블리에 대한 버전 관리 지원을 제공합니다. <xref:System.Resources.SatelliteContractVersionAttribute>를 애플리케이션의 주 어셈블리에 적용하면 위성 어셈블리를 업데이트하지 않고 어셈블리를 업데이트 및 재배포할 수 있습니다. 예를 들어 위성 어셈블리를 다시 빌드 및 다시 배포하지 않고 새 리소스를 도입하지 않은 서비스 팩과 함께 <xref:System.Resources.SatelliteContractVersionAttribute> 클래스를 사용할 수 있습니다. 지역화된 리소스를 사용하려면 주 어셈블리의 위성 계약 버전이 위성 어셈블리의 <xref:System.Reflection.AssemblyVersionAttribute> 클래스와 일치해야 합니다. <xref:System.Resources.SatelliteContractVersionAttribute>에서 정확한 버전 번호를 지정해야 하고 와일드카드 문자(예: “*”)는 허용되지 않습니다. 자세한 내용은 [데스크톱 응용 프로그램의 리소스 검색](https://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f)을 참조하세요.

## <a name="updating-assemblies"></a>어셈블리 업데이트
 <xref:System.Resources.SatelliteContractVersionAttribute> 클래스를 사용하여 위성 어셈블리를 업데이트할 필요 없이 주 어셈블리를 업데이트하거나 그 반대로 할 수 있습니다. 주 어셈블리가 업데이트되면 해당 어셈블리 버전 번호가 변경됩니다. 기존 위성 어셈블리를 계속 사용하려면 주 어셈블리의 버전 번호를 변경하고 위성 계약 버전 번호는 동일하게 유지합니다. 예를 들어 첫 번째 릴리스에서 주 어셈블리 버전은 1.0.0.0일 수 있습니다. 위성 계약 버전 및 위성 어셈블리의 어셈블리 버전도 1.0.0.0입니다. 서비스 팩을 적용하기 위해 주 어셈블리를 업데이트해야 할 경우 어셈블리 버전을 1.0.0.1로 업데이트할 수 있지만 위성 계약 버전 및 위성의 어셈블리 버전은 1.0.0.0으로 유지합니다.

 주 어셈블리를 업데이트하지 않고 위성 어셈블리를 업데이트해야 할 경우에는 위성 어셈블리의 <xref:System.Reflection.AssemblyVersionAttribute>를 변경합니다. 위성 어셈블리와 함께 새 위성 어셈블리가 이전 위성 어셈블리와 호환됨을 명시하는 정책 어셈블리를 전달해야 합니다. 정책에 대한 자세한 내용은 [런타임에서 어셈블리를 찾는 방법](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)을 참조하세요.

 다음 코드는 위성 계약 버전을 설정하는 방법을 보여 줍니다. 코드는 AssemblyInfo.vb 또는 AssemblyInfo.cs 파일이나 빌드 스크립트에 삽입할 수 있습니다.

```vb
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>

```

```csharp
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]
```

## <a name="see-also"></a>관련 항목
 [런타임에서 어셈블리를 찾는 방법](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34) [어셈블리 특성 설정](https://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e) [보안 및 지역화 된 위성 어셈블리](../ide/security-and-localized-satellite-assemblies.md) [응용 프로그램 지역화](../ide/localizing-applications.md) 응용 프로그램 [전역화 및 지역화](../ide/globalizing-and-localizing-applications.md)

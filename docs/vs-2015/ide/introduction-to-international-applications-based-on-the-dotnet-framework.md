---
title: .NET Framework 기반의 국가별 애플리케이션 소개 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0d57cee8591196d12e51e58fb0e5e6a4a2cdf94a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75848372"
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>.NET Framework 기반의 국가별 애플리케이션 소개
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에는 지역화 대비 애플리케이션을 만드는 두 개의 부분으로, 다양한 문화권에 맞게 조정할 수 있는 애플리케이션을 디자인하는 프로세스인 전역화 및 특정 문화권에 맞게 리소스를 변환하는 프로세스인 지역화가 있습니다. 전 세계 대상을 위한 애플리케이션을 디자인하는 방법에 대한 일반 정보는 [지역화 대비 애플리케이션 개발을 위한 최선의 구현 방법](https://msdn.microsoft.com/library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c)을 참조하세요.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 지역화 모델은 애플리케이션 코드 및 대체(fallback) 리소스가 둘 다 포함된 주 어셈블리와 애플리케이션이 개발된 원래 언어에 대한 기타 개체로 구성됩니다. 각 지역화된 애플리케이션에는 위성 어셈블리 또는 지역화된 리소스만 들어 있는 어셈블리가 포함됩니다. 주 어셈블리에는 항상 대체 리소스가 포함되므로 지역화된 위성 어셈블리에서 리소스를 찾을 수 없으면 <xref:System.Resources.ResourceManager>는 계층 구조 방식으로 리소스를 로드하려고 시도하고 결국 주 어셈블리의 리소스를 대체합니다. 리소스 대체(fallback) 시스템은 [지역화를 위한 리소스의 계층적 구성](../ide/hierarchical-organization-of-resources-for-localization.md)에서 자세히 설명합니다.

 모든 Microsoft 지역화된 제품에 대한 용어집을 지역화 리소스로 사용하는 것이 좋습니다. 이 CSV 파일에는 12,000개가 넘는 영어 용어와 최대 59개 언어의 용어 번역이 포함됩니다. 용어집은 [Microsoft 용어 번역](https://msdn.microsoft.com/goglobal/bb688105.aspx) 웹 페이지에서 다운로드할 수 있습니다.

 Windows Forms 애플리케이션에 대한 프로젝트 시스템에서는 대체(fallback) 및 각각의 원하는 추가 UI 문화권에 대한 리소스 파일을 생성할 수 있습니다. 대체(fallback) 리소스 파일은 주 어셈블리에 빌드되고 문화권별 리소스 파일은 문화권마다 하나씩 위성 어셈블리에 빌드됩니다. 프로젝트를 빌드할 때 리소스 파일은 Visual Studio XML 형식(.resx)에서 중간 이진 형식(.resources)으로 컴파일되어 위성 어셈블리에 포함됩니다.

 Windows Forms 및 Web Forms에 대한 프로젝트 시스템에서는 어셈블리 리소스 파일 템플릿을 사용하여 리소스 파일을 빌드하고, 리소스에 액세스하고, 프로젝트를 빌드할 수 있습니다. 위성 어셈블리는 주 어셈블리와 함께 만들어집니다.

 지역화된 애플리케이션이 실행될 때 해당 모양은 두 개의 문화권 값에 따라 결정됩니다. *문화권* 은 사용자의 언어, 환경 및 문화권 규칙과 관련 된 사용자 기본 설정 정보 집합입니다. UI culture 설정에 따라 로드 되는 리소스가 결정 됩니다. UI 문화권은 Web.config 파일 및 페이지 지시문에서는 `UICulture`로 설정되고 Visual Basic 또는 Visual C# 코드에서는 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A>로 설정됩니다. 문화권 설정에 따라 날짜, 숫자, 통화 등의 값 서식이 결정됩니다. 문화권은 Web.config 파일 및 페이지 지시문에서는 `Culture`로 설정되고 Visual Basic 또는 Visual C# 코드에서는 <xref:System.Globalization.CultureInfo.CurrentCulture%2A>로 설정됩니다.

## <a name="see-also"></a>관련 항목
 <xref:System.Globalization> <xref:System.Resources>
 [응용 프로그램](../ide/globalizing-and-localizing-applications.md) [보안 및 지역화 된 위성 어셈블리](../ide/security-and-localized-satellite-assemblies.md) 전역화 및 지역화

---
title: 보안 및 지역화된 위성 어셈블리 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 866e313a36af5ef72f910a5eafbf7b31c971d890
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672905"
---
# <a name="security-and-localized-satellite-assemblies"></a>보안 및 지역화된 위성 어셈블리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

주 어셈블리에 강력한 이름 지정이 사용될 경우 주 어셈블리와 같은 프라이빗 키를 사용하여 위성 어셈블리에 서명해야 합니다. 주 어셈블리와 위성 어셈블리 간에 퍼블릭/프라이빗 키 쌍이 일치하지 않으면 리소스가 로드되지 않습니다. 어셈블리 서명에 대한 자세한 내용은 [방법: 강력한 이름으로 어셈블리 서명](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67)을 참조하세요.

 일반적으로 조직의 서명 그룹 또는 외부 서명 조직이 프라이빗 키로 서명하도록 해야 할 수 있습니다. 이는 액세스가 보통 몇몇 개인으로 제한된다는 프라이빗 키의 민감한 특성 때문입니다. 개발 중에 지연된 서명을 사용할 수 있습니다. 자세한 내용은 [어셈블리 서명 연기](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [어셈블리 보안 고려 사항](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067) [주요 보안 개념](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98) .NET Framework [응용 프로그램 지역화](../ide/localizing-applications.md) 응용 프로그램 [전역화 및 지역화](../ide/globalizing-and-localizing-applications.md) 응용 프로그램 [을 기반으로 하는 국가별 응용 프로그램 소개](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)

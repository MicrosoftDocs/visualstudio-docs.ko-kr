---
title: 64 비트 응용 프로그램의 필수 구성 요소 배포 | Microsoft Docs
description: 64 비트 플랫폼에서 응용 프로그램의 ClickOnce 배포에 대 한 필수 구성 요소로 사용할 수 있는 재배포 가능 패키지에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c051e57bb6af707e7bd5c096e230966e98498bd2
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382912"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>64비트 애플리케이션의 필수 구성 요소 배포
ClickOnce 배포에서는 64비트 플랫폼에 애플리케이션을 설치할 수 있습니다. 대상 플랫폼은 32비트 플랫폼의 경우 **x86** , AMD64/EM64T 명령 집합을 지원하는 머신의 경우 **x64** , 64비트 Itanium 프로세서의 경우 **Itanium** 입니다.

## <a name="prerequisites"></a>필수 구성 요소
 다음 테이블에는 64비트 애플리케이션 설치의 필수 구성 요소로 사용할 수 있는 재배포 가능 파일이 나와 있습니다.

 64비트 구성 요소가 없는 필수 구성 요소를 선택하면 선택한 패키지를 64비트 플랫폼에서 사용할 수 없다는 경고가 표시될 수 있습니다.

| 재배포 가능 파일 | x64 지원 | IA64 지원 |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | 예 | 아니요 |
| Visual C++ 2010 런타임 라이브러리(IA64) | 아니요 | 예 |
| Visual C++ 2010 런타임 라이브러리(x64) | 예 | 아니요 |
| Microsoft .NET Framework 4(x86 및 x64) | 예 | |
| Microsoft .NET Framework 4 Client Profile(x86 및 x64) | 예 | |

## <a name="see-also"></a>참조
- [응용 프로그램, 서비스 및 구성 요소 배포](../deployment/deploying-applications-services-and-components.md)
- [방법: ClickOnce 애플리케이션을 사용하여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [64비트 애플리케이션](/dotnet/framework/64-bit-apps)
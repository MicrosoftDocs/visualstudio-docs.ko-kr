---
title: 64 비트 응용 프로그램의 필수 구성 요소 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92f30e8e059475c907da184aa59a8e4b7a2cf19f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675577"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>64비트 애플리케이션의 필수 구성 요소 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 배포에서는 64비트 플랫폼에 애플리케이션을 설치할 수 있습니다. 대상 플랫폼은 32비트 플랫폼의 경우 **x86**, AMD64/EM64T 명령 집합을 지원하는 머신의 경우 **x64**, 64비트 Itanium 프로세서의 경우 **Itanium**입니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 다음 테이블에는 64비트 애플리케이션 설치의 필수 구성 요소로 사용할 수 있는 재배포 가능 파일이 나와 있습니다.  
  
 64비트 구성 요소가 없는 필수 구성 요소를 선택하면 선택한 패키지를 64비트 플랫폼에서 사용할 수 없다는 경고가 표시될 수 있습니다.  
  
|재배포 가능 파일|x64 지원|IA64 지원|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|예|예|  
|Visual C++ 2010 런타임 라이브러리(IA64)|예|예|  
|Visual C++ 2010 런타임 라이브러리(x64)|예|예|  
|Microsoft .NET Framework 4(x86 및 x64)|예||  
|Microsoft .NET Framework 4 Client Profile(x86 및 x64)|예||  
  
## <a name="see-also"></a>참고 항목  
 [응용 프로그램, 서비스 및 구성 요소 배포](../deployment/deploying-applications-services-and-components.md)   
 [방법: ClickOnce 응용 프로그램을 사용 하 여 필수 구성 요소 설치](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64비트 애플리케이션](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)

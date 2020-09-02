---
title: 디버깅 및 호스팅 프로세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 10f3968367b188203671fa6bfff48bc482efe4f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157890"
---
# <a name="debugging-and-the-hosting-process"></a>디버깅 및 호스팅 프로세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 호스팅 프로세스를 사용하면 디버거 성능을 향상시킬 수 있고 부분 신뢰 디버깅 및 디자인 타임 식 계산 등과 같은 새로운 디버거 기능을 사용할 수 있습니다. 필요한 경우 호스팅 프로세스를 비활성화할 수 있습니다. 자세한 내용은 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md)을 참조하세요. 다음 섹션에서는 호스팅 프로세스를 사용하는 경우와 사용하지 않는 경우의 몇 가지 디버깅 차이점에 대해 설명합니다.  
  
## <a name="partial-trust-debugging-and-click-once-security"></a>부분 신뢰 디버깅 및 ClickOnce 보안  
 부분 신뢰 디버깅에는 호스팅 프로세스가 필요합니다. 호스팅 프로세스를 비활성화하면 **프로젝트 속성** 의 **보안**페이지에서 부분 신뢰 보안을 활성화한 경우라 해도 부분 신뢰 디버깅이 실행되지 않습니다. 자세한 내용은 [How to: Disable the Hosting Process](../ide/how-to-disable-the-hosting-process.md) 및 [How to: Debug a Partial Trust Application](../debugger/how-to-debug-a-partial-trust-application.md)를 참조하세요.  
  
## <a name="design-time-expression-evaluation"></a>디자인 타임 식 계산  
 디자인 타임 식에는 항상 호스팅 프로세스가 사용됩니다. **프로젝트 속성** 에서 호스팅 프로세스를 비활성화하면 클래스 라이브러리 프로젝트에 대한 디자인 타임 식 계산이 비활성화됩니다. 다른 프로젝트 형식에 대해서는 디자인 타임 식 계산이 비활성화되지 않습니다. 대신 Visual Studio가 실제 실행 파일을 시작하고 호스팅 프로세스 없이 디자인 타임 계산에 이 실행 파일을 사용합니다. 이러한 차이로 인해 서로 다른 결과가 발생할 수 있습니다.  
  
## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName의 반환 결과  
 `AppDomain.CurrentDomain.FriendlyName` 은 호스팅 프로세스가 활성화되어 있는지 여부에 따라 서로 다른 결과를 반환합니다. 호스팅 프로세스를 사용할 수 있는 상태에서 `AppDomain.CurrentDomain.FriendlyName` 을 호출하면 *app_name*`.vhost.exe`이 반환됩니다. 호스팅 프로세스를 사용할 수 없는 상태에서 호출하면 *app_name*`.exe`이 반환됩니다.  
  
## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName의 반환 결과  
 `Assembly.GetCallingAssembly().FullName` 은 호스팅 프로세스가 활성화되어 있는지 여부에 따라 서로 다른 결과를 반환합니다. 호스팅 프로세스를 사용할 수 있는 상태에서 `Assembly.GetCallingAssembly().FullName` 을 호출하면 `mscorlib`가 반환됩니다. 호스팅 프로세스를 사용할 수 없는 상태에서 `Assembly.GetCallingAssembly().FullName` 을 호출하면 애플리케이션 이름이 반환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [호스팅 프로세스 (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [방법: 부분 신뢰 응용 프로그램 디버깅](../debugger/how-to-debug-a-partial-trust-application.md)   
 [방법: 호스팅 프로세스 사용 안 함](../ide/how-to-disable-the-hosting-process.md)

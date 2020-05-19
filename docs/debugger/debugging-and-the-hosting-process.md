---
title: 디버깅 및 호스팅 프로세스 | Microsoft Docs
ms.date: 08/01/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], hosting process
- hosting process
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f77df2eae643b658e915662e0f50f6a376141d27
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188464"
---
# <a name="debugging-and-the-hosting-process"></a>디버깅 및 호스팅 프로세스
Visual Studio 호스팅 프로세스를 사용하면 디버거 성능을 향상시킬 수 있고 부분 신뢰 디버깅 및 디자인 타임 식 계산 등과 같은 새로운 디버거 기능을 사용할 수 있습니다. 필요한 경우 호스팅 프로세스를 비활성화할 수 있습니다. 다음 섹션에서는 호스팅 프로세스를 사용하는 경우와 사용하지 않는 경우의 몇 가지 디버깅 차이점에 대해 설명합니다.

> [!NOTE]
> Visual Studio 2017부터 호스팅 프로세스를 사용하여 디버그하는 옵션은 더 이상 필요하지 않으므로 제거되었습니다. 자세한 내용은 [Debugging: Visual Studio 2017 Aims To Speed Up Your Least Favorite Job](https://vslive.com/Blogs/News-and-Tips/2017/02/Debugging-Visual-Studio-2017-aims-to-speed-up-your-least-favorite-job.aspx)(디버깅: 번거로운 작업을 빠르게 처리하도록 설계된 Visual Studio 2017)을 참조하세요.

## <a name="partial-trust-debugging-and-click-once-security"></a>부분 신뢰 디버깅 및 ClickOnce 보안
 부분 신뢰 디버깅에는 호스팅 프로세스가 필요합니다. 호스팅 프로세스를 비활성화하면 **프로젝트 속성** 의 **보안**페이지에서 부분 신뢰 보안을 활성화한 경우라 해도 부분 신뢰 디버깅이 실행되지 않습니다. 자세한 내용은 [방법: 부분 신뢰 애플리케이션 디버그](debugger-security.md)를 참조하세요.

## <a name="design-time-expression-evaluation"></a>디자인 타임 식 계산
 디자인 타임 식에는 항상 호스팅 프로세스가 사용됩니다. **프로젝트 속성** 에서 호스팅 프로세스를 비활성화하면 클래스 라이브러리 프로젝트에 대한 디자인 타임 식 계산이 비활성화됩니다. 다른 프로젝트 형식에 대해서는 디자인 타임 식 계산이 비활성화되지 않습니다. 대신 Visual Studio가 실제 실행 파일을 시작하고 호스팅 프로세스 없이 디자인 타임 계산에 이 실행 파일을 사용합니다. 이러한 차이로 인해 서로 다른 결과가 발생할 수 있습니다.

## <a name="appdomaincurrentdomainfriendlyname-differences"></a>AppDomain.CurrentDomain.FriendlyName의 반환 결과
 `AppDomain.CurrentDomain.FriendlyName` 은 호스팅 프로세스가 활성화되어 있는지 여부에 따라 서로 다른 결과를 반환합니다. 호스팅 프로세스를 사용할 수 있는 상태에서 `AppDomain.CurrentDomain.FriendlyName` 을 호출하면 *app_name*`.vhost.exe`이 반환됩니다. 호스팅 프로세스를 사용할 수 없는 상태에서 호출하면 *app_name*`.exe`이 반환됩니다.

## <a name="assemblygetcallingassemblyfullname-differences"></a>Assembly.GetCallingAssembly().FullName의 반환 결과
 `Assembly.GetCallingAssembly().FullName` 은 호스팅 프로세스가 활성화되어 있는지 여부에 따라 서로 다른 결과를 반환합니다. 호스팅 프로세스를 사용할 수 있는 상태에서 `Assembly.GetCallingAssembly().FullName` 을 호출하면 `mscorlib`가 반환됩니다. 호스팅 프로세스를 사용할 수 없는 상태에서 `Assembly.GetCallingAssembly().FullName` 을 호출하면 애플리케이션 이름이 반환됩니다.

## <a name="see-also"></a>참조

- [방법: 부분 신뢰 애플리케이션 디버그](debugger-security.md)
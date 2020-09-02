---
title: UWP 앱에서 프리페치된 콘텐츠를 사용하여 디버그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 65b889452a23bb970cbee4c65455679a3473abab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348069"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>Visual Studio에서 프리페치된 콘텐츠를 사용하여 UWP 앱 디버그

 UWP 앱의 응답성을 향상하려면 Windows에 웹 페이지 또는 이미지 등의 일부 웹 콘텐츠를 앱의 [WinINet](/windows/desktop/WinInet/about-wininet) 캐시에 미리 로드하도록 요청할 수 있습니다. 이 기능을 프리페치라고 합니다. 시작 시에 사용되는 콘텐츠에 특히 효과적이지만 자주 사용되는 다른 콘텐츠도 프리페치할 수 있습니다. [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher) 클래스의 메서드를 사용하면 미리 로드할 콘텐츠의 URI를 지정할 수 있습니다. 앱에 ContentPrefetcher 기능을 추가하는 방법에 대한 예제는 Windows SDK [콘텐츠 프리페치 샘플](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)을 참조하십시오.

 Windows는 휴리스틱을 사용하여 프리페치를 수행하는 시기와 필요성 및 어떤 리소스를 다운로드할지 결정합니다. 휴리스틱은 시스템 네트워크 및 전력 조건, 사용자 응용 프로그램 사용 내용, 이전 프리페치 시도 결과를 고려합니다. Visual Studio에서는 **Windows 스토어 앱 프리페치 트리거** 명령을 사용하여 Windows에서 ContentPrefetcher 휴리스틱을 무시하고 지정된 웹 콘텐츠 전체를 강제로 미리 로드할 수 있습니다. 이것은 알려진 상태(로드 여부와 관계없음)로 프리페치할 콘텐츠로 응용 프로그램의 동작 또는 성능을 테스트할 때 유용할 수 있습니다.

## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>ContentPrefetcher 지정 리소스를 강제로 미리 로드하려면
 이 절차는 이미 ContentPrefetcher 기능을 설정하고 응용 프로그램 프로젝트에서 미리 로드할 콘텐츠 URI를 지정했다는 가정 하에 진행됩니다. 지정된 리소스를 새로 만들거나 수정하는 경우 강제로 콘텐츠를 미리 로드하려면 **Windows 스토어 앱 프리페치 트리거** 명령을 선택하기 전에 앱을 시작했다가 종료해야 합니다. 먼저 응용 프로그램을 실행하여 URI를 등록합니다. 그러면 **Windows 스토어 앱 프리페치 트리거** 명령을 통해 ContentPrefetcher에서 강제로 콘텐츠를 다운로드하여 캐시를 추가합니다. 후속 응용 프로그램 실행 시 콘텐츠가 미리 로드되었다고 가정할 수 있습니다.

1. 응용 프로그램을 시작하여 프리페치 콘텐츠 URI를 앱과 함께 등록합니다. **디버그** 메뉴에서 **디버깅 시작**(키보드 바로 가기: F5)을 선택합니다.

2. **디버그** 메뉴에서 **디버깅 중지**를 선택합니다(바로 가기 키: Shift+F5).

3. **디버그** 메뉴에서 **기타 디버그 대상**을 선택한 다음, **Windows 스토어 앱 프리페치 트리거**를 선택합니다.

   이제 프리페치된 웹 리소스로 응용 프로그램을 디버그, 테스트 또는 분석할 수 있습니다.

> [!NOTE]
> 지정된 웹 콘텐츠를 추가 또는 수정할 때마다 이러한 단계를 반복합니다.

## <a name="see-also"></a>참조
- [블로그 게시물: Visual Studio 2013 업데이트 2에서 Windows 스토어 앱의 프리페치 트리거](https://devblogs.microsoft.com/devops/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)
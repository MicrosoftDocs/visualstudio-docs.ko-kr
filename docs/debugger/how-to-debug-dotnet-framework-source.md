---
title: '방법: .NET Framework 소스 디버그 | Microsoft Docs'
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 25f40b0528b794863aabdb13ed9785d2b0c551b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894276"
---
# <a name="how-to-debug-net-framework-source"></a>방법: .NET Framework 소스 디버그

.NET Framework 소스를 디버그하려면 다음이 필요합니다.

- .NET Framework 소스 단계별 실행을 사용하도록 설정해야 합니다.

- 코드에 대한 디버깅 기호에 액세스할 수 있어야 합니다.

  디버깅 기호를 즉시 다운로드하도록 선택할 수도 있고 나중에 다운로드하도록 옵션을 설정할 수도 있습니다. 기호를 즉시 다운로드하지 않으면 다음에 앱을 디버그하기 시작할 때 다운로드됩니다. 디버그하는 동안 **모듈** 또는 **호출 스택** 창을 사용하여 기호를 다운로드하고 로드할 수도 있습니다.

### <a name="to-enable-stepping-into-net-framework-source"></a>.NET Framework 소스 단계별 실행을 사용하도록 설정하려면

1. **도구**(또는 **디버그**) > **옵션** > **디버깅** > **일반**에서 **.NET Framework 소스 단계별 실행 사용**을 선택합니다.

   - 내 코드만을 사용하는 경우에는 내 코드만을 이제 사용하지 않는다는 경고 대화 상자가 표시됩니다. **확인**을 선택합니다.

   - 로컬 기호 캐시가 설정되어 있지 않았던 경우 경고 대화 상자에서 기본 기호 캐시가 설정되었음을 알려 줍니다. **확인**을 선택합니다.

1. **확인**을 선택하여 **옵션** 대화 상자를 닫습니다.

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>기호 소스 위치 및 로드 동작을 설정하거나 변경하려면

1. **도구**(또는 **디버그**) > **옵션** > **디버깅**에서 **기호** 범주를 선택합니다.

1. **기호** 페이지의 **기호 파일(.pdb) 위치**에서 **Microsoft 기호 서버**를 선택하여 공용 Microsoft 기호 서버의 기호에 액세스합니다. 도구 모음 단추를 선택하여 다른 기호 위치를 추가하고 로드 순서를 변경합니다.

1. 로컬 기호 캐시를 변경하려면 **이 디렉터리의 기호 캐시**에서 다른 위치를 편집하거나 찾아봅니다.

1. 기호를 즉시 다운로드하려면 **모든 기호 로드**를 선택합니다. 이 단추는 디버그하는 동안에만 사용할 수 있습니다.

   지금 기호를 다운로드하지 않으면 다음에 디버그하기 시작할 때 다운로드됩니다.

1. **확인**을 선택하여 **옵션** 대화 상자를 닫습니다.

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>모듈 또는 호출 스택 창에서 기호를 로드하려면

1. 디버그하는 동안 **디버그** > **창** > **모듈**을 선택하거나(또는 **Ctrl + Alt + U**를 누름) **디버그** > **창** > **호출 스택**(**Ctrl + Alt + C**)을 선택하여 창을 엽니다.

1. 기호가 로드되지 않은 모듈을 마우스 오른쪽 단추로 클릭합니다. **모듈** 창에서는 기호 로드 상태가 **기호 상태** 열에 있습니다. **호출 스택** 창에서는 상태가 **프레임 상태** 열에 있으며 프레임은 회색으로 표시됩니다.

   - 메뉴에서 **기호 로드**를 선택하여 컴퓨터의 폴더에서 기호 파일을 찾아 로드합니다.

   - **기호 로드 정보**를 선택하여 디버거가 기호를 검색한 위치를 표시합니다.

   - **기호 설정**을 선택하여 **기호** 페이지를 엽니다. **기호** 페이지의 **기호 파일(.pdb) 위치**에서 **Microsoft 기호 서버**를 선택하여 공용 Microsoft 기호 서버의 기호에 액세스합니다. 도구 모음 단추를 선택하여 다른 기호 위치를 추가하고 로드 순서를 변경합니다. **확인**을 선택하여 대화 상자를 닫습니다.

### <a name="see-also"></a>참조
- [관리 코드 디버깅](../debugger/debugging-managed-code.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
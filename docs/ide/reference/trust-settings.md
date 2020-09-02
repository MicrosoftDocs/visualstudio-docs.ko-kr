---
title: 파일 및 폴더에 대한 신뢰 설정
description: Visual Studio를 안전하게 유지하기 위해 파일 및 폴더에 대한 신뢰 설정을 변경하는 방법을 알아봅니다.
author: 2percentsilk
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 492a94962d255a9d18dcabdababf7fa6a540ada1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88197386"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>파일 및 폴더에 대한 신뢰 설정 구성

Visual Studio는 [MOTW(Mark of the Web)](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85))가 포함된 프로젝트를 열기 전에 사용자 승인 확인 메시지를 표시합니다. MOTW(Mark of the Web) 특성을 가졌거나 *신뢰할 수 있음*으로 지정되지 않은 파일 또는 폴더를 열기 전에 사용자 승인을 확인하는 메시지를 표시하도록 Visual Studio를 구성할 수도 있습니다. 파일 및 폴더 검사는 기본적으로 비활성화됩니다.

> [!WARNING]
> 승인하기 전에 파일, 폴더 또는 솔루션이 신뢰할 수 있는 사람 또는 신뢰할 수 있는 위치로부터 계속 제공될 수 있도록 해야 합니다.

## <a name="configure-trust-settings"></a>신뢰 설정 구성

신뢰 설정을 변경하려면 다음 단계를 수행합니다.

1. **도구** > **옵션** > **신뢰 설정**을 열고 오른쪽 창에서 **신뢰 설정 구성** 링크를 선택합니다.

2. 파일 및 폴더에 대한 원하는 검사 수준을 선택합니다. 각각에 대해 다른 검사를 수행할 수 있습니다. 옵션은 다음과 같습니다.

   * **확인 안 함**: Visual Studio에서 검사를 수행하지 않습니다.

   * **MOTW(Mark of the Web) 특성 확인**: 파일 또는 폴더에 MOTW(Mark of the Web) 특성이 있으면 Visual Studio에서 여는 것을 차단하고 열 수 있는 권한을 요청합니다.

   * **신뢰할 수 있는 경로인지 확인**: 파일 또는 폴더 경로가 **신뢰할 수 있는 경로** 목록에 없으면 Visual Studio에서 여는 것을 차단하고 열 수 있는 권한을 요청합니다.

   ![신뢰 확인 옵션](media/trust-settings.png)

## <a name="add-trusted-paths"></a>신뢰할 수 있는 경로 추가

신뢰할 수 있는 경로를 추가하려면 다음 단계를 수행합니다.

1. **도구** > **옵션** > **신뢰 설정**을 열고 오른쪽 창에서 **신뢰 설정 구성** 링크를 선택합니다.

2. **신뢰 설정** 대화 상자에서 **추가**를 클릭한 후 **파일** 또는 **폴더**를 선택합니다.

3. 신뢰할 수 있는 목록에 추가하려는 파일 또는 폴더로 이동하여 선택합니다.

   파일 또는 폴더 경로가 **신뢰할 수 있는 경로** 목록에 표시됩니다.

   ![추가된 신뢰할 수 있는 경로](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>신뢰할 수 있는 경로 제거

신뢰할 수 있는 경로를 제거하려면 다음 단계를 수행합니다.

1. **도구** > **옵션** > **신뢰 설정**을 열고 오른쪽 창에서 **신뢰 설정 구성** 링크를 선택합니다.

2. **신뢰할 수 있는 경로** 목록에서 제거하려는 경로를 선택하고 **제거**를 클릭합니다.

   > [!TIP]
   > 여러 항목을 선택하려면 **Shift**를 누른 상태로 경로를 선택합니다.

   선택한 경로가 **신뢰할 수 있는 경로** 목록에서 제거됩니다.

---
title: '연습: 그래픽 정보 캡처 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aab86d42cd158ad64ebb16497b8d2d9f5a7002df
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734735"
---
# <a name="walkthrough-capturing-graphics-information"></a>연습: 그래픽 정보 캡처
이 연습에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 그래픽 진단을 사용하여 Direct3D 앱에서 그래픽 정보를 수동으로 캡처하는 방법을 보여 줍니다.

 이 연습에서는 다음 작업을 설명합니다.

- 앱에 그래픽 진단 후크

- 그래픽 정보 캡처

## <a name="capturing-graphics-information"></a>그래픽 정보 캡처
 그래픽 진단 도구를 사용하려면 먼저, 이 도구에서 사용하는 그래픽 정보를 캡처해야 합니다. 캡처를 사용하도록 설정하려면 **진단 시작** 명령을 사용하여 앱이 시작될 때 그래픽 진단을 후크합니다.

#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>프로젝트 또는 솔루션이 로드된 후 그래픽 정보 캡처를 사용하도록 설정하려면

1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 그래픽 정보를 캡처하려는 앱용 프로젝트 또는 솔루션 파일을 로드합니다.

2. 그래픽 진단 도구 모음에서 **진단 시작**을 선택합니다.

#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>프로젝트 또는 솔루션을 로드하지 않고 그래픽 정보 캡처를 사용하도록 설정하려면

1. 메뉴 모음에서 **파일**, **열기**, **프로젝트/솔루션**을 선택합니다. **프로젝트 열기** 대화 상자가 나타납니다.

2. 프로젝트 또는 솔루션 파일 대신, 그래픽 정보를 캡처할 앱용 실행 파일을 지정한 후 **열기**를 선택합니다.

3. 메뉴 모음에서 **디버그**, **그래픽**, **진단 시작**을 선택합니다.

   응용 프로그램을 시작하고 프레임을 렌더링한 후 그래픽 정보를 캡처할 수 있습니다.

#### <a name="to-capture-graphics-information"></a>그래픽 정보를 캡처하려면

- 그래픽 진단 도구 모음에서 **캡처** 단추를 선택합니다. ![그래픽 캡처 단추 아이콘](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")

   또는

   앱에 포커스가 있는 상태에서 **Print Screen**을 누릅니다.

  프레임에 대한 정보를 캡처할 때마다 그래픽 진단 기능은 Direct3D 이벤트와 연결된 상태를 기록하고 그래픽 로그에 해당 데이터를 추가합니다. 각 그래픽 진단 세션에 대해 새 그래픽 로그가 생성됩니다. 그래픽 로그에 관한 자세한 내용은 [개요](overview-of-visual-studio-graphics-diagnostics.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계
 이 연습에서는 그래픽 정보를 수동으로 캡처하는 방법을 보여 주었습니다. 다음 단계로 아래 옵션을 고려해 보세요.

- 그래픽 진단 도구를 사용하여 캡처한 그래픽 정보를 분석하는 방법에 대해 알아봅니다. [개요](overview-of-visual-studio-graphics-diagnostics.md)를 참조하세요.

## <a name="see-also"></a>참조
- [Capturing Graphics Information](capturing-graphics-information.md)
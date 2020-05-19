---
title: 그래픽 프레임 유효성 검사 | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49248c6209f9e56e51551f6cd3d4af66ecac8b56
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735494"
---
# <a name="graphics-frame-validation"></a>그래픽 프레임 유효성 검사
<!-- VERSIONLESS -->
Visual Studio 2017 이상에서는 **프레임 유효성 검사** 도구를 지원합니다.  프레임 유효성 검사 창에는 이벤트 목록과 관련된 오류 및 경고가 표시됩니다.  이 창을 보려면 **보기 > 프레임 유효성 검사** 메뉴를 선택합니다.

![프레임 유효성 검사](media/gfx_diag_frame_validation.png)

왼쪽 위 모서리에서 **유효성 검사 실행** 단추를 클릭하여 분석을 시작합니다.  프레임의 복잡성에 따라 완료하는 데 몇 분 정도 걸릴 수 있습니다.  여기에 두 가지 소스의 데이터가 표시됩니다. 즉, [SDK 계층](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers)을 사용할 수 있을 때 D3D 자체에서 내보내는 메시지와 도구 자체 내부 상태 추적에서 수집되는 데이터가 조합되어 표시됩니다. 완료되면 다음과 같은 여러 데이터 열이 표시됩니다.

| **열** | **설명** |
|------------| - |
| 이벤트 ID | [이벤트 목록](graphics-event-list.md) 창의 항목에 매핑되는 ID입니다. |
| 심각도 | 손상, 오류, 경고, 정보 또는 메시지입니다. |
| 범주 | 애플리케이션 정의, 기타, 초기화, 정리, 컴파일, 상태 만들기, 상태 설정, 상태 가져오기, 실행, 리소스 조작, 셰이더, 중복 및 사용 안 함입니다. |
| 메시지 | 이벤트와 연결된 메시지입니다. |
| 이벤트 | 오류 또는 경고와 관련된 이벤트입니다. |

## <a name="see-also"></a>참조
[그래픽 진단(DirectX 그래픽 디버그)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->
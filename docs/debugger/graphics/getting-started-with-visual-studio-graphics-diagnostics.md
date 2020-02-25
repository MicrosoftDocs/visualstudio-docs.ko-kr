---
title: 그래픽 진단 시작 | Microsoft Docs
ms.custom: seodec18
ms.date: 05/26/2017
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 575b0254768ac359e43cd5b04c23a220549ac973
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557923"
---
# <a name="getting-started-with-visual-studio-graphics-diagnostics"></a>Visual Studio 그래픽 진단 시작
이 섹션에서는 처음으로 그래픽 진단 사용을 준비한 다음 Direct3D 앱에서 프레임을 캡처하고 Graphics Analyzer에서 검사합니다.

## <a name="requirements"></a>요구 사항
 Visual Studio에서 그래픽 진단를 사용 하려면 Visual Studio Enterprise, Visual Studio Professional 또는 Visual Studio Community를 사용 해야 합니다.  Visual Studio Code를 비롯 한 다른 버전은이 기능을 포함 하지 않습니다.

 [!INCLUDE[downloadvs](../includes/downloadvs_md.md)]

### <a name="windows-10-prerequisites"></a>Windows 10 필수 조건
 선택적 Windows 기능인 *그래픽 도구*는 Windows 10에서 그래픽 진단에 필요한 캡처 및 재생 인프라를 제공합니다.

 그래픽 도구를 설치하는 방법에 대한 자세한 내용은 [Windows 10용 그래픽 도구 설치](#InstallGraphicsTools)를 참조하세요.

## <a name="InstallGraphicsTools"></a> Windows 10용 그래픽 도구 설치
 Windows 10에서 그래픽 진단 인프라는 *그래픽 도구*라는 Windows의 선택적 기능에서 제공합니다. 이 기능은 캡처할 앱이 이전 버전의 Windows를 대상으로 하는지 여부나 사용하는 Direct3D 버전에 관계없이 Windows 10에서 그래픽 정보를 캡처하고 재생하는 데 필요합니다. 그래픽 도구 기능을 미리 설치하도록 선택할 수 있습니다. 그렇지 않으면 처음으로 Visual Studio에서 그래픽 진단 세션을 시작할 때 주문형으로 설치됩니다.

#### <a name="to-install-graphics-tools-for-windows-10"></a>Windows 10용 그래픽 도구를 설치하려면

1. 검색에서 **앱 및 기능** 을 입력 한 다음 **앱 & 기능** 설정을 엽니다.

2. **앱 & 기능** 설정의 오른쪽에서 **선택적 기능** ( **앱 & 기능**)을 선택 합니다.

   **선택적 기능** 설정이 표시 됩니다.

3. **선택적 기능** 설정에서 **기능 추가**를 선택 합니다. 설치할 수 있는 선택적 기능 목록이 나타납니다.

4. 기능 목록에서 **그래픽 도구**를 선택한 다음, **설치**를 선택합니다.

   또한 그래픽 도구 기능은 Windows 10 SDK를 설치할 때 자동으로 설치됩니다.

> [!TIP]
> Windows 10의 선택적 그래픽 도구 기능은 개발자 도구가 설치되지 않은 머신에서 지원, 테스트 및 진단 시나리오에 사용할 수 있는 간단한 캡처 및 재생 기능(예: 명령줄 캡처 프로그램 **dxcap.exe**)을 제공합니다. 자세한 내용은 [명령줄 캡처 도구](command-line-capture-tool.md) 항목을 참조하세요.

## <a name="using-graphics-diagnostics-for-the-first-time"></a>처음으로 그래픽 진단 사용
 이제 필요한 모든 항목이 준비되었으므로 그래픽 진단을 사용할 수 있습니다. 다음 단계를 수행합니다.

### <a name="1---create-a-direct3d-app"></a>1 - Direct3D 앱 만들기
 그래픽 진단를 탐색 하는 데 고유한 Direct3D 앱이 이미 있는 경우 좋은 방법입니다! 그렇지 않으면 다음 중 하나를 사용 합니다.

- Windows 10 용 **directx 11 앱 (유니버설 windows)** 또는 **directx 12 앱 (유니버설 windows)** 프로젝트 템플릿
- Windows 10 용 [Direct3D 12 UAP 샘플](https://code.msdn.microsoft.com/Direct3D-12-UAP-Sample-ecb1779f)

  계속 진행하기 전에 앱을 빌드할 수 있는지 확인합니다.

### <a name="2---start-a-graphics-diagnostics-session"></a>2 - 그래픽 진단 세션 시작
 이제 첫 번째 그래픽 진단 세션을 시작할 준비가 되었습니다. Visual Studio의 주 메뉴에서 **디버그, 그래픽, 그래픽 디버깅 시작**을 선택 하거나 **alt + F5**를 누릅니다. 그러면 그래픽 진단 모드로 앱이 시작되고 Visual Studio에 진단 세션 창이 표시됩니다.

> [!IMPORTANT]
> Windows 10에서 앱을 실행 중인 경우 선택적 그래픽 도구 기능을 아직 설치하지 않았으면 지금 설치하라는 메시지가 표시됩니다. Windows 10에서 그래픽 진단을 사용하려면 먼저 설치해야 합니다.

### <a name="3---capture-frames"></a>3 - 프레임 캡처
 앱이 시작되는 즉시 프레임을 캡처할 수 있습니다.

#### <a name="to-capture-single-frames"></a>단일 프레임을 캡처하려면

- Visual Studio의 그래픽 도구 모음 또는 진단 세션 창에서 **프레임 캡처** 단추를 선택합니다. 또는 앱에 포커스가 있는 경우 키보드에서 **Print Screen** 키를 누르기만 하면 됩니다.

#### <a name="to-capture-a-sequence-of-frames"></a>프레임 시퀀스를 캡처하려면

- Visual Studio의 진단 세션 창에서 **캡처할 프레임 수**를 시퀀스로 캡처할 프레임 수로 설정한 다음, 위에서 설명한 단일 프레임 캡처 방법을 사용하여 시퀀스를 캡처합니다.

   단일 프레임을 다시 캡처하려면 **캡처할 프레임 수**를 *1*로 설정합니다.

  프레임 캡처를 완료하면 앱을 종료하거나 그래픽 도구 모음 또는 진단 세션 창에서 **중지** 단추를 선택하면 됩니다.

### <a name="4---examine-captured-frames-in-the-graphics-analyzer"></a>4 – Graphics Analyzer에서 캡처된 프레임 검사
 이제 방금 캡처한 프레임을 검사할 수 있습니다. 프레임 분석을 시작하려면 진단 세션 창에서 검사하려는 프레임의 프레임 번호를 선택합니다. 그러면 프레임이 **Graphics Analyzer**에 열립니다. 여기에서 그래픽 진단 도구를 사용하여 앱이 Direct3D를 사용하여 렌더링 문제를 추적하거나 **프레임 분석** 도구를 사용하여 성능을 파악하는 방법을 검사할 수 있습니다.

 진단 세션 창에서 잘못된 프레임을 선택했거나 다른 프레임을 검사하려는 경우 Graphics Analyzer에서 새 프레임을 선택할 수 있습니다. 그래픽 로그 창의 **렌더링 대상** 탭에 있는 렌더링 대상 이미지에서 **프레임 목록**을 확장한 다음, 검사할 다른 프레임을 선택합니다.

 Graphics Analyzer 도구를 함께 사용 하는 방법에 대 한 자세한 내용은 [예제](graphics-diagnostics-examples.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Direct3D 12 그래픽](/windows/desktop/direct3d12/direct3d-12-graphics)
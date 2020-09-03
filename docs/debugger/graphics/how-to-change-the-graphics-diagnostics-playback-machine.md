---
title: '방법: 그래픽 진단 재생 머신 변경 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f057e2e4f9d39fd3c5d985b3f0d19751d508614
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85769379"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>방법: 그래픽 진단 재생 머신 변경
로컬 머신을 사용하거나 원격 머신 또는 디바이스를 사용하여 그래픽 정보를 재생할 수 있습니다.

## <a name="choosing-a-playback-machine"></a>재생 머신 선택
 재생 머신은 그래픽 로그에서 그래픽 이벤트를 재생하는 데 사용되는 머신 또는 디바이스입니다. 일반적으로 로컬 머신은 가장 편리한 옵션이지만, 캡처된 머신과 다른 하드웨어 또는 드라이버 버전이 있는 머신에서는 렌더링 문제가 재현되지 않을 수 있습니다. 이 문제가 발생하면 문제를 더 잘 재현하는 원격 재생 머신을 선택하고 계속해서 개발 머신을 사용하여 문제를 진단할 수 있습니다.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>로컬 머신을 사용하여 그래픽 정보를 재생하려면

1. 그래픽 로그 문서 창에서 **재생 머신** 링크를 선택합니다. **원격 디버거 연결** 대화 상자가 나타납니다.

2. **수동 구성** 아래 **주소** 속성에 `localhost`을 입력합니다.

3. **인증 모드** 속성을 **없음**으로 설정합니다.

4. **선택** 단추를 선택합니다.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>원격 머신을 사용하여 그래픽 정보를 재생하려면

1. 그래픽 로그 문서 창에서 **재생 머신** 링크를 선택합니다. **원격 디버거 연결** 대화 상자가 나타납니다.

2. **수동 구성** 아래 **주소** 속성에 그래픽 정보를 재생하는 데 사용할 머신 또는 디바이스의 Windows 도메인 이름 또는 IP 주소를 입력합니다.

3. 재생 머신 연결을 보호하는 데 사용하려는 권한 부여 종류를 지정합니다.

    - Windows 인증의 경우 **인증 모드** 속성을 **Windows**로 설정합니다.

    - 인증이 없는 경우 **인증 모드** 속성을 **없음**으로 설정합니다.

4. **선택** 단추를 선택합니다.

> [!NOTE]
> **원격 디버거 연결** 대화 상자에는 개발 머신에 직접 연결되거나 동일한 서브넷에 있는 원격 디버깅 대상도 표시될 수 있습니다. 수동으로 구성하지 않고 해당 원격 디버깅 대상 중 하나를 그래픽 진단 재생 머신으로 사용할 수 있습니다. **원격 디버거 연결** 대화 상자에서 원하는 대상을 선택한 다음, **선택** 단추를 선택합니다.

## <a name="see-also"></a>참조
- [그래픽 로그 문서](graphics-log-document.md)
---
title: Visual Studio의 DirectX 12 지원 | Microsoft Docs
description: DirectX 12 사용자는 전체 그래픽 디버깅 환경을 위해 Windows의 PIX를 사용할 것을 권장함
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671419"
---
# <a name="directx-12-support-in-visual-studio"></a>Visual Studio의 DirectX 12 지원

## <a name="directx-12-support"></a>DirectX 12 지원

Visual Studio 그래픽 진단은 DirectX 12 게임을 지원하지 않습니다. DirectX 12를 완전히 지원하는 그래픽 디버깅을 위해서는 Visual Studio에서 ‘Windows의 PIX’를 사용하는 것이 좋습니다. 

Windows의 PIX는 원격 기능을 사용하는 성능 조정 및 디버깅 도구입니다. Windows의 PIX는 그래픽 디버깅 요구에 맞는 7가지 주요 기능을 제공합니다. GPU 캡처를 사용하여 Direct3D 12 그래픽 렌더링의 성능을 디버그하고 분석합니다. 타이밍 캡처를 사용하여 게임에서 수행하는 모든 CPU 및 GPU 작업의 성능과 스레딩을 파악합니다. 파일 IO 캡처를 사용하여 타이틀의 디스크 IO 패턴 및 패키지 레이아웃의 비효율성을 식별합니다.

[**Windows의 PIX**](https://aka.ms/PIXonWindows)를 사용한 그래픽 디버깅을 경험해 보세요.

[**Windows의 PIX를 다운로드** ](https://aka.ms/downloadPIX)하거나 [**설명서를 확인**하세요.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>Windows의 PIX

Windows의 PIX에는 7가지 주요 작업 모드가 있습니다.
1. **GPU 캡처**를 사용하여 Direct3D 12 그래픽 렌더링의 성능을 디버그하고 분석합니다.
2. **타이밍 캡처**를 사용하여 게임에서 수행하는 모든 CPU 및 GPU 작업의 성능과 스레딩을 파악하고 GPU 메모리 사용량을 추적합니다.
3. **함수 요약 캡처**는 각 함수의 실행이 지속되는 시간 및 각 함수가 호출되는 빈도에 대한 정보를 누적합니다.
4. **호출 그래프 캡처**는 단일 함수의 실행을 추적합니다.
5. **메모리 할당 캡처**는 게임에서 처리하는 메모리 할당에 대한 인사이트를 제공합니다.
6. **파일 IO 캡처**를 사용하여 타이틀의 디스크 IO 패턴 및 패키지 레이아웃의 비효율성을 식별합니다.
7. **시스템 모니터**는 게임을 실행하는 동안 실시간 카운터 데이터를 표시합니다.

Windows의 PIX에 대해 자세히 소개하는 동영상을 [**여기**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)에서 확인하세요.

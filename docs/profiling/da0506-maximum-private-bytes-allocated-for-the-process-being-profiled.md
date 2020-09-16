---
title: DA0506 - 프로파일링되고 있는 프로세스에 할당된 최대 전용 바이트 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a5447c21e3a1049bcb2cb86e3e0419e43fc4e953
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036810"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: 프로파일링되고 있는 프로세스에 할당된 최대 전용 바이트

|항목|값|
|-|-|
|규칙 ID|DA0506|
|범주|리소스 모니터링|
|프로파일링 방법|모두|
|메시지|이 정보는 참고용으로만 수집됩니다. Process Private Bytes 카운터는 프로파일링하고 있는 프로세스에 의해 할당된 가상 메모리를 측정합니다. 보고된 값은 모든 측정 간격에서 관찰되는 최대값입니다.|
|규칙 유형|정보|

 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.

## <a name="rule-description"></a>규칙 설명
 이 메시지는 프로세스가 현재 할당한 가상 메모리의 최대 크기(바이트)를 보고합니다(전용 바이트). 전용 바이트는 프로세스 내에서 실행되는 스레드만 액세스할 수 있는, 프로세스에 의해 할당된 가상 메모리 위치를 나타냅니다.

 32비트 컴퓨터에서 실행되는 32비트 프로세스의 경우 프로세스 중 전용 부분의 상한은 2GB입니다. 32비트 프로세스는 [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini 스위치를 사용해서 최대 3GB의 가상 메모리를 얻을 수 있습니다. 64비트 컴퓨터에서 실행되는 32비트 프로세스는 전용 가상 메모리를 4GB까지 확보할 수 있습니다.

 64비트 컴퓨터에서 실행되는 64비트 프로세스는 전용 가상 메모리를 8TB까지 확보할 수 있습니다.

 보고된 값은 프로파일링되는 프로세스가 활성 상태였던 모든 측정 간격에 대한 최대값입니다.

 프로세스 주소 공간에 대한 자세한 내용은 Windows 메모리 관리 설명서에서 [Virtual Address Space](/windows/win32/memory/virtual-address-space)(가상 주소 공간)를 참조하세요.

## <a name="how-to-use-rule-data"></a>규칙 데이터를 사용하는 방법
 보고된 값을 사용하여 프로그램의 여러 가지 버전이나 빌드에 대한 성능을 비교하거나 여러 가지 프로파일링 시나리오에서 애플리케이션의 성능을 파악합니다.

 프로세스 전용 바이트의 최대값이 프로세스 주소 공간의 최대 확장값을 구조적으로 제한한 크기에 근접할 경우 메모리 예외가 발생할 수 있습니다. 자세한 내용은 MSDN Magazine에서 [Investigating Memory Issues](/archive/msdn-magazine/2006/november/clr-inside-out-investigating-memory-issues)(메모리 문제 검사)를 참조하세요.
---
title: 계층 상호 작용 데이터 수집 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4f7b2a2bb5efd86d052247825a29a06c7f5ad109
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331592"
---
# <a name="collect-tier-interaction-data"></a>계층 상호 작용 데이터 수집

상호 작용 프로파일링은 ADO.NET 서비스를 통해 데이터베이스와 통신하는 다중 계층 애플리케이션의 함수 실행 시간에 대한 추가 정보를 제공합니다. 동기 함수 호출에 대해서만 데이터가 수집됩니다.

**Visual Studio 버전**

계층 상호 작용 프로파일링 데이터는 Visual Studio의 모든 버전을 사용하여 수집할 수 있습니다. 그러나 계층 상호 작용 프로파일링 데이터는 Visual Studio Enterprise에서만 볼 수 있습니다.

**Windows 8 및 Windows Server 2012**

Windows 8 데스크톱 앱 및 Windows Server 2012 앱에서 계층 상호 작용 데이터를 수집하려면 계측 방법을 사용해야 합니다. UWP 앱에 대한 계층 상호 작용 데이터는 수집할 수 없습니다. [Windows 8 및 Windows Server 2012 애플리케이션의 성능 도구](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)를 참조하세요. 지원되는 다른 Windows 버전의 모든 프로파일링 방법에 계층 상호 작용 데이터를 포함할 수 있습니다.

**성능 마법사**

성능 마법사의 버그 때문에 성능 탐색기에서 프로파일링 실행에 계층 상호 작용 데이터 수집 옵션을 추가해야 합니다. 또한 성능 탐색기의 대상 노드에 프로젝트, 실행 파일 또는 웹 사이트를 추가해야 합니다.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>성능 세션 속성 페이지를 사용하여 프로파일링 실행에 계층 상호 작용 데이터를 추가하려면

1. 성능 탐색기에서, 상황에 맞는 메뉴에서 **속성**을 선택합니다.

2. **계층 상호 작용** 페이지를 선택한 다음 **계층 상호 작용 프로파일링 사용** 확인란을 선택합니다.

3. 성능 탐색기에서, **대상** 노드를 선택한 다음 프로파일링하려는 프로젝트, 실행 파일 또는 웹 사이트를 지정합니다.

## <a name="see-also"></a>참고 항목

[계층 상호 작용 뷰](../profiling/tier-interactions-view.md)

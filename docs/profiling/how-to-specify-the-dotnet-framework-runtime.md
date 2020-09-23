---
title: .NET Framework 런타임 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 27846b448f7e0667004bd25d24bd447fe43f8e51
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851127"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>방법: .NET Framework 런타임 지정

.NET Framework 4 릴리스에서는 다양한 버전의 .NET Framework 런타임을 사용하여 빌드된 모듈로 애플리케이션을 구성할 수 있습니다. 기본적으로 Visual Studio 프로파일링 도구는 애플리케이션이 로드한 첫 번째 런타임을 프로파일링합니다. 프로파일러를 사용하여 애플리케이션을 시작할 때, 그리고 프로파일러를 이미 실행 중인 애플리케이션에 연결할 때 프로파일링할 런타임을 지정할 수 있습니다.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>프로파일러를 사용하여 애플리케이션을 시작할 때 프로파일링할 .NET Framework 런타임을 지정하려면

1. **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**, **고급**을 차례로 클릭합니다.

     **대상 CLR 버전** 목록 상자에는 **자동** 및 컴퓨터에 설치된 .NET Framework 런타임 버전이 표시됩니다.

2. 다음 단계 중 하나를 수행합니다.

    - 프로파일링할 CLR 버전을 클릭합니다.

    - **자동**을 클릭하여 애플리케이션이 로드한 첫 번째 버전을 프로파일링합니다.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>프로파일러를 애플리케이션에 연결할 때 프로파일링할 .NET Framework 런타임을 지정하려면

1. **분석** 메뉴에서 **프로파일러**를 가리키고 **연결/분리**를 클릭합니다.

2. **프로세스에 프로파일러 연결** 대화 상자에서 프로파일링할 프로세스를 클릭합니다.

     **대상 CLR 버전** 목록 상자에는 **자동** 및 컴퓨터에 설치된 .NET Framework 런타임 버전이 표시됩니다.

3. 다음 단계 중 하나를 수행합니다.

    - 프로파일링할 CLR 버전을 클릭합니다.

    - **자동**을 클릭하여 프로파일러가 애플리케이션에 연결될 때 로드된 버전을 프로파일링합니다.

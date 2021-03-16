---
title: DA0030 - 데이터베이스 프로젝트의 계층 상호 작용 측정값 수집 | Microsoft Docs
description: System.Data 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지하고 프로파일링 실행에서 상호 작용 데이터를 수집하지 않았습니다. 다시 프로파일링하고 계층 상호 작용 데이터를 추가해 보세요.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 44720e086fa0c9201fba319e445a44835faa9c2e
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465883"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: 데이터베이스 개체의 계층 상호 작용 측정값 수집

|항목|값|
|-|-|
|규칙 ID|DA0030|
|범주|프로파일링 도구 사용|
|프로파일링 방법|샘플링|
|메시지|다계층 애플리케이션의 상호 작용 측정값을 수집하면 데이터베이스 사용 패턴과 주요 데이터 액세스 지연을 파악하는 데 도움이 됩니다. 계층 상호 작용 프로파일링 옵션을 사용하면서 애플리케이션을 다시 프로파일링해 보세요.|
|규칙 유형|정보|

## <a name="cause"></a>원인
 <xref:System.Data> 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지하고 프로파일링 실행에서 상호 작용 데이터를 수집하지 않았습니다. 다시 프로파일링하고 계층 상호 작용 데이터를 추가해 보세요.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Data.Linq><xref:System.Data.Linq>를 포함하여 System.Data 네임스페이스에 있는 함수에서 많은 활동이 수행될 때마다 이 규칙이 실행됩니다.

 다계층 애플리케이션은 프레젠테이션 및 데이터 계층에 계층화된 서비스를 사용합니다. 일반적으로 데이터 계층은 Microsoft SQL Server 등의 데이터베이스 관리 시스템을 실행하는 별도의 프로세스입니다. 데이터 계층은 애플리케이션의 나머지 부분과는 다른 컴퓨터에서 실행될 수도 있습니다. 샘플링 프로필로는 Out-of-process 또는 원격 실행되는 함수와 서비스를 제대로 파악할 수 없습니다.

 프로파일링 도구는 ADO.NET 서비스에 대한 비동기 호출을 사용하여 Microsoft SQL Server 데이터 계층을 조작하는 다계층 애플리케이션에 대한 타이밍 정보를 수집할 수 있습니다. 계층 상호 작용 프로파일링을 명시적으로 사용하도록 설정해야 합니다. 기본적으로 켜지지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙은 참고용으로만 제공되며 정정 작업이 필요하지 않습니다.

 Visual Studio IDE에서 프로파일링 데이터에 계층 상호 작용 데이터를 추가하는 방법에 대한 자세한 내용은 [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)을 참조하세요. 명령줄에서 계층 상호 작용 데이터를 추가하는 방법에 대한 자세한 내용은 [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)을 참조하세요.

---
title: 'DA0030: 데이터베이스 프로젝트에 대한 계층 상호 작용 측정값 수집 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a4b140c1859d3a3a17eb2f48eb02a60a3e9d50c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152622"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: 데이터베이스 프로젝트의 계층 상호 작용 측정값 수집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

규칙 Id | DA0030 |  
| 범주 | 프로파일링 도구 사용 |  
| 프로 파일링 방법 | 샘플링 |  
| 메시지 | 다중 계층 응용 프로그램에 대 한 상호 작용 측정값을 수집 하면 데이터베이스 사용 패턴과 주요 데이터 액세스 지연을 이해 하는 데 도움이 됩니다. 계층 상호 작용 프로파일링 옵션을 사용하면서 애플리케이션을 다시 프로파일링해 보세요.|  
| 규칙 유형 | 정보 |  
  
## <a name="cause"></a>원인  
 <xref:System.Data> 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지하고 프로파일링 실행에서 상호 작용 데이터를 수집하지 않았습니다. 다시 프로파일링하고 계층 상호 작용 데이터를 추가해 보세요.  
  
## <a name="rule-description"></a>규칙 설명  
 <xref:System.Data.Linq><xref:System.Data.Linq>를 포함하여 System.Data 네임스페이스에 있는 함수에서 많은 활동이 수행될 때마다 이 규칙이 실행됩니다.  
  
 다계층 애플리케이션은 프레젠테이션 및 데이터 계층에 계층화된 서비스를 사용합니다. 일반적으로 데이터 계층은 Microsoft SQL Server 등의 데이터베이스 관리 시스템을 실행하는 별도의 프로세스입니다. 데이터 계층은 애플리케이션의 나머지 부분과는 다른 컴퓨터에서 실행될 수도 있습니다. 샘플링 프로필로는 Out-of-process 또는 원격 실행되는 함수와 서비스를 제대로 파악할 수 없습니다.  
  
 프로파일링 도구는 ADO.NET 서비스에 대한 비동기 호출을 사용하여 Microsoft SQL Server 데이터 계층을 조작하는 다계층 애플리케이션에 대한 타이밍 정보를 수집할 수 있습니다. 계층 상호 작용 프로파일링을 명시적으로 사용하도록 설정해야 합니다. 기본적으로 켜지지 않습니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 이 규칙은 참고용으로만 제공되며 정정 작업이 필요하지 않습니다.  
  
 Visual Studio IDE에서 프로파일링 데이터에 계층 상호 작용 데이터를 추가하는 방법에 대한 자세한 내용은 [계층 상호 작용 데이터 수집](../profiling/collecting-tier-interaction-data.md)을 참조하세요. 명령줄에서 계층 상호 작용 데이터를 추가하는 방법에 대한 자세한 내용은 [계층 상호 작용 데이터 수집](../profiling/adding-tier-interaction-data-from-the-command-line.md)을 참조하세요.

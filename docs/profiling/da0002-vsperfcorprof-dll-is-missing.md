---
title: DA0002 - VSPerfCorProf.dll 누락 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 36c9f3b33eab8428cd14aa26896c3813422d3dd7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537074"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll이 없습니다.

|항목|값|
|-|-|
|규칙 ID|DA0002|
|범주|프로파일링 도구 사용|
|프로파일링 방법|VSPerfCmd 및 VSPerfASPNETCmd 명령줄 도구를 사용하는 프로파일링|
|메시지|*VSPerfCLREnv.cmd*를 사용하여 환경 변수를 제대로 설정하지 않고 파일을 수집한 것 같습니다. 관리되는 이진에 대한 기호가 확인되지 않을 수 있습니다.|
|규칙 유형|정보|

## <a name="cause"></a>원인
 프로파일러는 프로파일링 실행 중 *VSPerfCorProf.dll*을 찾을 수 없습니다. 이 경고는 필요한 환경 변수를 초기화할 *VSPerfCLREnv.cmd* 도구를 사용하지 않고 프로파일러 데이터 컬렉션에 대한 명령줄 도구를 사용하는 경우에 발생합니다. 경고는 프로파일링 도구를 시작할 때 다른 프로파일러를 실행하는 경우 발생할 수도 있습니다.

## <a name="rule-description"></a>규칙 설명
 특정 환경 변수는 .NET Framework 이진 파일에서 기호를 확인하도록 프로파일러에 대한 프로파일링을 실행하기 전에 설정되어야 합니다. 이 경고는 프로파일링 데이터가 수집되기 전에 *VSPerfCLREnv.cmd* 도구가 실행되지 않았음을 제안합니다. 관리되는 이진에 대한 기호가 확인되지 않을 수 있습니다. 명령줄에서 프로파일링 도구 사용에 대한 자세한 내용은 [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)을 참조하세요.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구에서 명령줄 도구를 사용하여 관리되는 애플리케이션을 프로파일링할 때 데이터 수집을 시작하기 전에 [VSPerfCLREnv](../profiling/vsperfclrenv.md) 명령줄 도구를 시작합니다.

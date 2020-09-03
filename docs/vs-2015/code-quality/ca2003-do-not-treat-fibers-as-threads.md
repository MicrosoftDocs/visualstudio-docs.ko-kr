---
title: 'CA2003: 파이버를 스레드로 취급 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a8172490b267949686dd3390c85ed6d86531b192
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521176"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: 파이버를 스레드로 취급하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|범주|Microsoft.Reliability|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 관리 되는 스레드가 Win32 스레드로 처리 되 고 있습니다.

## <a name="rule-description"></a>규칙 설명
 관리 되는 스레드가 Win32 스레드 라고 가정 하지 마십시오. 파이버입니다. CLR (공용 언어 런타임)은 SQL에서 소유 하는 실제 스레드의 컨텍스트에서 파이버로 관리 되는 스레드를 실행 합니다. 이러한 스레드는 Appdomain 및 SQL Server 프로세스의 데이터베이스에서 공유할 수 있습니다. 관리 되는 스레드 로컬 저장소를 사용할 수 있지만 관리 되지 않는 스레드 로컬 저장소를 사용할 수 없거나 코드가 현재 OS 스레드에서 다시 실행 될 것으로 가정 합니다. 스레드의 로캘과 같은 설정을 변경 하지 마십시오. P/Invoke를 통해 CreateCriticalSection 또는 Createmutex가를 호출 하지 마세요. 잠금을 시작 하는 스레드 역시 잠금을 종료 해야 하기 때문입니다. 이는 파이버를 사용 하는 경우에는 발생 하지 않기 때문에 Win32 중요 섹션과 뮤텍스는 SQL에서 쓸모가 없습니다. 관리 되는 시스템 스레드 개체에서 대부분의 상태를 안전 하 게 사용할 수 있습니다. 여기에는 관리 되는 스레드 로컬 저장소 및 스레드의 현재 UI (사용자 인터페이스) 문화권이 포함 됩니다. 그러나 프로그래밍 모델의 이유로 SQL을 사용 하는 경우 스레드의 현재 문화권을 변경할 수 없습니다. 새 사용 권한을 통해 적용 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 스레드 사용을 검사 하 고 코드를 적절 하 게 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙을 억제 해서는 안 됩니다.

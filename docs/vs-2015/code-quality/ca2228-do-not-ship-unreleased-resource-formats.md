---
title: 'CA2228: 릴리스되지 않은 리소스 형식을 제공 하지 않습니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotShipUnreleasedResourceFormats
- CA2228
helpviewer_keywords:
- CA2228
- DoNotShipUnreleasedResourceFormats
ms.assetid: 2c614edc-4e94-4b4f-8067-eea677a75cd9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4adcae1c1cc616cdbcf5a7aa15342d221c2f4300
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540584"
---
# <a name="ca2228-do-not-ship-unreleased-resource-formats"></a>CA2228: 릴리스되지 않은 리소스 형식을 제공하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotShipUnreleasedResourceFormats|
|CheckId|CA2228|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 리소스 파일이 현재 지원 되지 않는 버전을 사용 하 여 빌드 되었습니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="rule-description"></a>규칙 설명
 의 시험판 버전을 사용 하 여 작성 된 리소스 파일은 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 지원 되는 버전의 .NET Framework에서 사용 하지 못할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 지원 되는 버전의 k를 사용 하 여 리소스를 빌드합니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

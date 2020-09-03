---
title: 코드 분석 체크 인 정책에 대 한 버전 호환성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609311"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>코드 분석 체크 인 정책에 대한 버전 호환성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다른 버전의를 사용 하 여 코드 분석 체크 인 정책을 평가 하 고 제작 해야 하는 경우에 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 는 체크 인 [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] 정책의 방법 및 평가의 차이점을 알아야 합니다 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] .

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>체크 인 정책 평가에 대 한 버전 호환성

- 에서 코드 분석 체크 인 정책을 평가 하는 경우에 존재 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 하지만에 존재 하지 않는 모든 규칙 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 은 무시 됩니다.

- 에서 코드 분석 체크 인 정책을 평가 하는 경우 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 에만 해당 하는 모든 새 규칙 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 은 무시 됩니다.

- 코드 분석 체크 인 정책에서 규칙 어셈블리를 지정 하는 경우는 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 인식 되지 않는 어셈블리로 지정 된 모든 규칙을 무시 합니다.

- 코드 분석 체크 인 정책에서 인식할 수 없는 규칙 어셈블리를 지정 하는 경우 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 메시지가 표시 됩니다.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>체크 인 정책 작성에 대 한 버전 호환성

- 버전을 사용 하 여 코드 분석 체크 인 정책을 만든 경우 버전을 사용 하 여 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 수정할 수 없습니다 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] . 또한 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 는 정책을 평가할 수 없습니다.

- 에서를 사용 하 여 코드 분석 체크 인 정책을 만든 경우 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 에서를 사용 하 여 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 수정할 수 있으며 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 정책을 통해이 정책을 평가할 수도 있습니다 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . 에서를 사용 하 여 정책을 수정한 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] 후 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 에는에서를 사용 하 여 더 이상 정책을 편집할 수 없습니다 [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 는 강력한 이름 불일치에 대 한 문제 없이 정책을 평가할 수 있습니다.

- 및 둘 다에 적용 되는 규칙 설정을 사용 하 여 코드 분석 체크 인 정책을 만들려면 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 에서 정책을 만들고 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] 필요한 사항을 모두 변경한 다음 정책을 저장 해야 합니다. 규칙에 대 한 변경 내용이에만 있는 경우에 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 는에서 정책을 수정 하 고 저장 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 합니다.

     에서 정책을 저장 한 후 [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] 에는에 있는 규칙에 대 한 설정을 더 이상 변경할 수 없습니다 [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] .

---
title: 자세한 로그 파일 지정 (ClickOnce 배포)
description: Clickonce 배포 설치, 초기화, 업데이트 및 제거를 위해 ClickOnce에서 유지 관리 되는 활동 로그의 자세한 정도를 지정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0da285cfef49bd495fbecf39131e49cacd0476a5
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350922"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>방법: ClickOnce 배포에 대한 자세한 로그 파일 지정
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 모든 배포에 대 한 활동 로그 파일을 유지 관리 합니다. 이러한 로그는 배포 설치, 초기화, 업데이트 및 제거와 관련 된 정보를 문서화 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다. 이러한 로그 파일에 기록 하는 세부 정보를 늘리려면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 레지스트리 편집기 ( *regedit.exe* )를 사용 하 여 자세한 정도를 지정 합니다.

> [!CAUTION]
> 레지스트리 편집기를 잘못 사용 하면 운영 체제를 다시 설치 해야 할 수 있는 심각한 문제가 발생할 수 있습니다. 레지스트리 편집기를 사용할 때는 특별히 주의해야 합니다.

 다음 절차에서는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 현재 사용자에 대 한 로그 파일의 자세한 정도 수준을 지정 하는 방법을 설명 합니다. 자세한 정도 수준을 줄이려면이 레지스트리 값을 제거 합니다.

### <a name="to-specify-verbose-log-files"></a>자세한 로그 파일을 지정 하려면

1. *Regedit.exe* 를 엽니다.

2. 노드 **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment** 로 이동 합니다.

3. 필요한 경우 라는 새 문자열 값을 만듭니다 `LogVerbosityLevel` .

4. `LogVerbosityLevel`값을로 설정 `1` 합니다.

## <a name="see-also"></a>참고 항목
- [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)
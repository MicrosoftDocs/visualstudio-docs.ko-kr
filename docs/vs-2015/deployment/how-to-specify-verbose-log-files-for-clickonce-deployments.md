---
title: '방법: ClickOnce 배포에 대 한 자세한 로그 파일 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843245"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>방법: ClickOnce 배포에 대한 자세한 로그 파일 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 모든 배포에 대 한 활동 로그 파일을 유지 관리 합니다. 이러한 로그는 배포 설치, 초기화, 업데이트 및 제거와 관련 된 정보를 문서화 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 합니다. 이러한 로그 파일에 기록 하는 세부 정보를 늘리려면 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 레지스트리 편집기 (**regedit.exe**)를 사용 하 여 자세한 정도를 지정 합니다.  
  
> [!CAUTION]
> 레지스트리 편집기를 잘못 사용 하면 운영 체제를 다시 설치 해야 할 수 있는 심각한 문제가 발생할 수 있습니다. 레지스트리 편집기를 사용할 때는 특별히 주의해야 합니다.  
  
 다음 절차에서는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 현재 사용자에 대 한 로그 파일의 자세한 정도 수준을 지정 하는 방법을 설명 합니다. 자세한 정도 수준을 줄이려면이 레지스트리 값을 제거 합니다.  
  
### <a name="to-specify-verbose-log-files"></a>자세한 로그 파일을 지정 하려면  
  
1. **Regedit.exe**를 엽니다.  
  
2. 노드로 이동 `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` 합니다.  
  
3. 필요한 경우 라는 새 문자열 값을 만듭니다 `LogVerbosityLevel` .  
  
4. `LogVerbosityLevel`값을로 설정 `1` 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 배포 문제 해결](../deployment/troubleshooting-clickonce-deployments.md)

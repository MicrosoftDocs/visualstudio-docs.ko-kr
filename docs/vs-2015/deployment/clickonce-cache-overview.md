---
title: ClickOnce 캐시 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployemtn
- ClickOnce applications, cache
- ClickOnce deployment, cache
ms.assetid: e379921e-9ef1-4326-bbf3-53ba67925526
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 58ea758ea10e2c58ff123a2bc991f14191db0aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151662"
---
# <a name="clickonce-cache-overview"></a>ClickOnce 캐시 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]로컬에서 설치 하거나 온라인으로 호스트 하 든 모든 응용 프로그램은 클라이언트 컴퓨터에 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 *캐시*에 저장 됩니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]캐시는 현재 사용자의 Documents And Settings 폴더에 있는 로컬 설정 디렉터리 아래의 숨겨진 디렉터리 패밀리입니다. 이 캐시에는 어셈블리, 구성 파일, 응용 프로그램 및 사용자 설정, 데이터 디렉터리를 비롯 한 모든 응용 프로그램 파일이 저장 됩니다. 캐시는 응용 프로그램의 데이터 디렉터리를 최신 버전으로 마이그레이션하는 역할도 담당 합니다. 데이터 마이그레이션에 대 한 자세한 내용은 [ClickOnce 응용 프로그램의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)를 참조 하세요.  
  
 응용 프로그램 저장소에 대해 단일 위치를 제공 하 여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 은 사용자 로부터 응용 프로그램의 실제 설치를 관리 하는 작업을 수행 합니다. 캐시는 또한 모든 응용 프로그램 및 해당 고유 버전의 어셈블리와 데이터 파일을 서로 분리 된 상태로 유지 하 여 응용 프로그램을 격리 하는 데 도움이 됩니다. 예를 들어 응용 프로그램을 업그레이드 하는 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 해당 버전 및 해당 데이터 리소스는 캐시에 고유한 디렉터리와 함께 제공 됩니다.  
  
## <a name="cache-storage-quota"></a>캐시 저장소 할당량  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 온라인으로 호스팅되는 응용 프로그램은 캐시 크기를 제한 하는 할당량에 의해 차지할 수 있는 공간의 크기에서 제한 됩니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . 캐시 크기는 모든 사용자의 온라인 응용 프로그램에 적용 됩니다. 부분적으로 신뢰할 수 있는 단일 온라인 응용 프로그램은 할당량 공간의 절반을 차지 하는 것으로 제한 됩니다. 설치 된 응용 프로그램은 캐시 크기에 의해 제한 되지 않으며 캐시 제한에도 영향을 주지 않습니다. 모든 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램의 경우 캐시는 현재 버전과 이전에 설치 된 버전만 유지 합니다.  
  
 기본적으로 클라이언트 컴퓨터는 온라인 응용 프로그램용 250 MB의 저장소를 포함 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 합니다. 데이터 파일은이 제한에 계산 되지 않습니다. 시스템 관리자는 캐시 크기 (kb)를 표현 하는 DWORD 값인 \Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment\OnlineAppQuotaInKB 레지스트리 키를 변경 하 여 특정 클라이언트 컴퓨터에서이 할당량 HKEY_CURRENT_USER을 확대 하거나 축소할 수 있습니다. 예를 들어 캐시 크기를 50 MB로 줄이기 위해이 값을 51200로 변경 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 애플리케이션의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)

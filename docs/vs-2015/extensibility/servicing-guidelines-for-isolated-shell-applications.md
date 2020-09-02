---
title: 격리 셸 응용 프로그램에 대 한 서비스 지침 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159276"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>격리 셸 애플리케이션에 대한 지침 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 격리 셸 응용 프로그램을 배포 하는 경우 응용 프로그램을 설치한 후에 응용 프로그램에 대 한 소프트웨어 업데이트를 제공할 수 있어야 합니다. 이렇게 하려면 Microsoft Installer (MSI) 파일을 사용 하 여 응용 프로그램을 설치 해야 합니다. 이러한 종류의 설치를 통해 Microsoft에서 제공 하는 소프트웨어 업데이트를 웹 다운로드에 의해 재배포 하 고 사용자 지정 개입 없이 고객이 사용 하도록 할 수 있습니다.  
  
## <a name="servicing-requirements"></a>서비스 요구 사항  
 설치 프로그램이 다음 세 가지 조건을 충족 하는지 확인 하 여 격리 된 셸 설치에서 업데이트를 허용할 수 있는지 확인할 수 있습니다.  
  
### <a name="redistribute-by-using-an-msi"></a>MSI를 사용 하 여 재배포  
 MSI는 제품 id를 유지 하 고 응용 프로그램에 클라이언트 컴퓨터의 실제 위치가 있는지 확인 하므로 MSI를 사용 하 여 응용 프로그램을 재배포 해야 합니다. 병합 모듈 (.msm 파일)은 이러한 보증을 제공 하지 않으므로 사용 하면 안 됩니다.  
  
### <a name="accounting-for-custom-actions"></a>사용자 지정 작업에 대 한 계정  
 사용자 지정 작업은 설치 관리자 프로그램의 비표준 설치 지시문입니다. 사용자 지정 작업은 파일 위치, 레지스트리 설정, 사용자 설정, 기타 설치 항목 등의 매개 변수를 변경 합니다. 사용자 지정 작업은 설치 시 데이터를 조작할 수 있습니다.  
  
 설치 프로그램에서 사용자 지정 작업을 사용 하는 경우 사용자가 응용 프로그램을 제거할 때 작업을 실행 취소할 수 있도록 모든 설치 시간 사용자 지정 작업에 해당 하는 사용자 지정 작업이 있어야 합니다. 설치 프로그램에서 해당 하는 제거 사용자 지정 작업을 제공 하지 못하면 응용 프로그램을 제거 하면 부분적으로 설치 된 상태로 유지 됩니다.  
  
- 특정 버전의 파일 또는 해시 값을 사용 하는 사용자 지정 작업은 소프트웨어 업데이트가 이러한 버전이 나 해시 값을 변경할 때 실패 합니다. 이 경우 사용자 지정 작업은 이러한 값을 수동으로 업데이트 해야 합니다. 제품 버전 간에 파일 또는 해시 값의 버전을 공유 하는 경우 추가 문제가 발생 합니다. 가능 하면 항상이 종속성을 피합니다.  
  
### <a name="accounting-for-shared-files"></a>공유 파일에 대 한 계정  
 공유 파일은 동일한 이름을 가지 며 여러 제품이 동일한 위치에 설치 됩니다. 이러한 제품은 버전, SKU (재고 보존 장치) 또는 둘 다에서 다를 수 있으며, 제품이 지정 된 컴퓨터에 공존할 수 있습니다. 그러나 공유 파일은 다음과 같은 여러 가지 이유로 서비스 문제를 만듭니다.  
  
- 한 응용 프로그램에 대 한 업데이트가 업데이트 되지 않은 두 번째 응용 프로그램에서 사용 하는 파일의 버전을 변경할 수 있으므로 공유 파일을 업데이트 하면 응용 프로그램 호환성 문제가 발생할 수 있습니다. 파일을 공유 하는 제품의 설치 관리자는 공유 파일에 대 한 참조를 계산 합니다. 따라서 제품을 제거 해도 설치 된 인스턴스 수가 감소 하는 것 이상으로 공유 파일에 영향을 주지 않습니다.  
  
- QFE (Quick Fix 엔지니어링) 설치 관리자는 파일 버전을 QFE 설치 관리자에서 서비스 하는 제품 버전으로 되돌립니다. 이 프로세스는 업데이트 된 공유 파일을 제공 하는 응용 프로그램을 중단 시킬 수 있습니다.

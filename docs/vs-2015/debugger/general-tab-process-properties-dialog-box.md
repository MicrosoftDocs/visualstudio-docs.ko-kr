---
title: 프로세스 속성 대화 상자, 일반 탭 Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9256ca4141e9e4ec9e5ae218f1e5a11bf2fa5362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182289"
---
# <a name="general-tab-process-properties-dialog-box"></a>프로세스 속성 대화 상자, 일반 탭
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**일반** 탭을 사용하여 특정 프로세스에 대한 자세한 정보를 확인할 수 있습니다. [프로세스 속성 대화 상자](../debugger/process-properties-dialog-box.md)를 표시하려면 포커스를 [프로세스 뷰](../debugger/processes-view.md) 창으로 이동합니다. 트리에서 프로세스 노드를 선택하고 **뷰** 메뉴에서 **속성**을 선택합니다.  
  
 **일반** 탭에서 사용할 수 있는 설정은 다음과 같습니다.  
  
|입력|설명|  
|-----------|-----------------|  
|**모듈 이름**|모듈의 이름입니다.|  
|**프로세스 ID**|이 프로세스의 고유 ID입니다. 프로세스 ID 번호는 재사용되므로 프로세스의 수명 동안만 해당 프로세스를 식별합니다. 프로세스 개체 형식은 프로그램이 실행될 때 만들어집니다. 프로세스의 모든 스레드는 동일한 주소 공간을 공유하고 동일한 데이터에 액세스합니다.|  
|**기본 우선 순위**|이 프로세스의 현재 기본 우선 순위입니다. 프로세스 내의 스레드는 해당 프로세스의 기본 우선 순위를 기준으로 자체 기본 우선 순위를 높일 수도 있고 낮출 수도 있습니다.|  
|**스레드**|이 프로세스에서 현재 활성 상태인 스레드 수입니다.|  
|**CPU 시간**|이 프로세스 및 해당 스레드에 걸린 총 CPU 시간입니다. 사용자 시간과 권한 있는 시간을 더한 시간과 같습니다.|  
|**사용자 시간**|유휴 상태가 아닌 스레드의 사용자 모드에서 이 프로세스의 스레드가 코드를 실행하는 데 소비한 누적 경과 시간입니다. 창 관리자, 그래픽 엔진 등 하위 시스템에서 하는 것처럼 애플리케이션이 사용자 모드로 실행됩니다.|  
|**권한 있는 시간**|유휴 상태가 아닌 스레드의 특권 모드에서 이 프로세스가 실행된 총 경과 시간입니다. 서비스 계층, 실행 루틴 및 커널은 특권 모드에서 실행됩니다. 그래픽 어댑터 및 프린터를 제외하고 대부분 디바이스의 드라이버도 특권 모드에서 실행됩니다. Windows에서 애플리케이션과 관련하여 수행하는 일부 작업은 Privileged Time뿐 아니라 다른 하위 시스템 프로세스에도 표시될 수 있습니다.|  
|**경과 시간**|이 프로세스가 실행되는 데 걸린 총 경과 시간입니다.|

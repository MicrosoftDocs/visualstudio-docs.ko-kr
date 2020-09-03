---
title: 참조(프로그래밍 방식 캡처) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cebeb7eb651c11b5f560b981df30213fc726c66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162255"
---
# <a name="reference-programmatic-capture"></a>참조(프로그램 방식 캡처)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 진단에서는 프로그래밍 방식 캡처 API를 통해 해당 캡처 기능을 프로그래밍 방식으로 제어할 수 있습니다. 이 API를 사용하면 메시지를 전환하여 그래픽 진단 HUD(헤드업 디스플레이)에 추가하고, 그래픽 로그 파일을 초기화하고 만들며, 그래픽 정보를 캡처할 수 있습니다.  
  
## <a name="programmatic-capture-apis"></a>프로그래밍 방식 캡처 API  
  
### <a name="classes"></a>클래스  
  
|이름|설명|  
|----------|-----------------|  
|[VsgDbg 클래스](../debugger/vsgdbg-class.md)|그래픽 진단의 앱 내 구성 요소를 프로그래밍 방식으로 제어하는 인터페이스를 나타냅니다.|  
  
### <a name="preprocessor-symbols"></a>전처리기 기호  
  
|이름|설명|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|그래픽 로그 파일이 사용자의 임시 파일 디렉터리에 저장되는지 여부를 존재로 정의합니다.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|그래픽 로그 파일의 기본 파일 이름을 정의합니다.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|`VsgDbg` 클래스의 기본 인스턴스가 제공되는지 여부를 존재로 정의합니다.|  
  
## <a name="related-articles"></a>관련 문서  
  
|제목|설명|  
|-----------|-----------------|  
|[Capturing Graphics Information](../debugger/capturing-graphics-information.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 그래픽 진단 도구를 사용하여 렌더링 문제를 진단할 수 있도록 DirectX 기반 앱에서 그래픽 정보를 캡처하는 방법을 보여 줍니다.|  
|[개요](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|그래픽 진단을 사용하여 DirectX 게임 및 앱의 렌더링 오류를 디버그하는 방법을 보여 줍니다.|

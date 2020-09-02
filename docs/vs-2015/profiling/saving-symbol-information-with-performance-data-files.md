---
title: 성능 데이터 파일을 사용하여 기호 정보 저장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9d2e8b0414746523d0f76e8266f6463d9c05574
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160293"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>성능 데이터 파일을 사용하여 기호 정보 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE(통합 개발 환경)를 사용하여 파일을 분석하는 경우 VSP 파일을 다른 컴퓨터로 이동하려면 보고서 파일에서 기호를 저장 또는 *serialize*하기 위한 성능 프로젝트 설정을 지정해야 합니다. 이렇게 하면 보고서 파일의 크기가 증가합니다. 기호를 serialize해야 하는 이유는 다음의 두 가지입니다.  
  
- 대상 어셈블리가 임시 스토리지의 해당 위치에서 손실되기 전에 성능 보고서에 코드 기호를 포함합니다.  
  
- 기호를 유지하여 성능 보고서를 프로파일링된 컴퓨터에서 이식할 수 있도록 하고, 다른 기호를 사용할 수 있는 다른 컴퓨터에서 분석을 위해 보고서를 여는 경우 같은 정보가 출력되도록 하기 위해  
  
  **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 또는 명령줄에서 기호를 serialize할 수 있습니다.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE에서 기호를 serialize하려면 메뉴 모음에서 **도구**를 가리키고 **옵션**을 클릭합니다. **옵션** 창에서 **성능 도구**를 선택한 다음 **자동으로 기호 정보 serialize** 확인란을 선택합니다.  
  
- PACKSYMBOLS는 보고서 파일을 저장할 때 사용할 수 있는 동일한 명령줄 옵션입니다. 기호를 serialize하려면 **vsperfreport /summary:all /packsymbols filename.vsp**를 입력합니다.  
  
## <a name="troubleshooting-symbol-problems"></a>기호 문제 해결  
 코드에 기호가 표시되지 않는 경우 몇 가지 일반적인 해결 방법을 사용할 수 있습니다.  
  
- 명령줄에서 vsperfreport /debugsympath를 실행하여 프로파일러 구성 요소가 기호 정보를 로드하는 위치의 전체 목록 및 사용되는 기호 파일이 프로젝트에서 사용 중인 파일과 일치하는지 여부를 표시합니다.  
  
- vsperfreport는 /PACKSYMBOLS 플래그를 포함하여 실행하거나 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE의 일반 성능 탐색기 옵션에서 기호 정보 serialize 옵션을 선택했는지 확인합니다.  
  
- 형식 데이터를 수집한 경우 vsperfreport 명령줄에 /SUMMARY:TYPE을 추가합니다.  
  
  Windows 또는 기타 Microsoft 프로그램에서 기호가 표시되지 않는 경우 다음을 수행합니다.  
  
- Windows 기호 캐시의 경로를 설정했는지 확인합니다. 기호 캐시 경로를 설정하려면 다음 중 하나를 수행합니다.  
  
  - [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE의 디버거->기호 옵션을 올바른 경로로 설정합니다.  
  
  - 기호를 포함하도록 VSPerfReport 명령줄의 -symbolpath 옵션을 추가합니다.  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]에서 기호가 표시되지 않으면 ASP 서버에 대해 기호 서버를 올바르게 설정했는지 확인합니다.  
  
## <a name="repacking-symbols"></a>기호 다시 압축  
 보고서에 기호를 다시 압축하려는 경우 VsPerfReport 명령줄 도구를 사용하면 됩니다. 다음 명령줄을 사용합니다.  
  
 VsPerfReport -clearpackedsymbols filename.vsp  
  
 VsPerfReport -packsymbols -summary:all filename.vsp  
  
## <a name="see-also"></a>관련 항목  
 [성능 도구 데이터 저장 및 내보내기](../profiling/saving-and-exporting-performance-tools-data.md)   
 [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)

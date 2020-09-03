---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 449c6c1ecdb0644b9b52b6ec12ce867dc34d66c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156096"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 로그 파일이 사용자의 임시 파일 디렉터리에 저장되는지 여부를 존재로 정의합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>값  
 존재 여부에 따라 그래픽 로그 파일이 사용자의 임시 파일 디렉터리에 저장되는지 여부를 결정하는 전처리기 기호입니다. 이 기호가 정의된 경우 `VSG_DEFAULT_RUN_FILENAME`에 정의된 파일 이름은 캡처된 앱의 현재 디렉터리에 상대적이거나 절대 경로입니다. 이 기호가 정의되지 않은 경우 `VSG_DEFAULT_RUN_FILENAME`에 정의된 파일 이름은 사용자의 임시 파일 디렉터리에 상대적이며 절대 경로일 수 없습니다.  
  
## <a name="remarks"></a>설명  
 사용자의 권한에 따라 그래픽 로그 파일을 임의 위치에 저장하지 못할 수 있습니다. 관리자가 선택하는 위치에 사용자가 쓸 수 있는지 여부가 확실하지 않은 경우에는 사용자의 임시 파일 디렉터리 또는 또 다른 알려진 유효한 위치에 그래픽 로그를 저장하도록 설정하는 것이 좋습니다.  
  
 그래픽 로그 파일이 임시 파일 디렉터리에 저장되지 않게 하려면 `vsgcapture.h`를 포함하기 전에 `DONT_SAVE_VSGLOG_TO_TEMP`를 정의해야 합니다.  
  
## <a name="example"></a>예제  
 이 예제에서는 호스트 머신의 절대 경로에 그래픽 로그 파일을 저장하는 방법을 보여 줍니다.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)

---
title: SccEnumChangedFiles 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 00ef98c93f02aa8e8a1b4ea53f1998d0ab6713a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200122"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

로컬 파일 목록이 지정 된 경우이 함수는 소스 코드 제어 데이터베이스의 해당 버전과 다른 파일을 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
SCCRTN SccEnumChangedFiles(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LONG    cFiles,  
   LPCSTR* lpFileNames,  
   LONG*   plIsFileDifferent  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pContext  
 진행 소스 제어 플러그 인 컨텍스트 포인터입니다.  
  
 hWnd  
 진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.  
  
 cFiles  
 진행 배열에 지정 된 파일 이름의 수 `lpFileNames` 입니다. 또한 배열의 크기를 지정 합니다 `plIsFileDifferent` .  
  
 lpFileNames 이름  
 진행 확인할 로컬 파일 이름 배열입니다.  
  
 plIsFileDifferent  
 [in, out] 각 파일의 차이점 상태를 나타내는 값의 배열입니다. 배열에는 최소한의 항목이 있어야 합니다 `cFiles` . 0이 아닌 값은 파일이 다른 것을 의미 합니다.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|작업이 완료되었습니다.|  
|SCC_UNSPECIFIEDERROR|일반 오류.|  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)

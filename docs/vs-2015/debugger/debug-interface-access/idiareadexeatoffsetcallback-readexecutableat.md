---
title: 'IDiaReadExeAtOffsetCallback:: ReadExecutableAt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ac5452437ab6fdec3eb68baf46aeeab8434df4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538865"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

실행 파일에서 지정 된 오프셋부터 시작 하 여 지정 된 바이트 수를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 fileOffset  
 진행 읽기를 시작할 실행 파일의 오프셋입니다.  
  
 cbData  
 진행 읽을 바이트 수입니다.  
  
 pcbData  
 제한이 읽은 바이트 수를 반환 합니다.  
  
 data[]  
 [in, out] 파일에서 읽은 바이트를 사용 하 여 채워진 배열입니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 절대 파일 오프셋을 사용 하 여 실행 파일에서 데이터 바이트를 로드 하기 위해 DIA 지원 코드에서 호출 됩니다. 이 메서드는 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드를 지원 하기 위해 호출 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

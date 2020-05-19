---
title: 클라이언트 블록 후크 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b7b0ef177922f09239c8925ced1ca013e966c0e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745713"
---
# <a name="client-block-hook-functions"></a>클라이언트 블록 후크 함수
적절한 함수를 작성하여 `_CLIENT_BLOCK` 블록에 저장되는 데이터 내용을 보고하거나 그 유효성을 검사할 수 있습니다. CRTDBG.H에 정의된 대로 다음과 같은 프로토타입을 가진 함수를 작성해야 합니다.

```cpp
void YourClientDump(void *, size_t)
```

 즉 후크 함수는 할당 블록 처음 부분을 가리키는 **void** 포인터와 할당 크기를 나타내는 **size_t** 형식 값을 허용하고 `void`를 반환해야 합니다. 그 외에도 원하는 내용을 추가할 수 있습니다.

 [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)를 사용하여 후크 함수를 설치한 경우 `_CLIENT_BLOCK` 블록을 덤프할 때마다 이 함수를 호출합니다. 그런 다음, [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)을 사용하여 덤프한 블록의 형식이나 하위 형식에 대한 정보를 얻을 수 있습니다.

 `_CrtSetDumpClient`에 전달한 함수에 대한 포인터는 CRTDBG.H에 정의된 대로 **_CRT_DUMP_CLIENT** 형식입니다.

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>참조

- [디버그 후크 함수 작성](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 샘플](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)
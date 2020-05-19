---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40f3c3c22de6b4b0ebdbdf2dfc953f4cb1c9b5e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736087"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
그래픽 로그 파일이 사용자의 임시 파일 디렉터리에 저장되는지 여부를 존재로 정의합니다.

## <a name="syntax"></a>구문

```C++
#define DONT_SAVE_VSGLOG_TO_TEMP
```

## <a name="value"></a>값
 존재 여부에 따라 그래픽 로그 파일이 사용자의 임시 파일 디렉터리에 저장되는지 여부를 결정하는 전처리기 기호입니다. 이 기호가 정의된 경우 `VSG_DEFAULT_RUN_FILENAME`에 정의된 파일 이름은 캡처된 앱의 현재 디렉터리에 상대적이거나 절대 경로입니다. 이 기호가 정의되지 않은 경우 `VSG_DEFAULT_RUN_FILENAME`에 정의된 파일 이름은 사용자의 임시 파일 디렉터리에 상대적이며 절대 경로일 수 없습니다.

## <a name="remarks"></a>설명
 사용자의 권한에 따라 그래픽 로그 파일을 임의 위치에 저장하지 못할 수 있습니다. 관리자가 선택하는 위치에 사용자가 쓸 수 있는지 여부가 확실하지 않은 경우에는 사용자의 임시 파일 디렉터리 또는 또 다른 알려진 유효한 위치에 그래픽 로그를 저장하도록 설정하는 것이 좋습니다.

 그래픽 로그 파일이 임시 파일 디렉터리에 저장되지 않게 하려면 `vsgcapture.h`를 포함하기 전에 `DONT_SAVE_VSGLOG_TO_TEMP`를 정의해야 합니다.

## <a name="example"></a>예제
 이 예제에서는 호스트 머신의 절대 경로에 그래픽 로그 파일을 저장하는 방법을 보여 줍니다.

```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h
#define DONT_SAVE_VSGLOG_TO_TEMP
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"

#include <vsgcapture.h>
```

## <a name="see-also"></a>참조
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)

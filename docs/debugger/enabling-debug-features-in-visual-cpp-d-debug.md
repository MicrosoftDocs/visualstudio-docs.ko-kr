---
title: C++ 프로젝트에서 디버그 기능 사용(-D_DEBUG) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 19d341cba47e0a3d2259cc57d239c63420095347
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737951"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>C++ 프로젝트에서 디버그 기능 사용(/D_DEBUG)
[!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)]에서 **_DEBUG** 기호를 정의하고 프로그램을 컴파일하면 어설션과 같은 디버깅 기능을 사용할 수 있습니다. **_DEBUG**는 다음 두 가지 방법 중 하나를 통해 정의할 수 있습니다.

- 소스 코드에서 **#define _DEBUG**를 지정하거나

- **/D_DEBUG** 컴파일러 옵션을 지정합니다. (Visual Studio에서 마법사를 사용하여 프로젝트를 만드는 경우 **/D_DEBUG**는 디버그 구성에 자동으로 정의됩니다.)

  **/D_DEBUG**가 정의되면 컴파일러가 **#ifdef _DEBUG** 기호와 `#endif` 기호 사이의 코드 섹션을 컴파일합니다.

  MFC 프로그램의 디버그 구성은 MFC 라이브러리의 디버그 버전과 링크해야 합니다. **_DEBUG** 및 **_UNICODE**와 같이 정의한 기호에 따라 MFC 헤더 파일에서 링크할 MFC 라이브러리 버전이 결정됩니다. 자세한 내용은 [MFC 라이브러리 버전](/cpp/mfc/mfc-library-versions)을 참조하세요.

## <a name="see-also"></a>참조
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)
- [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)
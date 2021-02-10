---
title: Visual C/C++ 사용자 지정 시각화 도우미 호환성
description: Visual Studio 2019의 새로운 기능은 레거시 C/C++ 식 계산기 추가 기능 및 사용자 지정 시각화 도우미와 호환되지 않을 수 있습니다. 자세한 내용은 이 문서를 참조하세요.
ms.custom: SEO-VS-2020
ms.date: 01/28/2019
ms.prod: visual-studio-dev16
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging assertions
- assertions, debugging
- assertions, assertion failures
- Assertion Failed dialog box
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.openlocfilehash: 32ad6b4b699f9cfe02739f341a4f9ddf29360f37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884314"
---
# <a name="visual-cc-custom-visualizer-compatibility"></a>Visual C/C++ 사용자 지정 시각화 도우미 호환성

Visual Studio 2019부터 C++에는 메모리를 많이 사용하는 구성 요소를 호스트하는 데 외부 64비트 프로세스를 사용하는 향상된 디버거가 포함되어 있습니다. 이 업데이트의 일부로, C/C++ 식 계산기에 대한 특정 확장을 새 디버거와 호환되도록 업데이트해야 합니다.

현재 레거시 C/C++ EE 추가 기능 또는 C/C++ 사용자 지정 시각화 도우미를 사용 중인 경우 **도구** > **옵션** > **디버깅** 으로 이동한 후 **외부 프로세스에 디버그 기호 로드(네이티브 전용)** 를 선택 취소하여 해당 외부 프로세스의 사용을 해제할 수 있습니다. 이 옵션의 선택을 취소하면 IDE(devenv.exe) 프로세스 내의 메모리 사용량이 크게 증가합니다. 따라서 대규모 프로젝트를 디버그할 것으로 예상되는 경우 확장의 소유자와 협력하여 이 디버깅 옵션과 호환되도록 하는 것이 좋습니다.

레거시 C/C++ EE 추가 기능 또는 C/C++ 사용자 지정 시각화 도우미의 소유자인 경우 작업자 프로세스에서 확장 로드를 옵트인하는 방법에 관해 [Concord 확장성 샘플 위키](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Worker-Process-Remoting)에서 자세히 알아볼 수 있습니다. [C/C++ 사용자 지정 시각화 도우미 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/tree/master/CppCustomVisualizer)도 찾을 수 있습니다.
---
title: 동기화 네임스페이스 및 폴더 이름
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 네임스페이스와 폴더 이름을 동기화하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 10dff5d9129d1a91f01ef7541397d86f5a71468c
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479812"
---
# <a name="sync-namespace-and-folder-name"></a>동기화 네임스페이스 및 폴더 이름

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 네임스페이스 및 폴더 이름 동기화

**시기:** 파일을 새 폴더로 끌어 솔루션 파트의 아키텍처를 변경하려는 경우 

**이유:** 새 폴더 구조를 사용하여 네임스페이스를 최신 상태로 유지하려고 합니다.

## <a name="how-to"></a>방법

1. 네임스페이스 이름에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. **네임스페이스를 \<folder name>(으)로 변경** 을 선택합니다.

   ![네임스페이스 및 폴더 이름 동기화](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)

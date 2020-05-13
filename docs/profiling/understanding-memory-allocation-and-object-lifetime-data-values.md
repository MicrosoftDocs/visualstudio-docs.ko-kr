---
title: 메모리 할당 및 개체 수명 데이터 값 이해
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools, .NET memory method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6eec0c4bc5fc27e07bc04a8445ca14ce538ac376
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780002"
---
# <a name="understand-memory-allocation-and-object-lifetime-data-values"></a>메모리 할당 및 개체 수명 데이터 값 이해

*프로파일링 도구의*.NET 메모리 할당[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 방법은 할당에서 생성되었거나 가비지 수집에서 삭제된 개체 크기 및 수에 대한 정보를 수집하고 이벤트가 발생할 때 함수 *호출 스택*에 대한 추가 정보를 수집합니다. *호출 스택*은 프로세서에서 실행되는 함수에 대한 정보를 저장하는 동적 구조체입니다.

메모리 프로파일러는 프로파일링된 애플리케이션에서 .NET Framework 개체를 할당할 때마다 컴퓨터 프로세서를 중단시킵니다. 개체 수명 데이터도 수집되는 경우 프로파일러는 각 .NET Framework 가비지 수집 후에 프로세서를 중단합니다. 데이터는 프로파일링된 각 함수와 각 개체 유형에 대해 집계됩니다.

## <a name="allocation-data"></a>할당 데이터

메모리 이벤트가 발생하면 할당되거나 삭제된 메모리 개체의 총 개수와 크기가 증가합니다.

메모리 할당 이벤트가 발생하면 프로파일러는 호출 스택에서 각 함수의 샘플 개수를 증가시킵니다. 데이터를 수집할 때는 호출 스택에서 하나의 함수만이 함수 본문의 코드를 실행하고 있는 상태입니다. 스택의 다른 함수는 반환하기 위해 호출한 함수가 반환되기를 대기 중인 함수 호출 계층의 부모입니다.

- 할당 이벤트의 경우 프로파일러는 현재 명령을 실행 중인 함수의 *전용* 샘플 개수를 증가시킵니다. 전용 샘플은 함수의 전체(*포괄*) 샘플에도 포함되므로 현재 활성 상태인 함수의 포괄 샘플 개수도 증가합니다.

- 프로파일러는 호출 스택에 있는 다른 모든 함수의 포괄 샘플 개수를 증가시킵니다.

## <a name="lifetime-data"></a>수명 데이터

.NET Framework의 가비지 수집기는 애플리케이션의 메모리 할당 및 해제를 관리합니다. 가비지 수집기의 성능을 최적화하기 위해 관리되는 힙은 0세대, 1세대 및 2세대의 3개 세대로 나뉩니다. 런타임 가비지 수집기는 0세대에서 새 개체를 저장합니다. 수집이 완료된 후에 남아 있는 개체는 승격되어 1세대 및 2세대에 저장됩니다.

가비지 수집기는 전체 개체 세대의 할당을 취소하여 메모리를 회수합니다. 프로파일링된 애플리케이션이 만든 개체의 경우 개체 수명 뷰에는 개체의 수/크기와 해당 개체가 회수된 세대가 표시됩니다.

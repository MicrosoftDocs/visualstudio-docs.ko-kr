---
title: Workflow Designer에서 지원되지 않는 디버깅 시나리오
description: 워크플로 디자이너에서 지원 되지 않는 디버깅 시나리오에 대해 알아봅니다. 예를 들어 "코드를 편집한 후에는 실행을 계속할 수 없습니다."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: d9ce8d15e44fecca673fdaa9fccd70ff13eb6783
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433520"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Workflow Designer에서 지원되지 않는 디버깅 시나리오

워크플로 디자이너는 다음과 같은 디버깅 시나리오를 지원 하지 않습니다.

- 코드를 편집한 후에는 실행을 계속할 수 없습니다.

- 워크플로의 임의의 지점에서 실행을 계속할 수 없습니다(다음 설정).

- 커서에 도달할 때까지 실행을 계속할 수 없습니다(커서까지 실행).

- Workflow Designer를 사용하지 않고 코드로 만든 워크플로는 Workflow Designer를 사용하여 디버깅할 수 없습니다.

- 이전 버전의 WF (Windows Workflow Foundation)에서 만든 워크플로는 .NET Framework 4 이상에서 디버그할 수 없습니다.

- 활동 또는 <xref:System.Activities.Statements.Flowchart> 노드 간 링크에는 중단점을 정의할 수 없습니다.

- 디버깅하는 동안에는 클립보드를 사용할 수 없습니다.

- 활동을 복사하거나 붙여 넣으면 중단점이 유지되지 않습니다.

- 호출 스택 창에서는 워크플로 중단점을 설정할 수 없습니다.

- 디자이너에서 중단점을 만들 때 **새 중단점** 대화 상자의 **줄** 및 **문자** 설정은 사용 되지 않습니다.

- 중단점 창 또는 바로 가기 메뉴에서는 워크플로 디버깅에 다음과 같은 열 또는 옵션을 사용할 수 없습니다.

  - 조건

  - 적중 횟수

  - 적중될 때

  - 함수

  - 데이터

  - 프로세스

  - 디스어셈블리로 이동

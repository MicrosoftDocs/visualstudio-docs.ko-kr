---
title: Visual Studio에서 소스 제어를 용이하게 만드는 방법
titleSuffix: ''
description: Visual Studio에서 Git 및 GitHub를 사용하여 코드의 변경 내용을 추적하고 필요한 경우 이를 되돌리는 방법을 알아봅니다.
ms.date: 04/01/2021
ms.topic: conceptual
ms.author: tglee
author: TerryGLee
ms.manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: 6e4bed3201a48975e9da266794f085f78be6d68c
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215580"
---
# <a name="how-visual-studio-makes-source-control-easy"></a>Visual Studio에서 소스 제어를 용이하게 만드는 방법

이전에 작업하던 코드 버전으로 돌아가고 싶다고 생각한 적이 있나요? 코드 복사본을 백업으로 다른 위치에 수동으로 저장한 적이 있나요? 소스 제어를 사용하면 시간이 지나면서 코드에서 변경한 내용을 추적할 수 있으므로 진행 상황을 추적하고 특정 버전으로 되돌릴 수 있습니다. Visual Studio에서는 가장 많이 사용되는 최신 버전 제어 시스템인 Git을 쉽게 사용할 수 있습니다.

## <a name="a-great-place-to-start-with-git--github"></a>Git 및 GitHub에서 시작하는 데 적합한 위치

GitHub는 코드를 저장하고 디바이스와 관계없이 어디서나 액세스할 수 있는 안전한 클라우드 코드 스토리지를 별도의 비용 없이 제공합니다. Visual Studio에는 소스 제어를 사용하여 쉽게 코드를 관리하고 다른 사용자와 협업할 수 있도록 하는 최고 수준의 Git 및 GitHub 기능이 제공됩니다. 먼저 다음 **Git 리포지토리 만들기** 대화 상자를 사용하여 Git 및 GitHub에 코드를 추가합니다. 이렇게 하려면 메뉴 모음에서 **Git** > **Git 리포지토리 만들기** 를 선택합니다.

:::image type="content" source="media/git-source-control-create-repository.png" alt-text="Visual Studio의 Git 리포지토리 만들기 대화 상자.":::

GitHub를 사용하여 많은 오픈 소스 리포지토리를 탐색하고 학습할 수도 있습니다. Visual Studio를 사용하면 기존 GitHub 리포지토리를 쉽게 복제하고 찾아볼 수 있으므로 뛰어난 학습 환경입니다.

## <a name="streamlined-and-intuitive-inner-loop-git-experience"></a>간소화되고 직관적인 내부 루프 Git 환경

Visual Studio는 일상적인 워크플로(내부 루프)의 생산성 최대화에 중점을 둔, 검색 가능하고 직관적인 Git 기능을 제공합니다. 변경 내용을 커밋하기 위해 더 이상 코드에서 벗어날 필요가 없습니다. 이러한 기능으로는 최상위 Git 메뉴, Git 변경 내용 창, Git에 포커스가 있는 상태 표시줄 등이 있습니다. Git은 전체적인 환경으로 Visual Studio와 통합됩니다. 예를 들어 솔루션 탐색기와 코드 편집기에 모두 최고 수준의 Git 통합이 포함됩니다.

:::image type="content" source="media/git-source-control-inner-loop.png" alt-text="Git 메뉴와 솔루션 탐색기의 Git 변경 내용 탭이 표시된 Visual Studio IDE":::

## <a name="first-class-repository-management--collaboration"></a>최고 수준의 리포지토리 관리 및 협업

Visual Studio에는 강력한 리포지토리 검색 및 협업 기능이 포함되어 다른 도구를 사용할 필요가 없습니다. 들어오고 나가는 커밋, 분기 미리 보기 및 커밋 비교를 계속 확인하여 리포지토리를 최신 상태로 유지합니다. 또한 분기를 관리하고 커밋을 제거 및 cherry-pick하여 리포지토리를 관리합니다.

:::image type="content" source="media/git-source-control-repository-management.png" alt-text="Git 메뉴와 솔루션 탐색기의 Git 변경 내용 탭이 강조 표시된 Visual Studio IDE":::

## <a name="interactive--smart-git-functionality"></a>대화형 및 스마트 Git 기능

Visual Studio의 Git 통합은 상황별 지원을 제공하고 적절한 작업을 수행하라는 메시지를 표시하여 신뢰와 자신감이 향상됩니다. 또한 단어 차이를 표시하거나 숨기고 충돌과 차이점을 탐색할 수 있는 충돌 해결 환경이 포함되어 있습니다.

:::image type="content" source="media/git-source-control-interactive-functionality.png" alt-text="Git 상황별 지원 및 충돌 해결을 보여 주는 Visual Studio IDE":::

## <a name="next-steps"></a>다음 단계

Visual Studio에서 Git 및 GitHub 사용에 대해 자세히 알아보려면 YouTube 동영상 [Getting started with Git in Visual Studio](https://www.youtube.com/watch?v=GCZ9x3yqkyc&list=PLReL099Y5nRc-zbaFbf0aNcIamBQujOxP)(Visual Studio에서 Git 시작)를 시청하세요.

## <a name="see-also"></a>참조

- [Visual Studio에서 Git 및 GitHub 시작](/learn/modules/visual-studio-github-push/)
- [Visual Studio의 새로운 Git 환경](git-with-visual-studio.md)
- [Git와 팀 탐색기 나란히 비교](git-team-explorer-feature-comparison.md)
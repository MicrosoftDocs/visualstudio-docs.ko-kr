---
title: GitHub Codespaces 개요(미리 보기)
description: Visual Studio를 사용한 GitHub Codespaces에 관한 정보와 이 서비스가 개발 환경을 클라우드로 확장하는 데 어떻게 도움이 되는지 자세히 알아봅니다.
ms.topic: overview
ms.date: 09/04/2020
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 629ad64ad2a179e1f70998240f26a4484280e514
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005015"
---
# <a name="what-is-github-codespaces-preview"></a>GitHub Codespaces란? (미리 보기)

Codespaces를 소개해 드리겠습니다.

GitHub Codespaces는 장기 프로젝트이든, 단기 작업(예: 끌어오기 요청 검토)이든 관계없이 모든 활동을 지원하는 클라우드 기반 개발 환경입니다. Visual Studio 2019 미리 보기 내에서 codespace를 사용할 수 있습니다([제한된 퍼블릭 베타에 등록](https://github.com/features/codespaces/signup-vs)).

또한 GitHub Codespaces는 일반적으로 개발 환경에 대한 반복성 및 안정성(프로덕션 워크로드용으로 예약됨) 같은 DevOps의 많은 이점을 제공합니다. 선호하여 사용 중인 도구, 프로세스, 구성도 함께 사용하도록 GitHub Codespaces를 개인 설정할 수도 있습니다.

이 문서에서는 주요 개념을 설명하고 Codespaces 기능을 소개합니다. 시작하려는 경우 [codespace와 함께 Visual Studio 사용](use-visual-studio-with-codespaces.md)을 참조하세요.

> [!IMPORTANT]
> GitHub Codespaces를 사용하려면 제한된 [퍼블릭 베타](https://github.com/features/codespaces/signup-vs)에 등록해야 합니다. 베타 기간에 GitHub는 Codespaces의 가용성에 관한 어떠한 보증도 하지 않습니다. 베타에 참가하는 방법에 대한 자세한 내용은 [Codespaces 정보](https://docs.github.com/github/developing-online-with-codespaces/about-codespaces#joining-the-beta)를 참조하세요.

## <a name="concepts-and-features"></a>개념 및 기능

GitHub Codespaces 기능은 몇 가지 기본 개념에 기반하여 빌드됩니다. 이 섹션에서는 기본 개념을 설명하고 기능을 간략히 살펴봅니다.

### <a name="remote-development"></a>원격 개발

오늘날 대부분 개발자는 특정 개발 및 런타임 스택으로 구성된 원격 설정 또는 VM에서 코딩을 시도합니다. 이렇게 하는 이유는 개발 환경을 로컬에서 설정하는 것이 너무 어렵고 지나친 중단을 초래하며 경우에 따라 거의 불가능하기 때문입니다. 또한 개인은 일상 업무에 필요한 머신에 “장애를 일으킬” 걱정 없이 신기술이나 새 프레임워크를 사용해 보기를 원합니다.

원격 환경과 원격 지원 도구를 사용하면 개발자의 역량이 강화되지만 대개 머신 관리의 오버헤드가 발생합니다. 환경 구성으로 인해 종종 온보딩 및 컨텍스트 전환이 복잡해집니다. GitHub Codespaces는 많은 환경이 동시에 존재할 수 있도록 하여 신속한 온보딩과 컨텍스트 전환을 방해하는 요소를 제거합니다. 

GitHub Codespaces는 환경 설정이 아닌 생산성에 집중할 수 있는 관리형 솔루션을 제공합니다. GitHub Codespaces는 원격 개발을 지원하기 위해 개념적, 기술적으로 Visual Studio 2019를 확장합니다. 

### <a name="about-codespaces"></a>codespace 정보

codespace는 GitHub Codespaces의 “백 엔드” 절반입니다. 여기에서 소프트웨어 개발과 관련된 모든 컴퓨팅(컴파일, 디버깅, 복원 등)이 발생합니다. codespace를 만들면 작업을 완료하거나, PR을 검토하거나, 새 프로젝트를 시작하는 데 필요한 모든 것이 준비됩니다. codespace는 런타임, 컴파일러, 디버거, 편집기, 사용자 지정 dot 파일 구성, 프로젝트에서 작업하는 데 필요한 소스 코드를 구성합니다.

클라우드 호스팅 codespace에는 다음과 같은 이점이 있습니다.

- 신속하게 만들고 삭제할 수 있습니다. 필요한 만큼(계정 한도까지) 만든 다음에 작업 완료 시 삭제하면 됩니다.
- 관리형이므로 직접 수행해야 하는 전체 유지 관리 작업이 줄어듭니다.
- 예측 가능한 가격이 책정되며 사용한 만큼만 요금을 부담하면 됩니다. 그리고 자동 일시 중단 기능이 기본 제공되어 런어웨이 비용을 없앨 수 있습니다.
- 컴퓨팅 리소스를 절약할 수 있습니다. 개발 워크로드를 클라우드로 이동하면 개인 머신에서 제한된 리소스를 자유롭게 사용할 수 있습니다.

## <a name="custom-configuration"></a>사용자 지정 구성

GitHub Codespaces는 가장 광범위한 프로젝트 또는 작업을 수용하도록 빌드됩니다. 일반적인 기본값을 제공하는 스마트 구성 기능을 시작하거나 [사용자 지정 구성](customize-codespaces.md)을 사용하여 codespace를 미세 조정할 수 있습니다.

개발자는 유연한 구성을 통해 로컬 머신에 적용하기 어려운 고유한 구성 및 요구 사항을 사용하여 프로젝트에 신속하게 온보딩할 수 있습니다. 또한 재현 가능한 codespace는 “일부 머신에서만 작동하는” 문제를 제거합니다.

## <a name="personal-configuration"></a>개인 구성

기본 설정을 유지하는 것이 클라우드 호스팅 codespace에서 개발하는 작업을 친숙하고 자연스럽게 느끼게 한다는 것을 알고 있습니다. GitHub Codespaces는 codespace 구성을 기반으로 개별화된 사용자 지정을 계층화합니다. 편집기 및 터미널의 개인 기본 설정 및 구성은 GitHub Codespaces에서 지원됩니다.

codespace는 [사용자 지정 dot 파일](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account)(예: `.bashrc`, `.gitconfig` 등)의 사용자별 컬렉션을 사용하여 만들 수 있으며, GitHub Codespaces는 Git ID, 테마 및 설정을 자동으로 동기화하므로 사용자가 만드는 모든 codespace는 프로젝트별 환경 기능과 관계없이 원하는 모양과 느낌을 제공합니다.

## <a name="see-also"></a>추가 정보

* [codespace와 함께 Visual Studio를 사용하는 방법](use-visual-studio-with-codespaces.md)
* [codespace를 사용자 지정하는 방법](customize-codespaces.md)
* [지원되는 Visual Studio 기능](supported-features-codespaces.md)

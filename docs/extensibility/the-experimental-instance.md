---
title: 실험 인스턴스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699034"
---
# <a name="the-experimental-instance"></a>실험적 인스턴스
Visual Studio 개발 환경을 변경할 수 있는 테스트되지 않은 응용 프로그램에서 보호하기 위해 VSSDK는 실험에 사용할 수 있는 실험 공간을 제공합니다. 평소와 같이 Visual Studio를 사용하여 새 응용 프로그램을 개발하지만 이 실험 인스턴스를 사용하여 응용 프로그램을 실행합니다.

 VSIX 패키지가 있는 모든 응용 프로그램은 디버그 모드에서 Visual Studio 실험 인스턴스를 시작합니다.

 특정 솔루션 외부에서 Visual Studio의 실험 인스턴스를 시작하려면 명령 창에서 다음 명령을 실행합니다.

 "*\<비주얼 스튜디오 설치 경로>* \Common7\IDE\devenv.exe" /RootSuffix Exp

> [!NOTE]
> 실험 인스턴스는 및 `<version number>Exp` `<version number>Exp_Config` 노드 아래의 레지스트리에 기록됩니다. 예를 들어 Visual Studio 2015 실험 레지스트리 영역은
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` 및 `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 확장 프로그램을 개발하는 동안 실험 인스턴스에서 확장을 실행하는 것이 좋습니다. 확장을 배포하면 개발 인스턴스에서 실행됩니다. 응용 프로그램 등록에 대한 자세한 내용은 [VSPackage 등록을](../extensibility/internals/registering-vspackages.md)참조하십시오.

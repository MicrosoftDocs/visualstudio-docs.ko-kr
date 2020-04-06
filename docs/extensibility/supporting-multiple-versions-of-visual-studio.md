---
title: 여러 버전의 비주얼 스튜디오 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699484"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>여러 버전의 Visual Studio 지원
*나란히* 라는 용어는 동일한 컴퓨터에 여러 버전의 제품을 설치하고 유지할 수 있음을 의미합니다. VSPackage의 경우 사용자가 동일한 컴퓨터에 여러 개의 Visual Studio 버전을 설치할 수 있습니다. 그러나 VSPackage의 나란히 버전을 단일 버전의 Visual Studio에 로드할 수는 없습니다.

 VSPackage를 나란히 버전의 Visual Studio에 로드할 수 있도록 하기 전에 다음을 고려하십시오.

- 따라야 할 나란히 구현 전략을 결정해야 합니다.

   자세한 내용은 [공유 및 버전이 있는 VSPackage 중 선택을](../extensibility/choosing-between-shared-and-versioned-vspackages.md)참조하십시오.

- 솔루션 및 프로젝트 파일 형식은 구현 전략에 맞아야 합니다.

   자세한 내용은 [나란히 배포할 수 있는 사용자 지정 프로젝트 업그레이드](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) 및 파일 이름 [확장자 등록을](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)참조하십시오.

- 모든 버전에서 공유되는 버전이 있는 구성 요소와 구성 요소가 올바르게 설치되고 등록되도록 설치 관리자는 구현 전략을 처리해야 합니다.

   자세한 내용은 [VS패키지 설치 를 참조하여 Windows 설치 관리자및](../extensibility/internals/installing-vspackages-with-windows-installer.md) [구성 요소 관리를](../extensibility/internals/component-management.md)사용할 수 있습니다.

  > [!NOTE]
  > Visual Studio 버전을 설치하면 .NET Framework의 해당 버전도 설치됩니다. 예를 들어 동일한 컴퓨터에 Visual Studio 2010 및 Visual Studio 2012를 설치하면 .NET Framework의 버전 4.0과 4.5도 각각 설치됩니다.

## <a name="in-this-section"></a>섹션 내용
- [공유 VS 패키지 와 버전이 있는 VS패키지 중 에서 선택](../extensibility/choosing-between-shared-and-versioned-vspackages.md) VSPackage에서 나란히 문제를 해결하는 방법을 설명합니다.

- [나란히 배포할 파일 이름 확장자 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) VSPackage가 나란히 시나리오에서 파일 연결을 등록하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
- [Windows Installer를 사용하여 VSPackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md)

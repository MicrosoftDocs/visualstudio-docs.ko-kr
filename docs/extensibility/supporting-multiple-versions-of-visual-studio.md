---
title: 여러 버전의 Visual Studio 지원 | Microsoft Docs
description: 여러 버전의 Visual Studio를 지 원하는 방법에 대해 알아봅니다. Vspackage는 다양 한 버전으로 로드할 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d455ebf18ee8817e2adac2fa266592594ca7e6c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056105"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>여러 버전의 Visual Studio 지원
이러한 용어는 동일한 컴퓨터에 여러 버전의 제품을 설치 하 고 유지 관리할 *수 있음을 의미* 합니다. Vspackage의 경우 사용자가 여러 Visual Studio 버전을 동일한 컴퓨터에 설치할 수 있습니다. 그러나 Vspackage의 side-by-side 버전을 Visual Studio의 단일 버전으로 로드할 수는 없습니다.

 VSPackage를 Visual Studio의 side-by-side 버전으로 로드할 수 있도록 하기 전에 다음 사항을 고려 하세요.

- 따라야 하는 side-by-side 구현 전략을 결정 해야 합니다.

   자세한 내용은 [공유 및 버전 관리 Vspackage 중에서 선택](../extensibility/choosing-between-shared-and-versioned-vspackages.md)을 참조 하세요.

- 솔루션 및 프로젝트 파일 형식은 구현 전략에 맞아야 합니다.

   자세한 내용은 [사용자 지정 프로젝트 업그레이드](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) 및 [side-by-side 배포를 위한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)을 참조 하세요.

- 설치 관리자는 버전이 지정 된 구성 요소와 모든 버전에서 공유 되는 구성 요소가 올바르게 설치 및 등록 되도록 구현 전략을 처리 해야 합니다.

   자세한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md) 및 [구성 요소 관리](../extensibility/internals/component-management.md)를 참조 하세요.

  > [!NOTE]
  > 버전의 Visual Studio를 설치 하면 해당 버전의 .NET Framework도 설치 됩니다. 예를 들어, 동일한 컴퓨터에 Visual Studio 2010 및 Visual Studio 2012를 설치 하면 각각 .NET Framework의 버전 4.0 및 4.5이 설치 됩니다.

## <a name="in-this-section"></a>섹션 내용
- [공유 및 버전 관리 Vspackage 중에서 선택](../extensibility/choosing-between-shared-and-versioned-vspackages.md) VSPackage에서 side-by-side 문제를 해결 하는 방법을 설명 합니다.

- [Side-by-side 배포를 위한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) VSPackage가 병렬 시나리오에서 파일 연결을 등록 하는 방법에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [Windows Installer를 사용하여 VSPackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md)

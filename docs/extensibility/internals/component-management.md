---
title: 구성 요소 관리 | Microsoft Docs
description: Visual Studio에서 VSPackage 설치 관리자를 만들 때 Windows Installer 구성 요소를 관리 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9767af4c30957111526303600f9e8eda815b42f0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057093"
---
# <a name="component-management"></a>구성 요소 관리
Windows Installer의 작업 단위를 Windows Installer 구성 요소 (WICs 또는 구성 요소 라고도 함) 라고 합니다. GUID는 Windows Installer를 사용 하는 설치에 대 한 기본 설치 단위 및 참조 계산 인 각 WIC를 식별 합니다.

 여러 제품을 사용 하 여 VSPackage 설치 관리자를 만들 수 있지만이 논의에서는 Windows Installer (*.msi*) 파일을 사용 하는 것으로 가정 합니다. 설치 관리자를 만들 때 정확한 참조 계산이 항상 발생 하도록 파일 배포를 올바르게 관리 해야 합니다. 따라서 제품의 여러 버전은 설치 및 제거 시나리오를 혼합 하 여 서로 방해 하거나 서로 중단 하지 않습니다.

 Windows Installer에서 참조 횟수는 구성 요소 수준에서 발생 합니다. 리소스 (파일, 레지스트리 항목 등)를 구성 요소로 신중 하 게 구성 해야 합니다. 다른 시나리오에서 도움이 될 수 있는 모듈, 기능, 제품 등의 다른 수준의 조직이 있습니다. 자세한 내용은 [Windows Installer 기본 사항](../../extensibility/internals/windows-installer-basics.md)을 참조 하세요.

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Side-by-side 설치를 위한 설치 프로그램 제작 지침

- 버전 간에 공유 되는 파일 및 레지스트리 키를 자체 구성 요소로 작성 합니다.

     이렇게 하면 다음 버전에서 쉽게 사용할 수 있습니다. 예를 들어 전역으로 등록 된 라이브러리, 파일 확장명, **HKEY_CLASSES_ROOT** 에 등록 된 기타 항목 등을 입력 합니다.

- 공유 구성 요소를 별도의 병합 모듈로 그룹화 합니다.

     이 전략은 병렬 설치를 위해 적절히 작성 하는 데 도움이 됩니다.

- 버전 간에 동일한 Windows Installer 구성 요소를 사용 하 여 공유 파일 및 레지스트리 키를 설치 합니다.

     다른 구성 요소를 사용 하는 경우 파일 및 레지스트리 항목은 버전이 하나 VSPackage 제거 되지만 다른 VSPackage 아직 설치 되어 있으면 제거 됩니다.

- 동일한 구성 요소에서 버전이 지정 된 항목과 공유 항목을 혼합 하지 마세요.

     이렇게 하면 공유 항목을 전역 위치 및 버전이 지정 된 항목에 격리 된 위치에 설치할 수 없습니다.

- 버전이 지정 된 파일을 가리키는 공유 레지스트리 키가 없습니다.

     이렇게 하면 다른 버전의 VSPackage가 설치 된 경우 공유 키가 덮어쓰여집니다. 두 번째 버전을 제거한 후에는 해당 키가 가리키는 파일이 사라집니다.

## <a name="see-also"></a>참조
- [공유 및 버전 관리 Vspackage 중에서 선택](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VSPackage 설치 시나리오](../../extensibility/internals/vspackage-setup-scenarios.md)

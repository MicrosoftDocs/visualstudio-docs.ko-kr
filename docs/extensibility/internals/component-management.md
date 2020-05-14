---
title: 구성 요소 관리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5dcac9fb14a83021b852be2c52436fcdca84bf5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709332"
---
# <a name="component-management"></a>구성 요소 관리
Windows 설치 관리자의 작업 단위를 Windows 설치 관리자 구성 요소(WICs 또는 구성 요소라고도 함)라고 합니다. GUID는 Windows 설치 관리자를 사용하는 설치에 대한 설치 및 참조 계산의 기본 단위인 각 WIC를 식별합니다.

 여러 제품을 사용하여 VSPackage 설치 관리자를 만들 수 있지만 이 설명에서는 Windows*Installer(.msi)* 파일을 사용하는 것으로 가정합니다. 설치 관리자를 만들 때 올바른 참조 계산이 항상 이루어지도록 파일 배포를 올바르게 관리해야 합니다. 따라서 제품의 다른 버전은 설치 및 제거 시나리오를 혼합하여 서로 간섭하거나 중단하지 않습니다.

 Windows 설치 관리자에서 참조 카운트는 구성 요소 수준에서 발생합니다. 리소스(파일, 레지스트리 항목 등)를 구성 요소로 신중하게 구성해야 합니다. 모듈, 기능 및 제품과 같은 다른 수준의 조직이 다양한 시나리오에서 도움이 될 수 있습니다. 자세한 내용은 [Windows 설치 관리자 기본 을](../../extensibility/internals/windows-installer-basics.md)참조하십시오.

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>나란히 설치를 위한 작성 설정 지침

- 버전 간에 공유되는 파일 및 레지스트리 키를 자체 구성 요소로 작성합니다.

     이렇게 하면 다음 버전에서 쉽게 사용할 수 있습니다. 예를 들어 전역으로 등록된 형식 라이브러리, 파일 확장자, **HKEY_CLASSES_ROOT**등록된 기타 항목 등입니다.

- 공유 구성 요소를 별도의 병합 모듈로 그룹화합니다.

     이 전략을 사용하면 병렬 설치를 위해 올바르게 작성할 수 있습니다.

- 여러 버전에서 동일한 Windows Installer 구성 요소를 사용하여 공유 파일 및 레지스트리 키를 설치합니다.

     다른 구성 요소를 사용하는 경우 버전이 지정된 VSPackage가 제거되었지만 다른 VSPackage가 여전히 설치되어 있을 때 파일 및 레지스트리 항목이 제거됩니다.

- 동일한 구성 요소에서 버전이 있는 항목과 공유 항목을 혼합하지 마십시오.

     이렇게 하면 공유 항목을 전역 위치에 설치하고 격리된 위치에 버전이 있는 항목을 설치할 수 없습니다.

- 버전이 변경된 파일을 가리키는 공유 레지스트리 키가 없습니다.

     이렇게 하면 다른 버전이 있는 VSPackage를 설치할 때 공유 키가 덮어씁을 씁쓸하게 됩니다. 두 번째 버전을 제거한 후 키가 가리키는 파일이 사라집니다.

## <a name="see-also"></a>참조
- [공유 및 버전 이면된 VSPackage 중에서 선택](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [VS패키지 설정 시나리오](../../extensibility/internals/vspackage-setup-scenarios.md)

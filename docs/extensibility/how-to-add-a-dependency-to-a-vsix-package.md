---
title: '방법: VSIX 패키지에 종속성을 추가 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711073"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>방법: VSIX 패키지에 종속성을 추가합니다.

대상 컴퓨터에 아직 없는 종속성을 설치하는 VSIX 패키지 배포를 설정할 수 있습니다. 이렇게 하려면 *source.extension.vsixmanifest* 파일에 VSIX 종속성을 포함합니다.

## <a name="to-add-a-dependency"></a>종속성을 추가하려면

1. **디자인** 보기에서 *source.extension.vsixmanifest* 파일을 엽니다. **종속성** 탭으로 이동하여 **새**을 클릭합니다.

2. 설치된 확장을 추가하려면 새 **종속성 추가** 대화 상자에서 **설치된 확장을** 선택한 다음 **Name에**대해 목록에서 확장을 선택합니다.

3. 설치되지 않은 다른 VSIX를 추가하려면 새 **종속성 추가** 대화 상자에서 **파일 시스템에서 파일을** 선택한 다음 **찾아보기** 단추를 사용하여 VSIX를 선택합니다.

## <a name="require-a-specific-visual-studio-release"></a>특정 비주얼 스튜디오 릴리스 필요

예를 들어 확장에 특정 버전의 Visual Studio 2017이 필요한 경우 15.3에서 릴리스된 기능에 따라 달라지므로 VSIX **InstallationTarget**에서 빌드 번호를 지정할 수 있습니다. 예를 들어 릴리스 15.3에는 빌드 번호가 '15.0.26730.3'입니다. 여기에서 숫자를 빌드하는 릴리스의 매핑을 볼 수 [있습니다.](../install/visual-studio-build-numbers-and-release-dates.md) 릴리스 번호 '15.3'을 사용하면 제대로 작동하지 않습니다.

확장에 15.3 이상이 필요한 경우 **설치 대상 버전을** [15.0.26730.3, 16.0)으로 선언합니다.

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller는 이전 버전의 Visual Studio를 검색하고 사용자에게 이후 업데이트가 필요하다는 것을 알립니다.

## <a name="see-also"></a>참조

- [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [VSIX 패키지의 해부학](../extensibility/anatomy-of-a-vsix-package.md)
- [Windows 설치 관리자 배포에 대 한 확장 준비](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

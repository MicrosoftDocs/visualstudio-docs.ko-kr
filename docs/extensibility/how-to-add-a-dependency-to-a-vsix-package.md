---
title: '방법: VSIX 패키지에 종속성 추가 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 063767f8f50793253c236db5d5b90e1d6db1bff4
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905863"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>방법: VSIX 패키지에 종속성 추가

대상 컴퓨터에 아직 없는 종속성을 설치 하는 VSIX 패키지 배포를 설정할 수 있습니다. 이를 수행 하려면 *source.extension.vsixmanifest* 파일에 VSIX 종속성을 포함 합니다.

## <a name="to-add-a-dependency"></a>종속성을 추가 하려면

1. **디자인** 뷰에서 *source.extension.vsixmanifest* 파일을 엽니다. **종속성** 탭으로 이동 하 고 **새로 만들기**를 클릭 합니다.

2. 설치 된 확장을 추가 하려면 **새 종속성 추가** 대화 상자에서 **설치 된 확장** 을 선택 하 고 **이름**에 대해 목록에서 확장을 선택 합니다.

3. 설치 되지 않은 다른 VSIX를 추가 하려면 다음을 수행 합니다. **새 종속성 추가** 대화 상자에서 파일 **시스템의 파일** 을 선택한 다음 **찾아보기** 단추를 사용 하 여 VSIX를 선택 합니다.

## <a name="require-a-specific-visual-studio-release"></a>특정 Visual Studio 릴리스 필요

확장에 특정 버전의 Visual Studio 2017가 필요한 경우 (예: 15.3에서 릴리스된 기능에 따라 달라 지는 경우) VSIX **설치 대상**에서 빌드 번호를 지정할 수 있습니다. 예를 들어 릴리스 15.3의 빌드 번호는 ' 15.0.26730.3 '입니다. [여기](../install/visual-studio-build-numbers-and-release-dates.md)에서 빌드 번호에 대 한 릴리스 매핑을 볼 수 있습니다. 릴리스 번호 ' 15.3 '을 사용 하면 제대로 작동 하지 않습니다.

확장에 15.3 이상이 필요한 경우 **설치 대상 버전** 을 [15.0.26730.3, 16.0)로 선언 합니다.

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller는 이전 버전의 Visual Studio를 검색 하 고 나중에 업데이트가 필요 함을 사용자에 게 알립니다.

## <a name="see-also"></a>참조

- [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)
- [Windows Installer 배포를 위한 확장 준비](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

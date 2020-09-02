---
title: '방법: Visual Basic 개발자 설정을 적용하여 빌드 구성 관리 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a5f8568edc636955558ec93b55c0aedebf0065d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651830"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>방법: Visual Basic 개발자 설정을 적용하여 빌드 구성 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 개발자 설정이 적용되면 기본적으로 모든 고급 빌드 구성 옵션이 숨겨집니다. 이 항목에서는 이러한 설정을 수동으로 사용하도록 설정하는 방법을 설명합니다.

## <a name="enabling-advanced-build-configurations"></a>고급 빌드 구성 사용
 기본적으로 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 개발자 설정은 [프로젝트 디자이너](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7)의 **구성** 및 **플랫폼** 목록과 **구성 관리자** 대화 상자를 여는 옵션을 숨깁니다.

#### <a name="to-enable-advanced-build-configurations"></a>고급 빌드 구성을 사용하도록 설정하려면

1. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. **프로젝트 및 솔루션**을 확장하고 **일반**을 클릭합니다.

    > [!NOTE]
    > **일반** 노드는 **모든 설정 표시** 옵션이 선택 취소된 경우에도 표시됩니다. 모든 옵션을 사용 가능하게 표시하려면 **모든 설정 표시**를 클릭합니다.

3. **고급 빌드 구성 표시**를 클릭합니다.

4. **확인**을 클릭합니다.

     **빌드** 메뉴에서 **Configuration Manager** 현재 사용할 수 있으며, **구성** 및 **플랫폼** 목록이 프로젝트 디자이너에 표시 됩니다.

## <a name="see-also"></a>관련 항목
 [빌드 구성 이해](../ide/understanding-build-configurations.md) [및](../ide/compiling-and-building-in-visual-studio.md) 빌드

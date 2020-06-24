---
title: '방법: 공통 출력 디렉터리로 빌드'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a499b5ca5ea64dd9ded10f82b1af43258f346d3
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284778"
---
# <a name="how-to-build-to-a-common-output-directory"></a>방법: 공통 출력 디렉터리로 빌드

기본적으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]은(는) 솔루션 내에서 고유 폴더에 있는 솔루션에서 각 프로젝트를 빌드합니다. 프로젝트의 빌드 출력 경로를 변경하여 모든 출력이 동일한 폴더에 배치되도록 할 수 있습니다.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>모든 솔루션 출력을 공용 디렉터리에 배치하려면

1. 솔루션에서 한 프로젝트를 클릭합니다.

2. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

3. 프로젝트의 유형에 따라 **컴파일** 탭 또는 **빌드** 탭을 클릭하고 **출력 경로**를 솔루션에 있는 모든 프로젝트에 사용할 폴더로 설정합니다.

4. 솔루션의 모든 프로젝트에 대해 1-3단계를 반복합니다.

## <a name="see-also"></a>참고 항목

- [컴파일 및 빌드](../ide/compiling-and-building-in-visual-studio.md)
- [방법: 빌드 출력 디렉터리 변경](../ide/how-to-change-the-build-output-directory.md)
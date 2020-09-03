---
title: VS 셸 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: be8f2ffe-a322-4ac0-9c9e-873bd28e5d5e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a42ec6a762655589bfd589ae9dc0354e3a7d1cb5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659312"
---
# <a name="vs-shell-deployment"></a>VS 셸 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

격리 된 셸을 사용 하면 도메인별 언어와 상호 작용 하는 데 필요한 Visual Studio 기능과 해당 솔루션이 표시 되는 방법을 결정할 수 있습니다. Visual Studio의 격리 된 셸에 대 한 자세한 내용은 [격리 된 셸 사용자 지정](../extensibility/customizing-the-isolated-shell.md)을 참조 하세요. 격리 셸을 사용자 지정 하는 방법에 대 한 자세한 내용은 [격리 된 셸 사용자](https://msdn.microsoft.com/d75463cd-1155-42e4-8b7a-046ed6becbbf)지정에서 확인할 수 있습니다.

### <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Visual Studio 셸을 배포 대상으로 설정 하려면

1. **Dslpackage** 프로젝트에서 **source.extension.tt**를 엽니다.

2. 삽입 아래에서 `<SupportedProducts>` 다음을 수행 합니다.

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     *MyIsolatedShell* 을 격리 된 셸 패키지의 이름으로 바꿉니다.

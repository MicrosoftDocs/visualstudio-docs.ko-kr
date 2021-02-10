---
title: 프로세스 뷰 | Microsoft Docs
description: 프로세스 뷰에는 시스템의 모든 활성 프로세스 트리가 표시됩니다. 해당 콘텐츠 및 사용에 관해 알아보고 링크에 따라 추가 정보를 확인합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d48be382e222c9ca494237ae6b72bae54bb90d62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891451"
---
# <a name="processes-view"></a>프로세스 뷰
프로세스 뷰는 시스템의 모든 활성 프로세스의 트리를 표시합니다. 프로세스 ID와 모듈 이름이 표시됩니다. 일반적으로 실행 중인 프로그램에 해당하는 특정 시스템 프로세스를 검사하려면 프로세스 뷰를 사용합니다. 프로세스는 모듈 이름으로 식별되거나 “시스템 프로세스”로 지정됩니다.

 Microsoft Windows는 여러 프로세스를 지원합니다. 각 프로세스에는 하나 이상의 스레드가 있을 수 있으며, 각 스레드에는 하나 이상의 최상위 창이 연결되어 있을 수 있습니다. 각 최상위 창에는 일련의 창이 있습니다. \+ 기호는 수준이 축소되어 있음을 나타냅니다. 축소된 뷰는 프로세스당 한 줄로 구성됩니다. \+ 기호를 클릭하면 수준이 확장됩니다.

 일반적으로 실행 중인 프로그램에 해당하는 특정 시스템 프로세스를 검사하려면 프로세스 뷰를 사용합니다. 프로세스는 모듈 이름으로 식별되거나 “시스템 프로세스”로 지정됩니다. 프로세스를 찾으려면 트리를 축소하고 목록을 검색합니다.

## <a name="procedures"></a>절차

#### <a name="to-open-the-processes-view"></a>프로세스 뷰를 열려면

1. **Spy** 메뉴에서 **프로세스** 를 선택합니다.

   ![Spy&#43;&#43; 프로세스 뷰](../debugger/media/spy--_processes.png "Spy++_Processes") Spy++ 프로세스 뷰

   위의 그림은 프로세스 및 스레드 노드가 확장된 프로세스 뷰를 보여 줍니다.

### <a name="in-this-section"></a>섹션 내용
 [프로세스 뷰에서 프로세스 검색](../debugger/how-to-search-for-a-process-in-processes-view.md) 프로세스 뷰에서 특정 프로세스를 찾는 방법을 설명합니다.

 [프로세스 속성 표시](../debugger/how-to-display-process-properties.md) 메시지에 대한 자세한 정보를 표시하는 방법을 설명합니다.

### <a name="related-sections"></a>관련 단원
 [Spy++ 뷰](../debugger/spy-increment-views.md) 창, 메시지, 프로세스 및 스레드의 Spy++ 트리 뷰에 대해 설명합니다.

 [Spy++ 사용](../debugger/using-spy-increment.md) Spy++ 도구를 소개하고 해당 도구를 사용할 수 있는 방법을 설명합니다.

 [프로세스 검색 대화 상자](../debugger/process-search-dialog-box.md)는 프로세스 뷰에서 특정 프로세스의 노드를 찾는 데 사용됩니다.

 [프로세스 속성 대화 상자](../debugger/process-properties-dialog-box.md) 프로세스 뷰에서 선택한 프로세스의 속성을 표시합니다.

 [Spy++ 참조](../debugger/spy-increment-reference.md) 각 Spy++ 메뉴 및 대화 상자에 대해 설명하는 섹션이 있습니다.
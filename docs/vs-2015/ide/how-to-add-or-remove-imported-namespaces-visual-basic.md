---
title: '방법: 가져온 네임스페이스 추가 또는 제거(Visual Basic) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 75299dae66a07b2bc1671dbfcda935fc4af2b284
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645492"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>방법: 가져온 네임스페이스 추가 또는 제거(Visual Basic)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

네임스페이스를 가져오면 해당 네임스페이스의 요소를 정규화하지 않고 코드에서 사용할 수 있습니다. 예를 들어 `System.Messaging.MessageQueue` 클래스의 `Create` 메서드에 액세스하려면 `System.Messaging` 네임스페이스를 가져오고 코드에 필요한 요소를 `MessageQueue.Create`로 참조하면 됩니다.

 가져온 네임스페이스는 **프로젝트 디자이너**의 **참조** 페이지에서 관리됩니다. 이 대화 상자에서 지정하는 가져오기는 컴파일러(`/imports`)에 직접 전달되고 프로젝트의 모든 파일에 적용됩니다. `Imports` 문을 사용하여 단일 소스 코드 파일에서 네임스페이스를 사용합니다.

### <a name="to-add-an-imported-namespace"></a>가져온 네임스페이스를 추가하려면

1. **솔루션 탐색기**에서 프로젝트의 **My Project** 노드를 두 번 클릭합니다.

2. **프로젝트 디자이너**에서 **참조** 탭을 클릭합니다.

3. **가져온 네임스페이스** 목록에서 추가할 네임스페이스의 확인란을 선택합니다.

    > [!NOTE]
    > 가져올 네임스페이스는 참조된 구성 요소에 있어야 합니다. 네임스페이스가 목록에 나타나지 않으면 네임스페이스가 포함된 구성 요소에 참조를 추가해야 합니다. 자세한 내용은 [NIB 방법: 참조 추가 대화 상자를 사용하여 참조 추가 또는 제거](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)를 참조하세요.

### <a name="to-remove-an-imported-namespace"></a>가져온 네임스페이스를 제거하려면

1. **솔루션 탐색기**에서 프로젝트의 **My Project** 노드를 두 번 클릭합니다.

2. **프로젝트 디자이너**에서 **참조** 탭을 클릭합니다.

3. **가져온 네임스페이스** 목록에서 제거할 네임스페이스의 확인란을 선택 취소합니다.

## <a name="user-imports"></a>사용자 가져오기
 사용자 가져오기를 사용하여 전체 네임스페이스가 아닌 특정 네임스페이스 내의 특정 클래스를 가져올 수 있습니다. 예를 들어 애플리케이션에는 `Systems.Diagnostics` 네임스페이스에 대한 가져오기가 있을 수 있지만, 관심 있는 네임스페이스 내의 유일한 클래스는 `Debug` 클래스입니다. `System.Diagnostics.Debug`를 사용자 가져오기를 정의하고 나서 `System.Diagnostics`에 대한 가져오기를 제거할 수 있습니다.

 필요한 것이 실제로 `EventLog` 클래스였다는 생각과 결정을 나중에 변경한다면 `System.Diagnostics.EventLog`를 사용자 가져오기로 입력하고 업데이트 기능을 사용하여 `System.Diagnostics.Debug`를 덮어쓸 수 있습니다.

#### <a name="to-add-a-user-import"></a>사용자 가져오기를 추가하려면

1. **솔루션 탐색기**에서 프로젝트의 **My Project** 노드를 두 번 클릭합니다.

2. **프로젝트 디자이너**에서 **참조** 탭을 클릭합니다.

3. **가져온 네임스페이스** 목록 아래 텍스트 상자에 루트 네임스페이스를 포함하여 가져올 네임스페이스의 전체 이름을 입력합니다.

4. **사용자 가져오기 추가** 단추를 클릭하여 **가져온 네임스페이스** 목록에 네임스페이스를 추가합니다.

    > [!NOTE]
    > 네임스페이스가 이미 목록에 있는 네임스페이스와 일치할 경우 **사용자 가져오기 추가** 단추가 사용하지 않도록 설정됩니다. 하나의 가져오기를 두 번 추가할 수는 없습니다.

#### <a name="to-update-a-user-import"></a>사용자 가져오기를 업데이트하려면

1. **솔루션 탐색기**에서 프로젝트의 **My Project** 노드를 두 번 클릭합니다.

2. **프로젝트 디자이너**에서 **참조** 탭을 클릭합니다.

3. **가져온 네임스페이스** 목록에서 변경할 네임스페이스를 선택합니다.

4. **가져온 네임스페이스** 목록 아래 텍스트 상자에 새 네임스페이스의 이름을 입력합니다.

5. **사용자 가져오기 업데이트** 단추를 클릭하여 **가져온 네임스페이스** 목록에서 네임스페이스를 업데이트합니다.

## <a name="see-also"></a>관련 항목
 [프로젝트의 참조 관리](../ide/managing-references-in-a-project.md)

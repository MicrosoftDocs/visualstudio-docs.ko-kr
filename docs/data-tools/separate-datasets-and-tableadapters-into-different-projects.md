---
title: 별도 프로젝트 사용 오류
description: 응용 프로그램 계층을 신속 하 게 분리 하 고 N 계층 데이터 응용 프로그램을 생성할 수 있도록 데이터 집합 및 Tableadapter를 다른 프로젝트로 분리 하는 방법을 알아봅니다.
ms.date: 11/04/2016
ms.topic: how-to
ms.custom: SEO-VS-2020
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 9463fe0371ee3184fd78684e7fe0565820ab3bf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866543"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>데이터 세트 및 TableAdapter를 다른 프로젝트로 분리
형식화 된 데이터 집합은 [tableadapter](create-and-configure-tableadapters.md) 및 데이터 집합 클래스가 개별 프로젝트로 생성 될 수 있도록 향상 되었습니다. 이를 통해 응용 프로그램 계층을 신속 하 게 분리 하 고 n 계층 데이터 응용 프로그램을 생성할 수 있습니다.

다음 절차에서는 **데이터 세트 디자이너** 를 사용 하 여 생성 된 TableAdapter 코드가 포함 된 프로젝트와 별도의 프로젝트에 데이터 집합 코드를 생성 하는 프로세스에 대해 설명 합니다.

## <a name="separate-datasets-and-tableadapters"></a>별도의 데이터 집합 및 Tableadapter
TableAdapter 코드에서 데이터 집합 코드를 분리 하는 경우 데이터 집합 코드가 포함 된 프로젝트를 현재 솔루션에 배치 해야 합니다. 이 프로젝트를 현재 솔루션에 배치 하지 않으면 **속성** 창의 **데이터 집합 프로젝트** 목록에서 사용할 수 없습니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>데이터 집합을 다른 프로젝트로 분리 하려면

1. 데이터 집합 (*.xsd* 파일)이 포함 된 솔루션을 엽니다.

    > [!NOTE]
    > 솔루션에 데이터 집합 코드를 분리 하려는 프로젝트가 포함 되어 있지 않으면 프로젝트를 만들거나 솔루션에 기존 프로젝트를 추가 합니다.

2. **솔루션 탐색기** 에서 형식화 된 데이터 집합 파일 ( *.xsd* 파일)을 두 번 클릭 하 여 **데이터 세트 디자이너** 에서 데이터 집합을 엽니다.

3. **데이터 세트 디자이너** 빈 영역을 선택 합니다.

4. **속성** 창에서 **데이터 집합 프로젝트** 노드를 찾습니다.

5. **데이터 집합 프로젝트** 목록에서 데이터 집합 코드를 생성 하려는 프로젝트의 이름을 선택 합니다.

     데이터 집합 코드를 생성 하려는 프로젝트를 선택 하면 **데이터 집합 파일** 속성이 기본 파일 이름으로 채워집니다. 필요한 경우이 이름을 변경할 수 있습니다. 또한 특정 디렉터리에 데이터 집합 코드를 생성 하려는 경우 **프로젝트 폴더** 속성을 폴더 이름으로 설정할 수 있습니다.

    > [!NOTE]
    > **데이터 집합 프로젝트** 속성을 설정 하 여 데이터 집합 및 tableadapter를 분리 하는 경우 프로젝트의 기존 부분 데이터 집합 클래스는 자동으로 이동 되지 않습니다. 기존 부분 데이터 집합 클래스는 데이터 집합 프로젝트로 수동으로 이동 해야 합니다.

6. 데이터 집합을 저장 합니다.

     데이터 집합 코드는 **데이터 집합 프로젝트** 속성에서 선택한 프로젝트로 생성 되 고, **TableAdapter** 코드는 현재 프로젝트로 생성 됩니다.

데이터 집합 및 TableAdapter 코드를 분리 한 후에는 기본적으로 각 프로젝트의 불연속 클래스 파일이 생성 됩니다. 원본 프로젝트에는 TableAdapter 코드를 포함 하는 *DatasetName* (또는 *DatasetName.Designer.cs*) 라는 파일이 있습니다. **데이터 집합 프로젝트** 속성에 지정 된 프로젝트에는 데이터 집합 코드를 포함 하는 *DatasetName* (또는 *DatasetName.DataSet.Designer.cs*) 라는 파일이 있습니다.

> [!NOTE]
> 생성 된 클래스 파일을 보려면 데이터 집합 또는 TableAdapter 프로젝트를 선택 합니다. 그런 다음 **솔루션 탐색기** 에서 **모든 파일 표시** 를 선택 합니다.

## <a name="see-also"></a>참고 항목

- [N 계층 데이터 애플리케이션 개요](../data-tools/n-tier-data-applications-overview.md)
- [연습: N 계층 데이터 응용 프로그램 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [계층적 업데이트](../data-tools/hierarchical-update.md)
- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)

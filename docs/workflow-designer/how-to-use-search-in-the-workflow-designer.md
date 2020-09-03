---
title: '방법: Workflow Designer에서 검색 사용'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63ad6f8b6d3afd1f30f2e9a02eaa4927fb3608d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817478"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>방법: Workflow Designer에서 검색 사용

더 크고 더 복잡 한 워크플로를 쉽게 만들 수 있도록 워크플로 디자이너 내에서 검색 하 여 키워드별로 항목을 찾을 수 있습니다. 디자이너는 바꾸기를 지원하지 않습니다.

## <a name="quick-find"></a>빠른 찾기

빠른 찾기는 디자이너에서 다음을 찾습니다.

- <xref:System.Activities.Activity> 개체, <xref:System.Activities.Statements.FlowNode> 개체, <xref:System.Activities.Statements.State> 개체, 전환 및 기타 사용자 지정 흐름 제어 항목의 속성

- 변수

- 인수

- 식

### <a name="use-quick-find"></a>빠른 찾기 사용

1. Workflow designer를 연 상태에서 **ctrl + F**를 누르거나 찾기 **편집**  >  **을 선택 하 고**  >  **빠른 찾기**를 바꿉니다.

2. **찾을 내용** 텍스트 상자에 검색 용어를 입력 하 고 **다음 찾기**를 클릭 합니다.

3. 검색 용어는 현재 워크플로에 있습니다. 다음 그림은 디자이너에 있는 활동 표시 이름을 보여 줍니다.

   ![워크플로 디자이너의 검색 결과](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>파일에서 찾기

파일에서 찾기는 XAML 파일을 포함 하 여 워크플로 파일에서 문자열을 찾습니다.

### <a name="use-find-in-files"></a>파일에서 찾기 사용

1. Visual Studio에서 **ctrl** + **Shift** + **F**를 누르거나, 찾기 **편집**  >  **을 선택 하 고**  >  **파일에서 찾기**를 바꾸기를 선택 합니다.

2. **찾을 내용** 텍스트 상자에 검색 항목을 입력 하 고 **모두 찾기**를 클릭 합니다.

3. **찾기 결과 보기에** 찾기 결과가 표시 됩니다. 결과 항목을 두 번 클릭 하면 workflow designer의 일치 항목이 포함 된 활동으로 이동 합니다.
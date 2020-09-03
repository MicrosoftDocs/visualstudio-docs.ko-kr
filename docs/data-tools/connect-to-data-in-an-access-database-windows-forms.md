---
title: Access 데이터베이스의 데이터에 연결
ms.date: 07/18/2019
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting
- connecting to data, Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3a94467dbfa0c11fdb7bb6ba7aa4d304fef3979f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800634"
---
# <a name="connect-to-data-in-an-access-database"></a>Access 데이터베이스의 데이터에 연결

Visual Studio를 사용 하 여 Access 데이터베이스 ( *.mdb* 파일 또는 *.accdb* 파일)에 연결할 수 있습니다. 연결을 정의한 후 **데이터 원본** 창에 데이터가 나타납니다. 여기에서 테이블 또는 뷰를 디자인 화면으로 끌 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

이러한 절차를 사용 하려면 Windows Forms 또는 WPF 프로젝트와 Access 데이터베이스 (*.accdb* 파일) 또는 access 2000-2003 데이터베이스 (*.mdb* 파일)가 필요 합니다. 파일 형식에 해당하는 절차를 따릅니다.

## <a name="create-a-dataset-for-an-accdb-file"></a>.Accdb 파일에 대 한 데이터 집합 만들기

다음 절차를 사용 하 여 Microsoft 365, 액세스 2013, 액세스 2010 또는 액세스 2007를 사용 하 여 만든 데이터베이스에 연결 합니다.

1. Visual Studio에서 Windows Forms 또는 WPF 응용 프로그램 프로젝트를 엽니다.

2. **데이터 소스** 창을 열려면 **보기** 메뉴에서 **다른 Windows**  >  **데이터 소스**를 선택 합니다.

   ![다른 창 데이터 소스 보기](../data-tools/media/viewdatasources.png)

3. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.

   **데이터 원본 구성** 마법사가 열립니다.

4. **데이터 소스 형식 선택** 페이지에서 **데이터베이스** 를 선택 하 고 **다음**을 선택 합니다.

5. **데이터베이스 모델 선택** 페이지에서 **데이터 집합** 을 선택 하 고 **다음**을 선택 합니다.

6. **데이터 연결 선택** 페이지에서 **새 연결**을 선택하여 새 데이터 연결을 구성합니다.

   **연결 추가** 대화 상자가 열립니다.

7. **데이터 원본을** **Microsoft Access 데이터베이스 파일**로 설정 하지 않은 경우에는 **변경** 단추를 선택 합니다.

   **데이터 소스 변경** 대화 상자가 열립니다. 데이터 원본 목록에서 **Microsoft Access 데이터베이스 파일**을 선택 합니다. **데이터 공급자** 드롭다운에서 **.NET Framework Data Provider OLE DB**를 선택한 다음 **확인**을 선택 합니다.

8. **데이터베이스 파일 이름**옆에 있는 **찾아보기** 를 선택한 다음 *.Accdb* 파일로 이동 하 여 **열기**를 선택 합니다.

9. 사용자 이름 및 암호 (필요한 경우)를 입력 한 다음 **확인**을 선택 합니다.

10. **데이터 연결 선택** 페이지에서 **다음** 을 선택 합니다.

    데이터 파일이 현재 프로젝트에 없다고 알려주는 대화 상자가 표시 될 수 있습니다. **예** 또는 **아니요**를 선택 합니다.

11. **응용 프로그램 구성 파일에 연결 문자열 저장** 페이지에서 **다음** 을 선택 합니다.

12. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.

13. 데이터 집합에 포함 하려는 테이블이 나 뷰를 선택한 다음 **마침**을 선택 합니다.

    데이터 세트가 프로젝트에 추가되고 테이블과 뷰가 **데이터 원본** 창에 나타납니다.

## <a name="create-a-dataset-for-an-mdb-file"></a>.Mdb 파일에 대 한 데이터 집합 만들기

다음 절차에 따라 Access 2000-2003를 사용 하 여 만든 데이터베이스에 연결 합니다.

1. Visual Studio에서 Windows Forms 또는 WPF 응용 프로그램 프로젝트를 엽니다.

2. **보기** 메뉴에서 **기타 Windows**  >  **데이터 원본**을 선택 합니다.

   ![다른 창 데이터 소스 보기](../data-tools/media/viewdatasources.png)

3. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.

    **데이터 원본 구성** 마법사가 열립니다.

4. **데이터 소스 형식 선택** 페이지에서 **데이터베이스** 를 선택 하 고 **다음**을 선택 합니다.

5. **데이터베이스 모델 선택** 페이지에서 **데이터 집합** 을 선택 하 고 **다음**을 선택 합니다.

6. **데이터 연결 선택** 페이지에서 **새 연결**을 선택하여 새 데이터 연결을 구성합니다.

7. 데이터 원본이 **Microsoft Access 데이터베이스 파일 (OLE DB)** 이 아니면 **변경** 을 선택 하 여 **데이터 소스 변경** 대화 상자를 열고 **Microsoft Access 데이터베이스 파일**을 선택한 다음 **확인**을 선택 합니다.

8. **데이터베이스 파일 이름**에서 연결 하려는 *.mdb* 파일의 경로와 이름을 지정한 다음 **확인**을 선택 합니다.

   ![연결 액세스 데이터베이스 파일 추가](../data-tools/media/add-connection-access-db.png)

9. **데이터 연결 선택** 페이지에서 **다음** 을 선택 합니다.

10. **응용 프로그램 구성 파일에 연결 문자열 저장** 페이지에서 **다음** 을 선택 합니다.

11. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.

12. 데이터 집합에서 원하는 테이블 또는 뷰를 선택 하 고 **마침**을 선택 합니다.

    데이터 세트가 프로젝트에 추가되고 테이블과 뷰가 **데이터 원본** 창에 나타납니다.

## <a name="next-steps"></a>다음 단계

방금 만든 데이터 집합은 **데이터 소스** 창에서 사용할 수 있습니다. 다음 작업 중 어떤 작업이든 수행할 수 있습니다.

- **데이터 소스** 창에서 항목을 선택 하 고 폼 또는 디자인 화면으로 끌어 옵니다 ( [Visual Studio에서 데이터에 컨트롤 Windows Forms 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) 또는 [WPF 데이터 바인딩 개요](/dotnet/desktop-wpf/data/data-binding-overview)참조).

- **데이터 세트 디자이너**에서 데이터 원본을 열어 데이터 세트를 구성하는 개체를 추가하거나 편집합니다.

- 데이터 <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> 집합에 있는 데이터 테이블의 또는 이벤트에 유효성 검사 논리를 추가 합니다 (데이터 [집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)참조).

## <a name="see-also"></a>추가 정보

- [연결 추가](../data-tools/add-new-connections.md)
- [WPF 데이터 바인딩 개요](/dotnet/framework/wpf/data/data-binding-overview)
- [Windows Forms 데이터 바인딩](/dotnet/framework/winforms/data-binding-and-windows-forms)

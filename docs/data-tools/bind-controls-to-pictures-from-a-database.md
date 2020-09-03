---
title: 데이터베이스의 그림에 컨트롤 바인딩
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e9093c2a2d7cec95e4fdd08ff4273ae8f8126a36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282986"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>데이터베이스의 그림에 컨트롤 바인딩

**데이터 소스** 창을 사용 하 여 데이터베이스의 이미지를 응용 프로그램의 컨트롤에 바인딩할 수 있습니다. 예를 들어, <xref:System.Windows.Controls.Image> WPF 응용 프로그램의 컨트롤 또는 <xref:System.Windows.Forms.PictureBox> Windows Forms 응용 프로그램의 컨트롤에 이미지를 바인딩할 수 있습니다.

데이터베이스의 사진은 일반적으로 바이트 배열로 저장 됩니다. 바이트 배열로 저장 되는 **데이터 소스** 창의 항목에는 기본적으로 **없음** 으로 설정 되어 있습니다. 바이트 배열에는 간단한 바이트 배열의 모든 항목이 포함 될 수 있기 때문입니다. 이미지를 나타내는 **데이터 소스** 창에서 바이트 배열 항목에 대 한 데이터 바인딩된 컨트롤을 만들려면 만들 컨트롤을 선택 해야 합니다.

다음 절차에서는 **데이터 소스** 창이 이미 이미지에 바인딩된 항목으로 채워진 것으로 가정 합니다.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>데이터베이스의 그림을 컨트롤에 바인딩하려면

1. 컨트롤을 추가 하려는 디자인 화면이 WPF 디자이너 또는 Windows Forms 디자이너에서 열려 있는지 확인 합니다.

2. **데이터 원본** 창에서 원하는 테이블 또는 개체를 확장 하 여 해당 열 또는 속성을 표시 합니다.

   > [!TIP]
   > **데이터 소스** 창이 열려 있지 않으면 **View**  >  **다른 Windows**  >  **데이터 원본**보기를 선택 하 여 엽니다.

3. 이미지 데이터를 포함 하는 열 또는 속성을 선택 하 고 드롭다운 컨트롤 목록에서 다음 컨트롤 중 하나를 선택 합니다.

    - WPF designer가 열려 있으면 **이미지**를 선택 합니다.

    - Windows Forms designer가 열려 있으면 **PictureBox**를 선택 합니다.

    - 또는 데이터 바인딩을 지원 하 고 이미지를 표시할 수 있는 다른 컨트롤을 선택할 수 있습니다. 사용할 컨트롤이 사용 가능한 컨트롤 목록에 없으면 목록에 추가 하 여 선택할 수 있습니다 (예를 들어, 자세한 내용은 [데이터 소스 창에 사용자 지정 컨트롤 추가](../data-tools/add-custom-controls-to-the-data-sources-window.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)

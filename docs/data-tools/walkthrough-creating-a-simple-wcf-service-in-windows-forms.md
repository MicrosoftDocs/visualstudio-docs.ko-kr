---
title: Windows Forms에서 간단한 WCF 서비스 만들기
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 697e7b36b1b83987450a25e3cf8b717218bff5c9
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741929"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>연습: Windows Forms에서 간단한 WCF 서비스 만들기

이 연습에서는 WCF (simple Windows Communication Foundation) 서비스를 만들고 테스트 한 다음 Windows Forms 응용 프로그램에서 액세스 하는 방법을 보여 줍니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>서비스 만들기

1. Visual Studio를 엽니다.

::: moniker range="vs-2017"

2. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 선택합니다.

3. **새 프로젝트** 대화 상자에서 **Visual Basic** 또는 **Visual c #** 노드를 확장 하 고 wcf, **wcf 서비스 라이브러리**를 **차례로 선택 합니다**.

4. **확인**을 클릭하여 프로젝트를 만듭니다.

   ![WCF 서비스 라이브러리 프로젝트](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. 시작 창에서 **새 프로젝트 만들기**를 선택합니다.

3. **새 프로젝트 만들기** 페이지의 검색 상자에 **wcf 서비스 라이브러리** 를 입력 합니다. **WCF 서비스 라이브러리**의 c # 또는 Visual Basic 템플릿을 선택 하 고 **다음**을 클릭 합니다.

   ![Visual Studio 2019에서 새 WCF 서비스 라이브러리 프로젝트 만들기](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > 템플릿이 표시 되지 않는 경우 Visual Studio의 **Windows Communication Foundation** 구성 요소를 설치 해야 할 수 있습니다. **추가 도구 및 기능 설치** 를 선택 하 여 Visual Studio 설치 관리자을 엽니다. **개별 구성 요소** 탭을 선택 하 고 **개발 작업**으로 스크롤한 다음 **Windows Communication Foundation**를 선택 합니다. **수정**을 클릭합니다.

4. **새 프로젝트 구성** 페이지에서 **만들기**를 클릭 합니다.

::: moniker-end

   > [!NOTE]
   > 이렇게 하면 테스트 및 액세스할 수 있는 작업 서비스가 만들어집니다. 다음 두 단계는 다른 데이터 형식을 사용하도록 기본 메서드를 수정하는 방법을 보여 줍니다. 실제 애플리케이션에서는 서비스에 사용자 고유의 함수를 추가할 수도 있습니다.

5. **솔루션 탐색기**에서 **IService1** 또는 **IService1.cs**를 두 번 클릭 합니다.

   ![IService1 파일](../data-tools/media/wcf2.png)

   다음 줄을 찾습니다.

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   `value`매개 변수의 형식을 string으로 변경 합니다.

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   위의 코드에서 `<OperationContract()>` 또는 `[OperationContract]` 특성을 확인합니다. 이러한 특성은 서비스에서 노출하는 모든 메서드에 필요합니다.

6. **솔루션 탐색기**에서 **Service1** 또는 **Service1.cs**를 두 번 클릭 합니다.

   ![Service1 파일](../data-tools/media/wcf3.png)

   다음 줄을 찾습니다.

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   `value`매개 변수의 형식을 string으로 변경 합니다.

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>서비스 테스트

1. **F5** 키를 눌러 서비스를 실행합니다. **WCF 테스트 클라이언트** 폼이 표시 되 고 서비스가 로드 됩니다.

2. **WCF 테스트 클라이언트** 폼에서 **IService1** 아래의 **GetData()** 메서드를 두 번 클릭합니다. **GetData** 탭이 나타납니다.

     ![GetData&#40;&#41; 메서드](../data-tools/media/wcf4.png)

3. **요청** 상자에서 **값** 필드와 형식 `Hello`를 선택합니다.

     ![값 필드](../data-tools/media/wcf5.png)

4. **호출** 단추를 클릭합니다. **보안 경고** 대화 상자가 표시 되 면 **확인**을 클릭 합니다. 결과는 **응답** 상자에 표시 됩니다.

     ![응답 상자의 결과](../data-tools/media/wcf6.png)

5. **파일** 메뉴에서 **끝내기**를 클릭하여 테스트 폼을 닫습니다.

## <a name="access-the-service"></a>서비스 액세스

### <a name="reference-the-wcf-service"></a>WCF 서비스 참조

1. **파일** 메뉴에서 **추가** 를 가리킨 다음 **새 프로젝트**를 클릭 합니다.

2. **새 프로젝트** 대화 상자에서 **Visual Basic** 또는 **Visual c #** 노드를 확장 하 고 **Windows**를 선택한 다음 **Windows Forms 응용 프로그램**을 선택 합니다. **확인**을 클릭하여 프로젝트를 엽니다.

     ![Windows Forms 애플리케이션 프로젝트](../data-tools/media/wcf7.png)

3. **WindowsApplication1**을 마우스 오른쪽 단추로 클릭하고 **서비스 참조 추가**를 클릭합니다. **서비스 참조 추가** 대화 상자가 나타납니다.

4. **서비스 참조 추가** 대화 상자에서 **검색**을 클릭합니다.

     ![서비스 참조 추가 대화 상자](../data-tools/media/wcf8.png)

     **Service1** 이 **서비스** 창에 표시 됩니다.

5. **확인**을 클릭하여 서비스 참조를 추가합니다.

### <a name="build-a-client-application"></a>클라이언트 애플리케이션을 빌드합니다

1. Windows Forms 디자이너를 아직 열지 않은 경우 **솔루션 탐색기**에서 **Form1.vb** 또는 **Form1.cs**을 두 번 클릭하여 엽니다.

2. **도구 상자**에서 `TextBox` 컨트롤, `Label` 컨트롤 및 `Button` 컨트롤을 폼으로 끌어옵니다.

     ![폼에 컨트롤 추가](../data-tools/media/wcf9.png)

3. `Button`을 두 번 클릭하고 다음 코드를 `Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. **솔루션 탐색기**에서 **WindowsApplication1**을 마우스 오른쪽 단추로 클릭한 다음, **시작 프로젝트로 설정**을 클릭합니다.

5. **F5** 키를 눌러 프로젝트를 실행 합니다. 텍스트를 입력하고 단추를 클릭합니다. 레이블은 "입력 했습니다."를 표시 하 고 입력 한 텍스트를 표시 합니다.

     ![결과가 표시된 폼](../data-tools/media/wcf10.png)

## <a name="see-also"></a>참고 항목

- [Windows Communication Foundation 서비스 및 Visual Studio의 WCF.NET 데이터 서비스](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

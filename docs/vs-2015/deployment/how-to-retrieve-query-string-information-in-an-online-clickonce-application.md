---
title: '방법: 온라인 ClickOnce 응용 프로그램에서 쿼리 문자열 정보 검색 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 588ff95f90c6d85526dfe931e8f0b8ab439d9b94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697587"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>방법: 온라인 ClickOnce 애플리케이션에서 쿼리 문자열 정보 검색
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*쿼리 문자열* 은 임의의 정보를 *name=value*형식으로 포함하는, 물음표(?)로 시작되는 URL의 일부입니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 에 호스트하는 `WindowsApp1` 이라는 이름의 `servername`애플리케이션이 있으며, 애플리케이션이 시작될 때 `username` 변수에 대해 값을 전달하려 한다고 가정해 보겠습니다. URL은 다음과 같습니다.  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 다음 두 절차는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 사용하여 쿼리 문자열 정보를 얻는 방법을 보여 줍니다.  
  
> [!NOTE]
> 파일 공유나 로컬 파일 시스템이 아니라 HTTP를 사용하여 애플리케이션이 시작될 때 쿼리 문자열에서만 정보를 전달할 수 있습니다.  
  
 첫 번째 절차에서는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션이 시작될 때 작은 코드 부분을 사용하여 이러한 값을 읽는 방법을 보여 줍니다.  
  
 다음 절차에서는 쿼리 문자열 매개 변수를 수용할 수 있도록 MageUI.exe를 사용하여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 구성하는 방법을 보여 줍니다. 애플리케이션을 게시할 때마다 이 작업을 수행해야 합니다.  
  
> [!NOTE]
> 이 기능의 사용 여부를 결정하기 전에 이 항목의 뒷부분에 나오는 "보안" 섹션을 참조하세요.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Mage.exe 또는 MageUI.exe를 사용 하 여 배포를 만드는 방법에 대 한 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)를 참조 하세요.  
  
> [!NOTE]
> .NET Framework 3.5 SP1부터 명령줄 인수를 오프라인 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 전달할 수 있습니다. 애플리케이션에 인수를 제공하려는 경우 .APPREF-MS 확장명의 바로 가기 파일에 매개 변수를 전달할 수 있습니다.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>ClickOnce 애플리케이션에서 쿼리 문자열 정보를 가져오려면  
  
1. 프로젝트에 다음 코드를 추가합니다. 이 코드가 작동하려면 System.Web에 대한 참조가 필요하며 System.Web, System.Collections.Specialized 및 System.Deployment.Application에 대해 `using` 또는 `Imports` 문을 추가해야 합니다.  
  
     [!code-csharp[ClickOnceQueryString#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs#1)]
     [!code-vb[ClickOnceQueryString#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb#1)]  
  
2. 이름으로 인덱싱된 쿼리 문자열 매개 변수의 <xref:System.Collections.DictionaryBase.Dictionary%2A> 를 검색하려면 전에 정의한 함수를 호출합니다.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>MageUI.exe를 사용하여 ClickOnce 애플리케이션에서 쿼리 문자열이 전달되도록 하려면  
  
1. .NET 명령 프롬프트를 열고 다음을 입력합니다.  
  
    ```  
    MageUI  
    ```  
  
2. **파일** 메뉴에서 **열기**를 선택하고 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 대한 배포 매니페스트를 엽니다( `.application` 확장명으로 끝나는 파일).  
  
3. 왼쪽 탐색 창에서 **배포 옵션** 패널을 선택하고, **애플리케이션으로 URL 매개 변수가 전달되도록 허용** 확인란을 선택합니다.  
  
4. **파일** 메뉴에서 **저장**을 선택합니다.  
  
> [!NOTE]
> 또는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서 쿼리 문자열이 전달되도록 할 수 있습니다. **프로젝트 속성** 을 열고 **게시**탭을 선택하고 **옵션** 단추를 클릭한 다음 **매니페스트** 를 선택하여 **애플리케이션으로 URL 매개 변수가 전달되도록 허용**확인란을 선택합니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 쿼리 문자열 매개 변수를 사용할 경우 애플리케이션의 설치 및 활성화 방법에 대해 신중해야 합니다. 웹 또는 네트워크 공유에서 애플리케이션을 사용자 컴퓨터에 설치하도록 구성한 경우 사용자는 URL을 통해 애플리케이션을 한 번만 활성화할 가능성이 있습니다. 그런 다음 사용자는 대개 **시작** 메뉴의 바로 가기를 사용하여 애플리케이션을 활성화합니다. 그 결과 애플리케이션은 수명 동안 쿼리 문자열 인수를 한 번만 수신하도록 보장됩니다. 나중에 사용할 수 있도록 사용자의 컴퓨터에 이러한 인수를 저장하기로 선택한 경우 안전한 방식으로 저장해야 합니다.  
  
 온라인 전용인 애플리케이션은 항상 URL을 통해 활성화됩니다. 그러나 이 경우, 쿼리 문자열 매개 변수가 누락되거나 손상되더라도 제대로 작동하도록 애플리케이션을 작성해야 합니다.  
  
## <a name="net-framework-security"></a>.NET Framework 보안  
 악의적인 문자의 입력을 사용 전에 지우려는 경우에만 URL 매개 변수가 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 전달되도록 하세요. 예를 들어 따옴표, 슬래시 또는 세미콜론이 포함된 문자열은 데이터베이스에 대한 SQL 쿼리에서 필터링되지 않고 사용될 경우 임의의 데이터 작업을 수행할 수 있습니다. 쿼리 문자열 보안에 대한 자세한 내용은 [Script Exploits Overview](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)

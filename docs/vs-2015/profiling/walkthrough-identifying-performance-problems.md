---
title: '연습: 성능 문제 확인 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance, analyzing
- profiling applications, walkthroughs
ms.assetid: 36f6f123-0c14-4763-99c3-bd60ecb95b87
caps.latest.revision: 58
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bc4135b9b861a460295c67c576405edd5c63211
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695010"
---
# <a name="walkthrough-identifying-performance-problems"></a>연습: 성능 문제 확인
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 성능 문제를 파악하도록 애플리케이션을 프로파일링하는 방법을 설명합니다.  
  
 이 연습에서는 관리되는 애플리케이션을 프로파일링하고 샘플링 및 계측을 사용하여 애플리케이션의 성능 문제를 격리 및 식별하는 과정을 단계별로 진행합니다.  
  
 이 연습에서는 다음과 같은 단계를 수행합니다.  
  
- 샘플링 방법을 사용하여 애플리케이션 프로파일링  
  
- 성능 문제를 찾아서 해결하기 위해 샘플링된 프로파일링 결과 분석  
  
- 계측 방법을 사용하여 애플리케이션 프로파일링  
  
- 성능 문제를 찾아서 해결하기 위해 계측된 프로파일링 결과 분석  
  
## <a name="prerequisites"></a>사전 요구 사항  
  
- C#에 대한 중간 정도의 이해도  
  
- [PeopleTrax 샘플](../profiling/peopletrax-sample-profiling-tools.md)의 복사본  
  
  프로파일링을 통해 제공되는 정보를 사용하려면 디버깅 기호 정보를 준비해 두는 것이 가장 좋습니다.  
  
## <a name="profiling-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 프로파일링  
 샘플링은 해당하는 프로세스를 주기적으로 폴링하여 활성 함수를 확인하는 프로파일링 방법입니다. 결과 데이터는 프로세스를 샘플링할 때 확인하려는 함수가 호출 스택 위에 있었던 빈도에 해당하는 수를 제공합니다.  
  
#### <a name="to-profile-an-application-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 애플리케이션을 프로파일링하려면  
  
1. 관리자 권한으로 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]을 엽니다. 프로파일링 시에는 관리자 권한으로 Visual Studio를 실행해야 합니다.  
  
2. PeopleTrax 솔루션을 엽니다.  
  
     이제 PeopleTrax 솔루션이 솔루션 탐색기에 표시됩니다.  
  
3. 프로젝트 구성 설정을 **릴리스**로 설정합니다.  
  
     애플리케이션에서 성능 문제를 검색하려면 릴리스 빌드를 사용해야 합니다. 디버그 빌드에는 성능을 저하시킬 수 있으며 성능 문제를 정확하게 보여 주지 않는 추가 정보가 컴파일되어 있으므로 프로파일링에는 릴리스 빌드를 사용하는 것이 좋습니다.  
  
4. **분석** 메뉴에서 **성능 마법사 시작**을 클릭합니다.  
  
     성능 마법사가 나타납니다.  
  
5. **CPU 샘플링(권장)** 이 선택되어 있는지 확인하고 **다음**을 클릭합니다.  
  
6. **다음 애플리케이션 중 프로파일링할 대상을 선택하십시오.** 에서 PeopleTrax를 선택하고 **다음**을 클릭합니다.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서 프로젝트를 빌드하고 애플리케이션 프로파일링을 시작합니다. **PeopleTrax** 애플리케이션 창이 나타납니다.  
  
7. **사용자 가져오기**를 클릭합니다.  
  
8. **ExportData**를 클릭합니다.  
  
     메모장이 열리고 **PeopleTrax**에서 내보낸 데이터가 들어 있는 새 파일이 표시됩니다.  
  
9. 메모장을 닫은 다음 **PeopleTrax** 애플리케이션을 닫습니다.  
  
     프로파일러는 프로파일링 데이터(\*.vsp) 파일을 생성하고, 성능 탐색기 창의 보고서 섹션에 파일 이름을 나열하고, [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]의 주 창에서 데이터 파일의 **요약** 뷰를 자동으로 로드합니다.  
  
#### <a name="to-analyze-sampled-profiling-results"></a>샘플링된 프로파일링 결과를 분석하려면  
  
1. 요약 뷰에는 프로파일링 실행 과정 동안의 CPU 사용률 시간 표시 막대, 가장 활발하게 사용된 애플리케이션 호출 트리의 분기를 나타내는 **실행 부하 과다 경로** 목록, 그리고 자체 함수 본문에서 코드를 실행하는 동안 가장 많이 샘플링된 함수를 보여 주는 **개별 작업이 가장 많은 함수**의 목록이 표시됩니다.  
  
     **실행 부하 과다 경로** 목록을 조사하여 목록 끝부분에 있는 PeopleTrax 함수가 PeopleNS.People.GetNames 메서드임을 확인합니다. 이 메서드의 위치를 분석하면 효율적입니다. 함수 이름을 클릭하여 **함수 정보** 뷰에서 GetNames의 정보를 표시합니다.  
  
2. **함수 정보** 뷰에느 두 개의 창이 있습니다. 비용 배분 창에서는 함수가 수행한 작업, 해당 함수가 호출한 함수가 수행한 작업, 그리고 샘플링된 인스턴스 수에서 함수를 호출한 함수가 차지하는 비율을 보여 주는 그래픽 뷰가 제공됩니다. 함수 이름을 클릭하면 뷰에서 포커스가 설정된 함수를 변경할 수 있습니다. 예를 들어 PeopleNS.People.GetPeople을 클릭하여 GetPeople을 선택된 함수로 설정할 수 있습니다.  
  
     **함수 코드 뷰** 창에는 함수의 소스 코드(사용 가능한 경우)가 표시되며, 선택한 함수에서 가장 비용이 높은 줄이 강조 표시됩니다. GetNames를 선택하면 이 함수가 애플리케이션 리소스에서 문자열을 읽은 다음 <xref:System.IO.StringReader>를 사용하여 문자열의 각 줄을 <xref:System.Collections.ArrayList>에 추가함을 확인할 수 있습니다. 이 함수를 최적화하는 확실한 방법은 없습니다.  
  
3. GetNames의 호출자는 PeopleNS.People.GetPeople뿐이므로 비용 배분 창에서 GetPeople을 클릭하여 해당 코드를 조사합니다. 이 메서드는 GetNames에 의해 생성된 사용자 및 회사 이름에서 PersonInformationNS.PersonInformation 개체의 <xref:System.Collections.ArrayList>를 반환합니다. 그러나 GetNames는 PersonInformation 개체를 만들 때마다 두 번 호출됩니다. 메서드 시작 시에 목록을 한 번만 만들고, PersonInformation 만들기 루프 중에 해당 목록으로 인덱싱하면 메서드를 쉽게 최적화할 수 있습니다.  
  
4. 샘플 애플리케이션 코드에서는 GetPeople의 대체 버전이 제공되며, 빌드 속성에 조건부 컴파일 기호를 추가하면 최적화된 함수를 호출할 수 있습니다. 솔루션 탐색기 창에서 People 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다. 속성 페이지 메뉴에서 **빌드**를 클릭한 다음 조건부 컴파일 기호 텍스트 상자에 **OPTIMIZED_GETPEOPLE**을 입력합니다. 다음 빌드에서 원래 메서드가 최적화된 버전의 GetPeople로 바뀝니다.  
  
5. 성능 세션을 다시 실행합니다. 성능 탐색기 도구 모음에서 **프로파일링 시작**을 클릭합니다. **사용자 가져오기**, **데이터 내보내기**를 차례로 클릭합니다. 표시되는 메모장 창을 닫고 PeopleTrax 애플리케이션을 닫습니다.  
  
     새 프로파일링 데이터 파일이 생성되고 새 데이터의 **요약** 뷰가 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 주 창에 표시됩니다.  
  
6. 두 프로파일링 실행을 비교하려면 성능 탐색기에서 두 데이터 파일을 선택하고 마우스 오른쪽 단추로 클릭한 다음 **성능 보고서 비교**를 클릭합니다. 그러면 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 주 창에 비교 보고서 창이 나타납니다. **델타** 열에 함수의 성능 값이 이전 **기준** 값과 이후 **비교** 값으로 변경된 내용이 표시됩니다. **열** 드롭다운 목록에서 비교할 값을 선택할 수 있습니다. **포괄 샘플 비율(%)** 을 선택합니다.  
  
     GetPeople 및 GetNames 메서드의 성능이 크게 향상되었음을 확인할 수 있습니다.  
  
## <a name="profiling-by-using-the-instrumentation-method"></a>계측 방법을 사용하여 프로파일링  
 계측은 프로파일러가 프로브 함수를 프로파일링된 이진 파일의 특수하게 빌드된 버전에 삽입하는 프로파일링 방법입니다. 프로브는 계측된 모듈에서 함수의 진입 및 종료 시에, 그리고 해당 함수의 모든 호출 사이트에서 타이밍 정보를 수집합니다. 계측 프로세스는 네트워크에서 통신하고 디스크에 쓰는 등의 입/출력 작업과 관련된 문제를 조사하는 데 유용합니다. 계측에서는 샘플링에 비해 더 자세한 정보를 제공하지만, 프로세스 실행이 보다 주입식이며 오버헤드가 더 많이 발생합니다. 계측된 이진 파일도 디버그 또는 릴리스 이진 파일보다 더 크므로 배포할 수 없습니다.  
  
 연습의 이 섹션에서는 계측 방법을 사용하여 앞에서 프로파일링한 PeopleTrax 애플리케이션에서 최적화할 수 있는 코드를 추가로 검색합니다. 그리고 요약 뷰 시간 표시 막대의 필터를 사용하여 사용자 목록이 메모장 파일에 작성되는 프로파일링된 애플리케이션의 데이터 내보내기 시나리오에 대한 분석을 중점적으로 수행합니다.  
  
#### <a name="to-profile-an-existing-application-by-using-the-instrumentation-method"></a>계측 방법을 사용하여 기존 애플리케이션을 프로파일링하려면  
  
1. 필요한 경우 Visual Studio에서 PeopleTrax 애플리케이션을 엽니다.  
  
     관리자 권한으로 Visual Studio를 실행 중이며, 솔루션의 빌드 구성이 **릴리스**로 설정되어 있는지 확인합니다.  
  
2. 성능 탐색기에서 **계측**을 클릭합니다.  
  
3. 성능 탐색기 도구 모음에서 **프로 파일링 시작**을 클릭합니다.  
  
     프로파일러에서 프로젝트를 빌드하고 애플리케이션 프로파일링을 시작합니다. PeopleTrax 애플리케이션 창이 나타납니다.  
  
4. **사용자 가져오기**를 클릭합니다.  
  
     PeopleTrax 데이터 표에 데이터가 채워집니다.  
  
5. 10초 정도 기다렸다가 **데이터 내보내기**를 클릭합니다.  
  
     **메모장**이 시작되고 PeopleTrax의 사용자 목록이 들어 있는 새 파일이 표시됩니다. 잠시 기다리면 필터링을 위한 데이터 내보내기 절차를 보다 쉽게 확인할 수 있습니다.  
  
6. **메모장**을 닫은 다음 **PeopleTrax** 응용 프로그램을 닫습니다.  
  
     [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에서 성능 세션 보고서(*.vsp)를 생성합니다.  
  
#### <a name="to-analyze-instrumented-profiling-results"></a>계측된 프로파일링 결과를 분석하려면  
  
1. 보고서 **요약** 뷰의 시간 표시 막대 그래프에는 프로파일링 실행 과정 동안 프로그램의 CPU 사용률이 표시됩니다. 데이터 내보내기 작업의 경우 그래프 오른쪽의 CPU 사용률이 크게 높아지거나 안정적으로 유지됩니다. 성능 세션을 필터링하여 내보내기 작업에서 수집된 데이터만 표시하고 분석할 수 있습니다. 데이터 내보내기 작업이 시작된 그래프상의 지점 왼쪽을 클릭합니다. 해당 작업의 오른쪽을 다시 클릭합니다. 그런 다음 시간 표시 막대 오른쪽의 링크 목록에서 **선택 필터**를 클릭합니다.  
  
    **실행 부하 과다 경로** 트리에는 PeopleTrax.Form1.ExportData 메서드에 의해 호출된 <xref:System.String.Concat%2A> 메서드가 작업 시간 중 대부분을 사용함이 표시됩니다. **System.String.Concat**는 **개별 작업이 가장 많은 함수** 목록에서도 맨 위에 있으므로 이 함수에 소요되는 시간을 줄이는 것이 최적화에서 중요한 작업일 가능성이 높습니다.  
  
2. 요약 테이블 중 하나에서 **System.String.Concat**를 두 번 클릭하여 함수 정보 뷰에서 자세한 내용을 확인합니다.  
  
3. Concat를 호출하는 메서드는 PeopleTrax.Form1.ExportData뿐임을 확인할 수 있습니다. **호출 함수**에서 **PeopleTrax.Form1.ExportData**를 클릭하여 함수 정보 뷰의 대상으로 해당 메서드를 선택합니다.  
  
4. 함수 코드 뷰 창에서 메서드를 검사합니다. **System.String.Concat**에 대한 리터럴 호출은 없습니다. 대신 += 피연산자는 여러 번 사용됩니다. 컴파일러는 이 피연산자를 **System.String.Concat** 호출로 바꿉니다. .NET Framework에서는 문자열을 수정하면 새 문자열이 할당됩니다. .NET Framework에는 문자열 연결용으로 최적화된 <xref:System.Text.StringBuilder> 클래스가 포함되어 있습니다.  
  
5. 이 문제 영역을 최적화된 코드로 바꾸려면 PeoplexTrax 프로젝트의 조건부 컴파일 기호로 OPTIMIZED_EXPORTDATA를 추가합니다.  
  
6. 솔루션 탐색기에서 PeopleTrax 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  
  
    PeopleTrax 프로젝트 속성 폼이 나타납니다.  
  
7. **빌드** 탭을 클릭합니다.  
  
8. **조건부 컴파일 기호** 텍스트 상자에 **OPTIMIZED_EXPORTDATA**를 입력합니다.  
  
9. 프로젝트 속성 폼을 닫고 메시지가 표시되면 **모두 저장**을 선택합니다.  
  
   애플리케이션을 다시 실행하면 성능이 현저히 향상 되었음을 확인할 수 있습니다. 성능이 사용자가 체감할 수 있도록 향상되더라도 프로파일링 세션을 다시 실행하는 것이 좋습니다. 첫 번째 문제로 인해 다른 문제는 명확하게 드러나지 않았을 수도 있으므로, 문제를 해결한 후에 데이터를 검토해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [간단한](../profiling/overviews-performance-tools.md)   
 [시작 하기](../profiling/getting-started-with-performance-tools.md)   
 [/Z7,/Zi,/ZI (디버그 정보 형식)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)

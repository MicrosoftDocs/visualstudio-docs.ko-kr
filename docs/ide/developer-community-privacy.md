---
title: 문제 보고서에 대한 개인 데이터
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f5b8e2d65454d75c08d3efc26af2fd93b22153b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284804"
---
# <a name="developer-community-data-privacy"></a>개발자 커뮤니티 데이터 개인 정보

기본적으로 [개발자 커뮤니티](https://developercommunity.visualstudio.com/)의 문제 보고서에 있는 모든 정보(설명 및 응답 포함)는 공개적으로 표시됩니다. 이를 통해 전체 커뮤니티에서 다른 사용자가 발견한 문제점, 솔루션 및 해결 방법을 볼 수 있기 때문에 유용합니다. 그러나 데이터 또는 ID의 개인 정보에 대한 우려가 있는 경우 옵션이 있습니다.

## <a name="identity-privacy"></a>ID 개인 정보

신원 노출이 우려되는 경우 자신의 세부 정보를 공개하지 않는 [새로운 Microsoft 계정을 만듭니다](https://signup.live.com/). 이 계정을 사용하여 보고서를 만듭니다.

## <a name="data-privacy"></a>데이터 개인 정보

데이터 개인 정보에 대한 우려가 있는 경우 항상 공개되는 초기 보고서의 제목이나 내용에 비공개 내용을 넣지 마십시오. 대신 보고서를 만든 다음, 별도의 주석으로 개인 세부 정보를 보냅니다. 문제 보고서가 작성되면 회신과 첨부 파일을 볼 수 있는 사용자를 지정할 수 있습니다.

1. 작성한 보고서에서 **주석 추가**를 선택하여 문제에 대한 개인 설명을 작성합니다.

2. 회신 편집기에서 **제출** 및 **취소** 단추 아래의 컨트롤을 사용하여 회신 대상을 지정합니다. **중재자 및 원래 게시자가 볼 수 있음**을 선택하여 Microsoft 직원과 본인만 볼 수 있도록 제한합니다.

   ![개발자 커뮤니티의 개인 정보 제어](media/developer-community-privacy-control.png)

   지정한 사람만이 주석과 그 안에 포함된 이미지, 링크 또는 코드를 볼 수 있습니다. 주석 아래의 모든 회신은 원래 주석과 동일한 공개 설정을 가집니다. 이는 회신의 개인 정보 컨트롤이 공개 제한 상태를 올바르게 표시하지 않는 경우에도 마찬가지입니다.

3. 재현에 필요한 설명 및 기타 정보, 이미지 및 첨부 파일을 추가합니다. **제출** 단추를 선택하여 이 정보를 비공개로 보냅니다.

   > [!NOTE]
   > Developer Community 웹 사이트에서는 첨부 파일이 크기는 최대 2GB, 개수는 최대 10개로 제한됩니다. 더 큰 파일을 업로드해야 하는 경우 새 문제 보고서를 제출하거나 개인 주석으로 Microsoft 직원에게 업로드 URL을 요청할 수 있습니다.
   > Microsoft에서 문제를 종결하면 90일 후에 연결된 첨부 파일이 삭제됩니다.

개인 정보를 보호하고 중요한 정보를 공개하지 않으려면 공개 제한적 주석에 따라 회신함으로써 Microsoft와의 모든 상호 작용을 유지하세요. 기타 다른 주석에 대한 회신은 실수로 중요한 정보가 누설될 수 있습니다.

## <a name="data-we-collect"></a>데이터 수집

Visual Studio 설치 관리자에서 **문제 보고**가 시작되면 최신 설치 로그를 수집합니다.

Visual Studio에서 **문제 보고**가 시작되면 다음 유형의 데이터 중 하나 이상을 수집합니다.

- 이벤트 로그의 Watson 및 .NET 엔트리

- Visual Studio 메모리 내 활동 로그 파일

- PerfWatson 파일(Watson 컬렉션이 사용하도록 설정된 경우)

- LiveShare 로그 파일(있는 경우)

- Xamarin 로그 파일(있는 경우)

- Nuget 로그 파일(있는 경우)

- 웹 디버거 로그 파일(있는 경우)

- 서비스 허브 로그 및 MEF 오류 로그(있는 경우)

- Python 로그(있는 경우)

- Windows Forms 로그(있는 경우)

- 스크린샷(포함하도록 선택한 경우)

- 다음을 포함하는 데이터 기록(기록을 포함하도록 선택한 경우):

  - 문제를 재현하기 위한 단계

  - ETL 추적 파일

  - 덤프 파일

> [!NOTE]
> 로그 파일, 스크린샷 및 데이터 기록을 전송하면 Microsoft에서 문제를 이해하고 대응하는 능력이 현저하게 향상됩니다.  따라서 이러한 항목을 포함하는 것이 좋습니다. 개인 정보를 보호하기 위해 첨부된 로그 파일, 스크린샷 및 데이터 기록은 문제 보고서와 함께 제출하여 사용 권한을 제공하는 경우에만 Microsoft로 전송됩니다. 보고서를 제출하기 전에 ‘문제 보고’ 창의 ‘요약’ 단계에서 포함된 파일을 확인할 수 있습니다. ‘요약’ 단계에서 ‘시스템 로그 연결’을 선택 취소하여 보고서에서 시스템 로그 파일을 제외할 수 있습니다. 참조용으로 다음 스크린샷을 참조하세요. 
  > ![문제 보고 - 수집된 로그 요약](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>참조

- [Visual Studio의 문제를 보고하는 방법](how-to-report-a-problem-with-visual-studio.md)
- [C++ 문제 보고서 데이터 개인 정보](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)

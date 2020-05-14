---
title: '방법: 권한 설정 | Microsoft 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling, setting permissions
- security [Visual Studio ALM], setting permissions
- permissions [Visual Studio ALM], profiling
- profiling tools, setting profiling permissions
- performance tools, setting profiling permissions
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c1ab7705c7ab46b07b08b707ce447f37c581036a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774591"
---
# <a name="how-to-set-permissions"></a>방법: 권한 설정

이 문서에서는 컴퓨터 관리자가 해당 컴퓨터에 대한 관리자 권한이 없는 사용자 또는 그룹에 프로파일링에 필요한 보안 권한을 부여하는 방식을 설명합니다.

기본 보안 원칙에 의하면 애플리케이션은 필요한 권한보다 크지 않은 권한으로 실행되어야 합니다. 이 원칙은 사용자에게도 적용됩니다. 사용자가 Administrators 그룹이 아닌 사용자 그룹의 구성원으로 로그온할 때 전체 권한을 가질 수 있다면 사용자에게 관리자 권한을 부여하면 안 됩니다. 첫 번째 절차 "사용자 권한을 가진 사용자 계정을 만들려면"에서는 사용자 그룹의 구성원에 대한 사용자 계정을 만드는 방법을 설명합니다.

사용자 그룹의 구성원은 팀의 다른 구성원과 공유되는 디스크의 폴더 및 파일에 대한 액세스 권한이 필요합니다. 두 번째 절차 "공유된 프로젝트 파일에 대한 액세스 권한을 부여하려면"에서는 이 액세스 권한을 부여하는 방법을 설명합니다.

사용자 그룹의 멤버는 관리자가 해당 사용자에게 프로파일링 도구의 소프트웨어 드라이버에 대한 액세스 권한을 부여한 경우 프로파일링 도구를 실행할 수 있습니다. 마지막 절차 “프로파일링 드라이버에 대한 액세스 권한을 부여하려면"에서는 이 드라이버에 대한 액세스 권한을 부여하는 방법을 설명합니다.

> [!NOTE]
> 이러한 절차의 단계를 수행하려면 관리자 권한이 필요합니다.

## <a name="to-create-a-user-account-that-has-user-permissions"></a>사용자 권한을 가진 사용자 계정을 만들려면

1. **내 컴퓨터**를 마우스 오른쪽 단추로 클릭한 다음 **관리**를 클릭합니다.

     **컴퓨터 관리** 창이 열립니다.

2. **로컬 사용자 및 그룹**을 확장합니다.

3. **사용자** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 사용자**를 클릭합니다.

     **새 사용자** 대화 상자가 나타납니다.

4. 만들고 있는 사용자 계정의 정보를 사용하여 이 대화 상자의 필드를 입력합니다. 암호를 지정합니다. 선택적으로 사용자에게 다음 로그온 시 암호를 변경하도록 요구하는 확인란을 선택합니다.

5. **만들기**, **닫기**를 차례로 클릭합니다.

     새 사용자가 관리자 권한이 없는 사용자의 그룹인 사용자 그룹에 나타납니다.

## <a name="to-grant-access-to-shared-project-files"></a>공유된 프로젝트 파일에 대한 액세스 권한을 부여하려면

1. Windows 탐색기(또는 파일 탐색기)에서 이 사용자가 사용하고 프로젝트 팀에서 공유하는 프로젝트 파일에 대한 폴더 트리의 루트를 찾습니다.

     이 폴더의 경로는 다음과 같습니다.

    ```cmd
    D:\ourProject
    ```

2. 폴더를 마우스 오른쪽 단추로 클릭하고**속성**을 클릭합니다.

     **\<폴더 이름> 속성** 대화 상자가 나타납니다.

3. **보안** 탭을 클릭합니다.

4. **그룹 또는 사용자 이름** 상자에서 사용자 계정의 이름을 클릭합니다.

5. **\<user name>에 대한 권한** 상자에서 **모든 권한** 확인란을 선택합니다.

6. **확인**을 클릭합니다.

     그러면 5단계에서 선택한 폴더로 시작하는 공유된 폴더 트리에 대한 권한이 사용자에게 부여됩니다.

## <a name="to-grant-access-to-the-profiling-driver"></a>프로파일링 드라이버에 대한 액세스 권한을 부여하려면

1. 관리자 권한으로 명령 프롬프트를 엽니다.

2. 디렉터리를 다음으로 변경합니다.

    ```cmd
    <drive>:\Program Files\Microsoft Visual Studio 14\Team Tools\Performance Tools
    ```

3. 다음 명령 실행:

    ```cmd
    vsperfcmd /admin:driver,start /admin:service,start
    ```

     이 명령은 프로파일링 도구용 드라이버를 설치하고 시작합니다.

     이 명령은 관리자가 아닌 사용자가 사용자 프로세스 공간에서 제공되는 프로파일링 기능을 사용할 수 있도록 프로파일링 드라이버 및 서비스를 시작합니다. 관리자만 명령을 실행할 수 있고 관리자가 아닌 사용자의 경우 명령이 실패합니다.

     이 절차의 최종 단계를 수행하지 않으면 이 단계의 결과는 컴퓨터가 다시 시작된 후 실행 취소됩니다.

4. 명령을 실행하여 컴퓨터에 대한 관리자 권한이 없는 사용자 또는 그룹이 프로파일링 드라이버 기능에 액세스하도록 허용합니다.

    ```cmd
    vsperfcmd /admin:security,allow,<right[,right],<user name|group name>
    ```

     이 명령을 실행하면 프로파일링 도구에 대한 액세스 권한이 \<user name> 또는 \<group name> 계정에 부여됩니다. \<right> 옵션에 따라 사용자가 액세스할 수 있는 프로파일링 기능이 결정됩니다. 이 \<right> 옵션은 다음 값 중 하나 이상일 수 있습니다.

    - FullAccess - 서비스에서 성능 데이터 수집, 프로파일링 및 세션 간 프로파일링을 포함한 모든 프로파일링 방법에 액세스하도록 허용합니다.

    - SampleProfiling - 샘플 프로파일링 방법에 액세스하도록 허용합니다.

    - CrossSession - 프로파일링 서비스에 필요한 세션 간 프로파일링에 액세스하도록 허용합니다.

5. (선택 사항) 컴퓨터가 다시 시작된 후 이전 단계의 결과를 보존하려면 다음 명령을 실행합니다.

    ```cmd
    vsperfcmd /admin:driver,autostart,on
    ```

   이제 지정된 사용자는 로그온한 후 관리자 권한 없이 프로파일링 도구를 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[성능 세션 구성](../profiling/configuring-performance-sessions.md)
[VSPerfCmd](../profiling/vsperfcmd.md)
[프로 파일링 및 Windows Vista 보안](../profiling/profiling-and-windows-vista-security.md)

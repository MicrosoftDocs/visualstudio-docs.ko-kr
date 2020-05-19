---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149201"
---
1. 원격 컴퓨터의 **시작** 메뉴에서 **원격 디버거**를 찾아 시작합니다. 
   
   원격 컴퓨터에 대한 관리 권한이 없는 경우 **원격 디버거** 앱을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 선택합니다. 이와 같은 권한이 있는 경우 정상적으로 시작합니다.

   관리자 권한으로 실행 중인 프로세스에 연결하려는 경우 또는 IIS와 같은 다른 사용자 계정으로 실행 중인 경우에는 **원격 디버거** 앱을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 선택합니다. 자세한 내용은 [Run the remote debugger as an administrator](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator)(관리자 권한으로 원격 디버거 실행)를 참조하세요.
   
1. 처음으로(또는 구성하기 전에) 원격 디버거를 시작할 때는 **원격 디버깅 구성** 대화 상자가 나타납니다.  
  
    ![원격 디버거 구성](../media/remotedebuggerconfwizardpage.png "원격 디버거 구성")  
  
1. Windows 웹 서비스 API가 설치되어 있지 않으면(Windows Server 2008 R2에만 해당) **설치** 단추를 선택합니다.  
  
1. 원격 도구를 사용하려는 네트워크 유형을 하나 이상 선택하세요. 컴퓨터가 도메인을 통해 연결된 경우 첫 번째 항목을 선택해야 합니다. 컴퓨터가 작업 그룹 또는 홈 그룹을 통해 연결된 경우 두 번째 또는 세 번째 항목을 적절하게 선택합니다.  
  
1. **원격 디버깅 구성**을 선택하여 방화벽을 구성하고 원격 디버거를 시작합니다.  
  
1. 구성이 완료되면 **원격 디버거** 창이 나타납니다.
  
    ![원격 디버거 창](../media/remotedebuggerwindow.png "원격 디버거 창")
  
    이제 원격 디버거가 연결을 기다리는 중입니다. 표시된 서버 이름과 포트 번호를 사용하여 Visual Studio에서 원격 연결 구성을 설정합니다.  
  
원격 디버거를 중지하려면 **파일** > **끝내기**를 선택합니다. **시작** 메뉴 또는 명령줄에서 다시 시작할 수 있습니다.  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```

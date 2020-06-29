---
ms.openlocfilehash: b8002d9e911c8d8c07a5aaf5286168e49a374a7c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292074"
---

1. UI에서 업데이트된 구성 옵션을 표시하려면 IIS 관리 콘솔을 닫았다가 다시 엽니다.

2. IIS에서 **기본 웹 사이트**를 마우스 오른쪽 단추로 클릭하고 **배포** > **웹 배포 게시 구성**을 선택합니다.

    ![웹 배포 구성](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

   **배포** 메뉴가 표시되지 않는 경우 이전 섹션을 참조하여 웹 배포가 실행 중인지 확인합니다.

3. **웹 배포 게시 구성** 대화 상자에서 설정을 검토합니다.

4. **설정**을 클릭합니다.

    **결과** 패널에서 출력은 지정된 사용자에게 액세스 권한을 부여했으며, *.publishsettings* 파일 확장명을 가진 파일을 대화 상자에 표시된 위치에 생성했음을 보여줍니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Windows Server 및 IIS 구성에 따라 XML 파일에 다른 값이 표시됩니다. 표시되는 값의 몇 가지 세부 정보는 다음과 같습니다.

   * `publishUrl` 특성에서 참조된 *msdeploy.axd* 파일은 웹 배포에 대해 동적으로 생성된 HTTP 처리기 파일입니다. (테스트 목적으로 `http://myhostname:8172`도 일반적으로 잘 작동합니다.)
   * `publishUrl` 포트는 웹 배포에 대한 기본값인 포트 8172로 설정됩니다.
   * `destinationAppUrl` 포트는 IIS에 대한 기본값인 포트 80으로 설정됩니다.
   * 이후 단계에서 호스트 이름을 사용하여 Visual Studio에서 원격 호스트에 연결할 수 없는 경우 호스트 이름 대신 IP 주소를 테스트합니다.

     > [!NOTE]
     > Azure VM에서 실행되는 IIS에 게시하는 경우 웹 배포 및 IIS 포트를 네트워크 보안 그룹에서 열어야 입니다. 자세한 내용은 [IIS 설치 및 실행](/azure/virtual-machines/windows/quick-create-portal#install-web-server)을 참조하세요.

5. Visual Studio를 실행 중인 컴퓨터에 이 파일을 복사합니다.

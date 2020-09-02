---
title: 방법-ClickOnce 응용 프로그램에 데이터 파일 포함 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7630d1b363afa7caeae361f607f4b73929fbba1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382408"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>방법: ClickOnce 애플리케이션에 데이터 파일 포함
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]설치 하는 각 응용 프로그램에는 응용 프로그램이 자체 데이터를 관리할 수 있는 대상 컴퓨터의 로컬 디스크에 데이터 디렉터리가 할당 됩니다. 데이터 파일에는 텍스트 파일, XML 파일 또는 Microsoft Access 데이터베이스 (*.mdb*) 파일 등 모든 형식의 파일이 포함 될 수 있습니다. 다음 절차에서는 모든 형식의 데이터 파일을 응용 프로그램에 추가 하는 방법을 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

### <a name="to-include-a-data-file-by-using-mageexe"></a>Mage.exe를 사용 하 여 데이터 파일을 포함 하려면

1. 응용 프로그램의 나머지 파일을 사용 하 여 응용 프로그램 디렉터리에 데이터 파일을 추가 합니다.

    일반적으로 응용 프로그램 디렉터리는 배포의 최신 버전 (예: v 1.0.0.0)으로 레이블이 지정 된 디렉터리입니다.

2. 응용 프로그램 매니페스트를 업데이트 하 여 데이터 파일을 나열 합니다.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    이 작업을 수행 하면 응용 프로그램 매니페스트의 파일 목록이 다시 만들어지고 해시 서명도 자동으로 생성 됩니다.

3. 원하는 텍스트 또는 XML 편집기에서 응용 프로그램 매니페스트를 열고 `file` 최근 추가 된 파일에 대 한 요소를 찾습니다.

    이라는 XML 파일을 추가한 경우 `Data.xml` 파일은 다음 코드 예제와 유사 하 게 표시 됩니다.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. 이 요소에 특성을 추가 하 `type` 고 값으로 지정 `data` 합니다.

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. 키 쌍 또는 인증서를 사용 하 여 응용 프로그램 매니페스트를 다시 서명 하 고 배포 매니페스트에 다시 서명 합니다.

    응용 프로그램 매니페스트의 해시가 변경 되었으므로 배포 매니페스트에 다시 서명 해야 합니다.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>MageUI.exe를 사용 하 여 데이터 파일을 포함 하려면

1. 응용 프로그램의 나머지 파일을 사용 하 여 응용 프로그램 디렉터리에 데이터 파일을 추가 합니다.

2. 일반적으로 응용 프로그램 디렉터리는 배포의 최신 버전 (예: v 1.0.0.0)으로 레이블이 지정 된 디렉터리입니다.

3. **파일** 메뉴에서 **열기** 를 클릭 하 여 응용 프로그램 매니페스트를 엽니다.

4. **파일** 탭을 선택 합니다.

5. 탭의 맨 위에 있는 텍스트 상자에 응용 프로그램 파일이 포함 된 디렉터리를 입력 하 고 **채우기**를 클릭 합니다.

     데이터 파일이 표에 표시 됩니다.

6. 데이터 파일의 **파일 유형** 값을 **데이터**로 설정 합니다.

7. 응용 프로그램 매니페스트를 저장 하 고 파일에 다시 서명 합니다.

     *MageUI.exe* 파일에 다시 서명 하 라는 메시지가 표시 됩니다.

8. 배포 매니페스트 다시 서명

     응용 프로그램 매니페스트의 해시가 변경 되었으므로 배포 매니페스트에 다시 서명 해야 합니다.

## <a name="see-also"></a>참조
- [ClickOnce 애플리케이션의 로컬 및 원격 데이터 액세스](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
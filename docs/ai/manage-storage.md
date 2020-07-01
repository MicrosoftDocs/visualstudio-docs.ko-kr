---
title: 데이터를 업로드할 스토리지 찾아보기
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: 188ebee353261ba49f6677a0f96db68b7e8d46d9
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371614"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>스토리지로 이동하여 데이터 업로드 또는 모델 및 로그 다운로드

원격 머신 또는 Azure 파일 공유에서 모든 스토리지로 이동하여 데이터를 업로드하거나 모델 및 로그를 다운로드할 수 있습니다. 또는 특정 작업에 대한 로그 및 작업 출력에 액세스하려는 경우 작업 브라우저에서도 수행할 수 있습니다.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>원격 컴퓨터 또는 파일 공유에서 모든 데이터에 액세스하려면

1. **서버 탐색기**를 엽니다.
2. 원격 머신 또는 Batch AI 컴퓨팅 컨텍스트를 확장합니다.
3. **스토리지**를 마우스 오른쪽 단추로 클릭한 다음, **찾아보기**를 클릭합니다.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>원격 머신 또는 파일 공유에서 작업 관련 데이터에 액세스하려면

1. [작업 기록](job-details.md)을 엽니다.
2. 작업을 선택합니다.
3. 이러한 중요 로그 파일에 빠르게 액세스하기 위해 **작업 폴더**를 클릭하거나 **StdOut/Stderr**을 클릭합니다.

    ![storage](media/manage-storage/job-workingfolder.png)

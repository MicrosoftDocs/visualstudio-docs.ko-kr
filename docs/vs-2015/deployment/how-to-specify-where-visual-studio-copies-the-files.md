---
title: '방법: Visual Studio 2015에서 파일을 복사 하는 위치 지정 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65226167"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>방법: Visual Studio의 파일 복사 위치 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce를 사용하여 애플리케이션을 게시하는 경우 `Publish Location` 속성에서 애플리케이션 파일 및 매니페스트가 배치되는 위치를 지정합니다. 이 위치는 파일 경로나 FTP 서버에 대한 경로가 될 수 있습니다.

 `Publish Location` 속성은 **프로젝트 디자이너**의 **게시** 페이지나 게시 마법사를 사용하여 지정할 수 있습니다. 자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조 하세요.

> [!NOTE]
> ClickOnce를 사용하여 애플리케이션 버전을 둘 이상 설치하면 이전 애플리케이션 버전이 지정한 게시 위치의 Archive 폴더로 이동합니다. 이러한 방식으로 이전 버전이 보관되므로 설치 디렉터리에 이전 버전의 폴더가 남지 않습니다.

### <a name="to-specify-a-publishing-location"></a>게시 위치를 지정하려면

1. **솔루션 탐색기**에서 프로젝트를 선택한 상태에서 **프로젝트** 메뉴에서 **속성**을 클릭합니다.

2. **게시** 탭을 클릭합니다.

3. **게시 위치** 필드에 다음 형식 중 하나를 사용하여 게시 위치를 입력합니다.

   - 파일 공유 또는 디스크 경로에 게시 하려면 UNC 경로 ( \\ \Server\ApplicationName) 또는 파일 경로 (C:\Deploy\ApplicationName)를 사용 하 여 경로를 입력 합니다.

   - FTP 서버에 게시 하려면 ftp:/ftp.microsoft.com/ApplicationName 형식을 사용 하 여 경로를 입력 \/ 합니다.

     찾아보기 (**...**) 단추가 작동 하려면 **게시 위치** 상자에 텍스트가 있어야 합니다.

## <a name="see-also"></a>관련 항목
 [Clickonce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md) [방법: 게시 마법사를 사용 하 여 Clickonce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

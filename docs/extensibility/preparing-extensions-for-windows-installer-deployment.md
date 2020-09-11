---
title: Windows Installer 배포용 확장 준비 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0084cfc6c08db1c1d15013362a186fec175b4ee4
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012219"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Windows Installer 배포를 위한 확장 준비
Windows Installer 패키지 (MSI)를 사용 하 여 VSIX 패키지를 배포할 수 없습니다. 그러나 MSI 배포에 대 한 VSIX 패키지의 내용을 추출할 수 있습니다. 이 문서에서는 기본 출력이 설치 프로젝트에 포함 될 VSIX 패키지인 프로젝트를 준비 하는 방법을 보여 줍니다.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer 배포를 위한 확장 프로젝트 준비
 설치 프로젝트에 추가 하기 전에 새 확장 프로젝트에서 이러한 단계를 수행 합니다.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows Installer 배포를 위한 확장 프로젝트를 준비 하려면

1. VSIX 매니페스트를 포함 하는 VSPackage, MEF 구성 요소, 편집기 장식 또는 기타 확장성 프로젝트 형식을 만듭니다.

2. 코드 편집기에서 VSIX 매니페스트를 엽니다.

3. `InstalledByMsi`VSIX 매니페스트의 요소를로 설정 `true` 합니다. VSIX 매니페스트에 대 한 자세한 내용은 [vsix 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)를 참조 하세요.

     그러면 VSIX 설치 관리자가 구성 요소를 설치 하려고 시도 하지 않습니다.

4. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 클릭 합니다.

5. **VSIX** 탭을 선택 합니다.

6. **다음 위치에 VSIX 콘텐츠 복사** 확인란을 선택 하 고 설치 프로젝트에서 파일을 선택 하는 경로를 입력 합니다.

## <a name="extract-files-from-an-existing-vsix-package"></a>기존 VSIX 패키지에서 파일 추출
 원본 파일이 없는 경우이 단계를 수행 하 여 기존 VSIX 패키지의 내용을 설치 프로젝트에 추가 합니다.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>기존 VSIX 패키지에서 파일을 추출 하려면

1. 이름을 바꿉니다 *. * *filename.zip*에 대 한 확장명을 포함 하는 vsix 파일입니다 *.*

2. *.Zip* 파일의 내용을 디렉터리에 복사 합니다.

3. 디렉터리에서 *[Content_types] .xml* 파일을 삭제 합니다.

4. 이전 절차에서와 같이 VSIX 매니페스트를 편집 합니다.

5. 나머지 파일을 설치 프로젝트에 추가 합니다.

## <a name="see-also"></a>참고 항목
- [Visual Studio 설치 관리자 배포](/previous-versions/2kt85ked(v=vs.120))
- [연습: 사용자 지정 작업 만들기](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
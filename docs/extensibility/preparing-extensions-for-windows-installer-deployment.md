---
title: Windows 설치 관리자 배포를 위한 확장 준비 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702024"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Windows 설치 관리자 배포에 대 한 확장 준비
MsI(Windows 설치 관리자 패키지)를 사용하여 VSIX 패키지를 배포할 수 없습니다. 그러나 MSI 배포에 대 한 VSIX 패키지의 내용을 추출할 수 있습니다. 이 문서에서는 기본 출력이 설치 프로젝트에 포함하기 위한 VSIX 패키지인 프로젝트를 준비하는 방법을 보여 주며 있습니다.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Windows 설치 관리자 배포를 위한 확장 프로젝트 준비
 설치 프로젝트에 추가하기 전에 새 확장 프로젝트에서 이러한 단계를 수행합니다.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Windows 설치 관리자 배포를 위한 확장 프로젝트를 준비하려면

1. VSPackage, MEF 구성 요소, 편집기 장식 또는 VSIX 매니페스트를 포함하는 기타 확장성 프로젝트 유형을 만듭니다.

2. 코드 편집기에서 VSIX 매니페스트를 엽니다.

3. VSIX `InstalledByMsi` 매니페스트의 요소를 `true`로 설정합니다. VSIX 매니페스트에 대한 자세한 내용은 [VSIX 확장 스키마 2.0 참조를](../extensibility/vsix-extension-schema-2-0-reference.md)참조하십시오.

     이렇게 하면 VSIX 설치 프로그램이 구성 요소를 설치하려고 시도하지 않습니다.

4. **솔루션 탐색기에서** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성을**클릭합니다.

5. **VSIX** 탭을 선택합니다.

6. **VSIX 복사 콘텐츠로 레이블이** 지정된 확인란을 다음 위치로 선택하고 설치 프로젝트에서 파일을 선택할 경로를 입력합니다.

## <a name="extract-files-from-an-existing-vsix-package"></a>기존 VSIX 패키지에서 파일 추출
 원본 파일이 없는 경우 설치 프로젝트에 기존 VSIX 패키지의 내용을 추가하려면 다음 단계를 수행합니다.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>기존 VSIX 패키지에서 파일을 추출하려면

1. 의 이름을 *바꿉니다. * *filename.vsix에서* *filename.zip까지의*확장명을 포함하는 VSIX 파일 .

2. *.zip* 파일의 내용을 디렉터리로 복사합니다.

3. 디렉터리에서 *[Content_types].xml* 파일을 삭제합니다.

4. 이전 절차와 같이 VSIX 매니페스트를 편집합니다.

5. 나머지 파일을 설치 프로젝트에 추가합니다.

## <a name="see-also"></a>참조
- [비주얼 스튜디오 설치 관리자 배포](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [연습: 사용자 지정 작업 만들기](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))

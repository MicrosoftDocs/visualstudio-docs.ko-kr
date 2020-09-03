---
title: 파일 속성, JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719a956558141684c7d755aafb6929f4368482f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657718"
---
# <a name="file-properties-javascript"></a>파일 속성, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

파일 속성을 사용하여 프로젝트 시스템이 파일에 대해 수행해야 하는 작업을 지정할 수 있습니다. 예를 들어 파일 속성을 설정하여 파일을 패키지에 리소스 파일로 추가해야 하는지 여부를 지정할 수 있습니다.

 솔루션 탐색기에서 파일을 선택하고 속성 창에서 해당 속성을 검사할 수 있습니다. JavaScript 파일에는 **출력 디렉터리에 복사**, **패키지 작업**, **파일 이름**, **파일 경로**의 네 가지 속성이 있습니다.

## <a name="file-properties"></a>파일 속성
 이 섹션에서는 JavaScript 파일에 공통적인 속성을 설명합니다.

### <a name="copy-to-output-directory-property"></a>출력 디렉터리에 복사 속성
 이 속성은 선택된 소스 파일이 출력 디렉터리에 복사되는 조건을 지정합니다. 파일이 출력 디렉터리에 전혀 복사되지 않을 경우 **복사 안 함**을 선택합니다. 파일이 출력 디렉터리에 항상 복사될 경우 **항상 복사**를 선택합니다. 파일이 출력 디렉터리에 있는 같은 이름의 기존 파일보다 더 새로울 때만 복사될 경우 **새 버전이면 복사**를 선택합니다.

### <a name="package-action"></a>패키지 작업
 **패키지 작업** 속성은 빌드가 실행될 때 Visual Studio가 파일로 수행하는 작업을 지정합니다. **패키지 작업**에는 다음과 같은 여러 값 중 하나가 포함될 수 있습니다.

- **없음** - 파일이 패키지 매니페스트에 포함되지 않습니다. 예를 들어 추가 정보 파일과 같은 문서가 포함된 텍스트 파일이 있습니다.

- **콘텐츠** - 파일이 패키지 매니페스트에 포함됩니다. 예를 들어 이 설정은 .htm, .js, .css, 이미지, 오디오 또는 비디오 파일의 기본값입니다.

- **매니페스트** – 파일이 패키지 매니페스트에 포함되지 않습니다. 대신에 패키지 매니페스트를 생성할 때 파일이 입력에 사용됩니다. 이 값은 package.appxmanifest 파일의 기본값입니다.

- **리소스** - 파일이 패키지 매니페스트에 포함되지 않습니다. 대신에 파일 콘텐츠가 패키지 매니페스트로 이동되는 PRI(패키지 리소스 인덱스)로 인덱싱됩니다. 일반적으로 리소스 파일에 사용됩니다.

  **패키지 작업**의 기본값은 솔루션에 추가하는 파일의 확장명에 따라 달라집니다.

### <a name="file-name-property"></a>파일 이름 속성
 파일 이름을 읽기 전용 값으로 표시합니다. 파일 이름을 바꾸려면 솔루션 탐색기를 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기**를 선택합니다.

### <a name="full-path-property"></a>전제 경로 속성
 파일의 전체 경로를 읽기 전용 값으로 표시합니다. 파일 경로를 변경하려면 솔루션 탐색기에서 파일을 끌어서 놓을 수 있습니다.

## <a name="reference-file-properties"></a>참조 파일 속성
 이 섹션에서는 [!INCLUDE[win8_app_js](../../includes/win8-app-js-md.md)]에서 참조되는 파일에 공통적인 속성을 설명합니다. 솔루션 탐색기에서 .winmd 파일, SDK 참조, 프로젝트 간 참조 또는 어셈블리 참조와 같은 참조를 선택하면 파일 형식에 따라 다른 속성이 속성 창에 표시될 수 있습니다.

### <a name="culture"></a>문화권
 참조와 연결된 언어를 표시합니다.

### <a name="file-type"></a>파일 유형
 참조의 파일 형식을 표시합니다.

### <a name="file-version"></a>파일 버전
 참조의 파일 버전을 표시합니다.

### <a name="identity"></a>ID
 프로젝트 파일에 저장되는 프로젝트에서 사용되는 참조의 ID를 표시합니다.

### <a name="package"></a>패키지
 참조와 연결된 패키지 매니페스트의 이름을 표시합니다.

### <a name="resolved-path"></a>확인된 경로
 프로젝트에서 사용되는 참조의 경로를 표시합니다.

### <a name="sdk-path"></a>SDK 경로
 참조된 SDK 파일의 경로를 표시합니다.

### <a name="uri"></a>Uri
 파일을 소스 파일로 포함하기 위해 프로젝트의 HTML 또는 JavaScript 파일에 포함해야 하는 URI를 표시합니다.

### <a name="version"></a>버전
 참조의 버전을 표시합니다.

## <a name="see-also"></a>관련 항목
 [NIB: 프로젝트 속성 (Visual Studio)](https://msdn.microsoft.com/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)

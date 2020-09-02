---
title: 소스 제어 플러그 인 용어집 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699906"
---
# <a name="source-control-plug-in-glossary"></a>소스 제어 플러그 인 용어집
소스 제어 플러그 인 SDK 설명서와 관련 된 유용한 용어 및 정의는 다음과 같습니다.

## <a name="definitions"></a>정의
 체크 인 사용자가 작업 복사본을 변경 하는 경우 사용자는 작업 복사본에서 중앙 소스 제어 리포지토리로 변경 내용을 보내야 합니다. 이렇게 하면 다른 사용자가 사용할 수 있는 파일의 새 수정 버전이 만들어집니다. 이 프로세스를 체크 인 이라고 합니다.

 저장소에서 작업 복사본을 요청 하는 작업을 체크 아웃 하 여 해당 리포지토리의 수정 의도를 알려 줍니다. 작업 복사본은 체크 아웃 된 시점의 프로젝트 상태를 반영 합니다.

 클라이언트 소스 코드 제어 시스템을 사용 하는 프로그램입니다. 이 설명서에서는 Visual Studio IDE에 대해 설명 합니다.

 소스 제어 작업을 수행할 때 사용자가 수정 버전에 연결할 수 있는 변경 내용을 설명 하는 메시지를 주석으로 처리 합니다.

 두 사용자가 같은 파일의 동일한 영역에 대 한 변경 내용을 체크 인하 려 할 때 발생 하는 상황을 충돌 합니다. 일반적으로 merge를 수행 해야 합니다.

 디렉터리 클라이언트 쪽 로컬 폴더를 디렉터리 라고 합니다. 사용자가 실제로 변경을 수행 하는 복사본입니다. 지정 된 프로젝트의 작업 복사본이 여러 개 있을 수 있습니다. 일반적으로 각 개발자에 게는 자체 복사본이 있습니다.

 Get 작업 가져오기는 사용자의 작업을 리포지토리 복사본으로 최신 상태로 만듭니다. 체크 아웃과 달리 get은 사용자에 게 최신 복사본만 필요 하지만 변경 하지 않는 경우에 수행 됩니다.

 기록 일반적으로 소스 제어 리포지토리에서 수행 된 모든 체크 아웃, 체크 인, 업데이트, 태그 및 릴리스에 대 한 요약입니다.

 IDE는 일반적으로 Visual Studio 통합 개발 환경을 나타냅니다. 그러나 소스 제어 플러그 인 API를 인식 하는 다른 클라이언트 환경도 참조할 수 있습니다.

 두 개 이상의 소스 코드 파일을 결합 하 여 이전 파일의 모든 기능을 통합 하는 새 파일을 구성 하는 프로세스를 병합 합니다. 이 개념은 둘 이상의 개발자가 동시에 파일에서 작업 하는 버전 제어에서 중요 합니다.

 프로젝트 소스 제어 폴더를 종종 프로젝트 라고 합니다. Visual Studio의 프로젝트 또는 솔루션과 관계가 없습니다.

 플러그 인 소스 제어 플러그 인 API를 구현 하 여 소스 제어 기능을 제공 하는 DLL입니다.

 리포지토리 원본 제어 시스템에서 프로젝트의 전체 수정 기록을 저장 하는 마스터 복사본입니다. 각 프로젝트에는 정확히 하나의 리포지토리가 있습니다.

 수정 파일 또는 파일 집합에 대 한 기록의 커밋된 변경입니다. 수정 버전은 지속적으로 변경 되는 프로젝트에서 하나의 스냅숏입니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)

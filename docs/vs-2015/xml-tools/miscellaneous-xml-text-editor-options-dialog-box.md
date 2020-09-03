---
title: 기타, XML, 텍스트 편집기, 옵션 대화 상자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656242"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>기타, XML, 텍스트 편집기, 옵션 대화 상자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 대화 상자에서는 XML 편집기에 대한 자동 완성 기능 및 스키마 설정을 변경할 수 있습니다. **옵션** 대화 상자는 **도구** 메뉴에서 액세스할 수 있습니다.

> [!NOTE]
> 이러한 설정은 **옵션** 대화 상자에서 **텍스트 편집기** 폴더, **XML** 폴더 및 **기타** 옵션을 선택한 경우에 사용할 수 있습니다.

## <a name="auto-insert"></a>자동 삽입
 **닫는 태그** 자동 완성 설정을 선택 하는 경우 태그를 아직 닫지 않은 경우 오른쪽 꺾쇠 괄호 (>)를 입력 하 여 시작 태그를 닫으면 편집기에서 끝 태그를 자동으로 추가 합니다. 기본 동작입니다.

 빈 요소를 완성하는 작업은 자동 완성 설정의 영향을 받지 않습니다. 빈 요소는 언제든지 백슬래시(/)를 입력하여 자동 완성할 수 있습니다.

 **특성 따옴표** XML 특성을 작성할 때 편집기는 문자를 삽입 `=" "` 하 고 큰따옴표 안에 캐럿 (^)을 배치 합니다.

 기본적으로 선택되어 있습니다.

 **네임 스페이스 선언** 필요할 때마다 편집기에서 네임 스페이스 선언을 자동으로 삽입 합니다.

 기본적으로 선택되어 있습니다.

 **기타 태그 (주석, CDATA)** 주석, CDATA, DOCTYPE, 처리 명령 및 기타 태그가 자동 완성 됩니다.

 기본적으로 선택되어 있습니다.

## <a name="network"></a>네트워크
 **Dtd 및 스키마 자동 다운로드** 스키마 및 Dtd (문서 종류 정의)는 HTTP 위치에서 자동으로 다운로드 됩니다. 이 기능은 자동 프록시 서버 검색 기능을 설정한 상태로 System.Net을 사용합니다.

 기본적으로 선택되어 있습니다.

## <a name="outlining"></a>개요
 **개요 모드로 파일 열기** 파일이 열릴 때 개요 기능을 설정 합니다.

 기본적으로 선택되어 있습니다.

## <a name="caching"></a>캐싱
 **스키마** 스키마 캐시의 위치를 지정 합니다. 찾아보기 단추 (**...**)를 클릭 하면 현재 스키마 캐시 위치에서 **디렉터리 찾아보기** 대화 상자가 열립니다. 다른 디렉터리를 선택 하거나 대화 상자에서 폴더를 선택 하 고 마우스 오른쪽 단추를 클릭 한 다음 **열기** 를 선택 하 여 디렉터리에 있는 항목을 확인할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [Xml 문서 속성, 속성 창](../xml-tools/xml-document-properties-properties-window.md) [Xml 편집기 구성 요소](../xml-tools/xml-editor-components.md)

---
title: Office 프로그래밍의 일반적인 작업
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1b0856d3832d31dd7027b2f264dd0a9cd1d657ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63007329"
---
# <a name="common-tasks-in-office-programming"></a>Office 프로그래밍의 일반적인 작업
  이 항목은 Visual Studio를 사용하여 Office 솔루션을 프로그래밍하는 방법에 대한 다음 범주의 일반적인 질문에 대해 답변을 찾을 수 있도록 설계되었습니다.

- [설치 및 일반 작업](#projects)

- [사용자 인터페이스 사용자 지정 작업](#ui).

- [Excel 자동화 작업](#excel)

- [Word 자동화 작업](#word)

- [데이터 작업](#data).

- [서버 쪽 문서 관리 작업](#server)

- [보안 태스크](#security).

- [배포 작업](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> 설치 및 일반 작업

- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)

- [방법: Office 솔루션 업그레이드](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)

- [방법: Office 주 interop 어셈블리 설치](../vsto/how-to-install-office-primary-interop-assemblies.md)

- [방법: 주 interop 어셈블리를 통한 Office 응용 프로그램 대상](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)

- [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)

- [방법: 코드를 실행 하지 않고 Office 솔루션 열기](../vsto/how-to-open-office-solutions-without-running-code.md)

- [방법: Office 솔루션에 대 한 구성 정보 설정](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)

- [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

- [방법: 추가 기능 사용자 인터페이스 오류 표시](../vsto/how-to-show-add-in-user-interface-errors.md)

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> 사용자 인터페이스 사용자 지정 작업

### <a name="controls-on-documents-and-worksheets"></a>문서 및 워크시트의 컨트롤

- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)

- [방법: 워크시트에 NamedRange 컨트롤 추가](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [방법: 워크시트에 ListObject 컨트롤 추가](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)

- [방법: Word 문서에 콘텐츠 컨트롤 추가](../vsto/how-to-add-content-controls-to-word-documents.md)

- [방법: Word 문서에 책갈피 컨트롤 추가](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

### <a name="task-panes-in-document-level-customizations"></a>문서 수준 사용자 지정의 작업 창

- [방법: Word 문서 또는 Excel 통합 문서에 작업 창 추가](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)

### <a name="task-panes-in-vsto-add-ins"></a>VSTO 추가 기능의 작업창

- [방법: 응용 프로그램에 사용자 지정 작업창 추가](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

### <a name="ribbon-customizations"></a>리본 사용자 지정

- [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)

- [방법: 리본의 탭 위치 변경](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)

- [방법: 기본 제공 탭 사용자 지정](../vsto/how-to-customize-a-built-in-tab.md)

- [방법: Backstage 보기에 컨트롤 추가](../vsto/how-to-add-controls-to-the-backstage-view.md)

- [방법: 리본 디자이너에서 리본 XML로 리본 메뉴 내보내기](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)

### <a name="outlook-form-regions"></a>Outlook 양식 영역

- [방법: Outlook 추가 기능 프로젝트에 양식 영역 추가](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

- [방법: Outlook에서 양식 영역을 표시 하지 못하게](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)합니다.

### <a name="custom-menus"></a>사용자 지정 메뉴

- [방법: 바로 가기 메뉴에 명령 추가](../vsto/how-to-add-commands-to-shortcut-menus.md)

## <a name="excel-automation-tasks"></a><a name="excel"></a> Excel 자동화 작업

- [방법: 프로그래밍 방식으로 워크시트 셀에 문자열 표시](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md)

- [방법: 프로그래밍 방식으로 새 통합 문서 만들기](../vsto/how-to-programmatically-create-new-workbooks.md)

- [방법: 프로그래밍 방식으로 통합 문서 열기](../vsto/how-to-programmatically-open-workbooks.md)

- [방법: 프로그래밍 방식으로 통합 문서 저장](../vsto/how-to-programmatically-save-workbooks.md)

- [방법: 프로그래밍 방식으로 통합 문서 닫기](../vsto/how-to-programmatically-close-workbooks.md)

- [방법: 프로그래밍 방식으로 통합 문서에 새 워크시트 추가](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)

- [방법: 프로그래밍 방식으로 워크시트 숨기기](../vsto/how-to-programmatically-hide-worksheets.md)

- [방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)

- [방법: 프로그래밍 방식으로 통합 문서 보호](../vsto/how-to-programmatically-protect-workbooks.md)

- [방법: 프로그래밍 방식으로 코드에서 워크시트 범위를 참조](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)합니다.

- [방법: 프로그래밍 방식으로 통합 문서의 범위에 스타일 적용](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)

- [방법: 프로그래밍 방식으로 선택한 셀이 포함 된 워크시트 행의 서식 변경](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)

- [방법: 프로그래밍 방식으로 워크시트 범위에서 텍스트 검색](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)

- [방법: 프로그래밍 방식으로 워크시트 인쇄](../vsto/how-to-programmatically-print-worksheets.md)

- [방법: 프로그래밍 방식으로 Excel 계산 실행](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)

- [방법: 프로그래밍 방식으로 워크시트의 데이터 정렬](../vsto/how-to-programmatically-sort-data-in-worksheets.md)

## <a name="word-automation-tasks"></a><a name="word"></a> Word 자동화 작업

- [방법: 프로그래밍 방식으로 새 문서 만들기](../vsto/how-to-programmatically-create-new-documents.md)

- [방법: 프로그래밍 방식으로 기존 문서 열기](../vsto/how-to-programmatically-open-existing-documents.md)

- [방법: 프로그래밍 방식으로 문서 저장](../vsto/how-to-programmatically-save-documents.md)

- [방법: 프로그래밍 방식으로 문서 닫기](../vsto/how-to-programmatically-close-documents.md)

- [방법: 프로그래밍 방식으로 Word 문서에 텍스트 삽입](../vsto/how-to-programmatically-insert-text-into-word-documents.md)

- [방법: 프로그래밍 방식으로 문서에서 범위 정의 및 선택](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)

- [방법: 프로그래밍 방식으로 Word 문서의 범위 다시 설정](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)

- [방법: 프로그래밍 방식으로 문서의 텍스트 서식 지정](../vsto/how-to-programmatically-format-text-in-documents.md)

- [방법: Word 문서에 XMLNode 컨트롤 추가](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [방법: 프로그래밍 방식으로 책갈피 텍스트 업데이트](../vsto/how-to-programmatically-update-bookmark-text.md)

- [방법: 프로그래밍 방식으로 문서에서 텍스트 검색 및 바꾸기](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)

- [방법: 프로그래밍 방식으로 문서 인쇄](../vsto/how-to-programmatically-print-documents.md)

- [방법: 프로그래밍 방식으로 Word 표 만들기](../vsto/how-to-programmatically-create-word-tables.md)

- [방법: 프로그래밍 방식으로 Word 표에 행 및 열 추가](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)

- [방법: 프로그래밍 방식으로 문서의 문자 수 계산](../vsto/how-to-programmatically-count-characters-in-documents.md)

## <a name="data-tasks"></a><a name="data"></a> 데이터 작업

### <a name="data-bound-controls"></a>데이터 바인딩된 컨트롤

- [방법: 데이터베이스의 데이터로 워크시트 채우기](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [방법: 서비스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-services.md)

- [방법: 개체의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [방법: 서비스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-services.md)

- [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)

### <a name="cached-data-in-document-level-solutions"></a>문서 수준 솔루션의 캐시 된 데이터

- [방법: 오프 라인 이나 서버에서 사용할 데이터를 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)합니다.

- [방법: Office 문서에서 프로그래밍 방식으로 데이터 소스 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)

- [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)

### <a name="custom-xml-data"></a>사용자 지정 XML 데이터

- [방법: 문서 수준 사용자 지정에 사용자 지정 XML 부분 추가](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [방법: VSTO 추가 기능을 사용 하 여 문서에 사용자 지정 XML 부분 추가](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

## <a name="server-side-document-management-tasks"></a><a name="server"></a> 서버 쪽 문서 관리 작업

- [방법: 문서에서 관리 코드 확장 제거](../vsto/how-to-remove-managed-code-extensions-from-documents.md)

- [방법: 문서에 관리 코드 확장명 연결](../vsto/how-to-attach-managed-code-extensions-to-documents.md)

## <a name="security-tasks"></a><a name="security"></a> 보안 작업

- [방법: Office 솔루션에 서명](../vsto/how-to-sign-office-solutions.md)합니다.

## <a name="deployment-tasks"></a><a name="deployment"></a> 배포 작업

- [방법: ClickOnce를 사용 하 여 Office 솔루션 게시](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)

- [방법: ClickOnce를 사용 하 여 SharePoint 서버에 문서 수준 Office 솔루션 게시](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)

- [방법: ClickOnce Office 솔루션 설치](https://msdn.microsoft.com/14702f48-9161-4190-994c-78211fe18065).

- [방법: 최종 사용자 컴퓨터에 Office 솔루션 실행을 위한 필수 구성 요소 설치](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)

- [방법: Office 솔루션 배포를 위해 IIS 준비](https://msdn.microsoft.com/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4)

- [방법: 배포 된 Office 솔루션 업데이트](https://msdn.microsoft.com/be96db53-b6ea-46ab-b8d9-b76b098b3b13).

- [방법: Office 솔루션의 설치 경로 변경](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)

## <a name="see-also"></a>추가 정보
- [Visual Studio에서 Office 개발 &#40;시작&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office 응용 프로그램 및 프로젝트 형식에 따라 사용 가능한 기능](../vsto/features-available-by-office-application-and-project-type.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)

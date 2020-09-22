---
title: 로컬 & 원격 데이터에 액세스 (ClickOnce 앱)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e93c8479e917e74d31c3eedbb00d9d5911442b92
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810473"
---
# <a name="access-local-and-remote-data-in-clickonce-applications"></a>ClickOnce 애플리케이션의 로컬 및 원격 데이터 액세스
대부분 애플리케이션에서는 데이터를 사용하거나 생성합니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서는 로컬에서 또는 원격으로 데이터를 읽고 쓰는 다양한 옵션을 제공합니다.

## <a name="local-data"></a>로컬 데이터
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]에서는 다음 메서드의 하나를 사용하여 데이터를 로컬에서 로드 및 저장할 수 있습니다.

- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 데이터 디렉터리

- 격리된 스토리지

- 기타 로컬 파일

### <a name="clickonce-data-directory"></a>ClickOnce 데이터 디렉터리
 로컬 컴퓨터에 설치된 모든 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션에는 사용자의 Documents and Settings 폴더에 저장된 데이터 디렉터리가 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션에 포함되고 “데이터" 파일로 표시된 모든 파일은 애플리케이션이 설치될 때 이 디렉터리에 복사됩니다. 데이터 파일의 파일 형식은 가장 자주 사용되는 텍스트, XML 및 데이터베이스 파일(예: Microsoft Access .mdb 파일)이 될 수 있습니다.

 데이터 디렉터리는 애플리케이션이 명시적으로 저장 및 유지 관리하는 데이터인 애플리케이션에서 관리되는 데이터에 사용됩니다. 애플리케이션 매니페스트에서 “데이터"로 표시되지 않은 모든 정적, 독립적 파일은 애플리케이션 디렉터리에 있습니다. 이 디렉터리는 응용 프로그램의 실행 파일 (*.exe*)과 어셈블리가 상주 하는 위치입니다.

> [!NOTE]
> [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션이 제거되면 데이터 디렉터리도 제거됩니다. 문서와 같이 최종 사용자가 관리하는 데이터를 저장하는 데 절대 데이터 디렉터리를 사용하지 마세요.

#### <a name="mark-data-files-in-a-clickonce-distribution"></a>ClickOnce 배포에서 데이터 파일 표시
 데이터 디렉터리에 기존 파일을 넣으려면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션의 애플리케이션 매니페스트 파일에서 기존 파일을 데이터로 표시해야 합니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램에 데이터 파일 포함](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)을 참조 하세요.

#### <a name="read-from-and-write-to-the-data-directory"></a>데이터 디렉터리에서 데이터 읽기 및 쓰기
 데이터 디렉터리에서 데이터를 읽으려면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션이 읽기 권한을 요청해야 합니다. 마찬가지로 디렉터리에 쓰려면 쓰기 권한이 필요합니다. 애플리케이션이 완전 신뢰로 실행되도록 구성되면 이 권한이 애플리케이션에 자동으로 포함됩니다. 권한 상승 또는 신뢰할 수 있는 응용 프로그램 배포 중 하나를 사용 하 여 응용 프로그램에 대 한 권한 상승에 대 한 자세한 내용은 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)을 참조 하세요.

> [!NOTE]
> 조직에서 신뢰할 수 있는 애플리케이션 배포를 사용하지 않고 권한 상승을 해제했으면 권한 어설션이 실패합니다.

 애플리케이션에 이들 권한이 포함되고 나면 애플리케이션이 <xref:System.IO>내의 클래스에서 메서드 호출을 사용하여 데이터 디렉터리에 액세스할 수 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 의 <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> 속성에 정의된 <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> 속성을 사용하여 Windows Forms <xref:System.Deployment.Application.ApplicationDeployment>애플리케이션 내에 데이터 디렉터리의 경로를 가져올 수 있습니다. 이 방법은 데이터에 액세스하는 가장 편리하고 권장되는 방법입니다. 다음 코드 예제에서는 배포에 데이터 파일로 포함 한 *CSV.txt* 이라는 텍스트 파일에 대해이 작업을 수행 하는 방법을 보여 줍니다.

 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]

 배포의 파일을 데이터 파일로 표시하는 방법에 대한 자세한 내용은 [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)을 참조하세요.

 <xref:System.Windows.Forms.Application> 클래스에서 관련 변수(예: <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>)를 사용하여 데이터 디렉터리 경로를 가져올 수도 있습니다.

 기타 파일 형식을 조작하려면 추가 권한이 필요할 수 있습니다. 예를 들어 Access 데이터베이스 (*.mdb*) 파일을 사용 하려는 경우에는 응용 프로그램에서 관련 클래스를 사용 하기 위해 완전 신뢰를 어설션해야 합니다 \<xref:System.Data> .

#### <a name="data-directory-and-application-versions"></a>데이터 디렉터리 및 애플리케이션 버전
 각 애플리케이션 버전에는 다른 버전에서 격리된 고유한 데이터 디렉터리가 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서는 애플리케이션에 런타임에 새 데이터 파일을 만들 위치가 있도록 데이터 파일이 배포에 포함되는지와 관계없이 이 디렉터리를 만듭니다. 새 애플리케이션 버전이 설치될 때 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서는 기존 데이터 파일이 원래 배포에 포함되거나 애플리케이션에서 만들어지는지와 관계없이 모든 기존 데이터 파일을 이전 버전의 데이터 디렉터리에서 새 버전의 데이터 디렉터리로 복사합니다.

 데이터 파일에 새 버전과 다른 이전 애플리케이션 버전의 해시 값이 있으면[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서는 이전 버전의 파일을 새 버전의 서버로 바꿉니다. 또한 이전 버전의 애플리케이션이 새 버전 배포에 포함된 것과 같은 이름의 파일을 만들었다면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 에서는 새 파일로 이전 버전 파일을 덮어씁니다. 두 경우에 모두 이전 파일은 데이터 디렉터리 내의 `.pre`하위 디렉터리에 포함되므로 애플리케이션이 마이그레이션을 위해 계속 이전 데이터에 액세스할 수 있습니다.

 세부적인 데이터 마이그레이션이 필요하면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포 API를 사용하여 이전 데이터 디렉터리에서 새 데이터 디렉터리로 사용자 지정 마이그레이션을 수행할 수 있습니다. <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>을 사용하여 사용 가능한 다운로드가 있는지 테스트하거나, <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> 또는 <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>를 사용하여 업데이트를 다운로드하고 업데이트가 완료된 후 사용자 지정 데이터 마이그레이션 작업을 수행해야 합니다.

### <a name="isolated-storage"></a>격리된 스토리지
 격리된 스토리지는 단순 API를 사용하여 파일을 만들고 파일에 액세스하기 위한 API를 제공합니다. 저장된 파일의 실제 위치는 개발자 및 사용자에게 표시되지 않습니다.

 격리 된 저장소는 모든 버전의 .NET Framework에서 작동 합니다. 격리된 스토리지는 추가적인 권한을 부여할 필요 없이 부분적으로 신뢰할 수 있는 애플리케이션에서도 작동합니다. 애플리케이션이 부분 신뢰로 실행되어야 하지만 애플리케이션 특정 데이터를 유지 관리해야 하면 격리된 스토리지를 사용해야 합니다.

 자세한 내용은 [격리된 스토리지](/dotnet/standard/io/isolated-storage)를 참조하세요.

### <a name="other-local-files"></a>기타 로컬 파일
 애플리케이션이 보고서, 이미지, 음악 등의 최종 사용자 데이터를 사용하거나 저장해야 하면 애플리케이션에는 로컬 파일 시스템에서 데이터를 읽고 쓸 수 있는 <xref:System.Security.Permissions.FileIOPermission> 이 필요합니다.

## <a name="remote-data"></a>원격 데이터
 나중에 애플리케이션이 원격 웹 사이트에서 고객 데이터나 시장 정보와 같은 정보를 검색해야 할 수 있습니다. 이 섹션에서는 원격 데이터를 검색하는 가장 일반적인 방법을 설명합니다.

### <a name="access-files-with-http"></a>HTTP를 사용 하 여 파일 액세스
 <xref:System.Net.WebClient> 네임스페이스의 <xref:System.Net.HttpWebRequest> 또는 <xref:System.Net> 클래스를 사용하여 웹 서버에서 데이터에 액세스할 수 있습니다. 데이터는 정적 파일이거나 원시 텍스트 또는 XML 데이터를 반환하는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션일 수 있습니다. 데이터가 XML 형식이면 포함된 <xref:System.Xml.XmlDocument> 메서드가 URL을 인수로 사용하는 <xref:System.Xml.XmlDocument.Load%2A> 클래스를 사용하여 데이터를 가장 빠르게 검색할 수 있습니다. 예제를 보려면 [DOM에서 XML 문서 읽기](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom)를 참조 하십시오.

 애플리케이션이 HTTP를 통해 원격 데이터에 액세스할 경우 보안을 고려해야 합니다. 기본적으로 애플리케이션 배포 방법에 따라 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션의 네트워크 리소스 액세스가 제한될 수 있습니다. 악의적인 프로그램이 권한 있는 원격 데이터에 액세스하지 못하도록 차단하거나 사용자 컴퓨터를 사용하여 네트워크의 다른 컴퓨터를 공격하지 못하도록 차단하기 위해 이러한 제한이 적용됩니다.

 다음 표에는 사용할 수 있는 배포 전략 및 기본 웹 권한이 나와 있습니다.

|배포 유형|기본 네트워크 권한|
|---------------------|---------------------------------|
|웹 설치|애플리케이션이 설치되는 소스 웹 서버에만 액세스할 수 있습니다.|
|파일 공유 설치|웹 서버에 액세스할 수 없습니다.|
|CD-ROM 설치|웹 서버에 액세스할 수 있습니다.|

 보안 제한으로 인해 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션이 웹 서버에 액세스할 수 없으면 애플리케이션은 해당 웹 사이트에 대한 <xref:System.Net.WebPermission> 을 어설션해야 합니다. 응용 프로그램의 보안 권한을 높이는 방법에 대 한 자세한 내용은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)을 참조 하세요.

### <a name="access-data-through-an-xml-web-service"></a>XML Web services를 통해 데이터 액세스
 데이터를 XML Web service로 노출하면 XML Web service 프록시를 통해 데이터에 액세스할 수 있습니다. 프록시는 둘 중 하나를 사용 하 여 만드는 .NET Framework 클래스입니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 고객 검색, 주문 제출 등의 XML Web service 작업은 프록시에서 메서드로 노출됩니다. 이를 통해 원시 텍스트 또는 XML 파일보다 훨씬 더 쉽게 Web services를 사용할 수 있습니다.

 XML Web service가 HTTP를 통해 작동할 경우 서비스는 <xref:System.Net.WebClient> 및 <xref:System.Net.HttpWebRequest> 클래스와 같은 보안 제한 사항이 적용됩니다.

### <a name="access-a-database-directly"></a>데이터베이스에 직접 액세스
 <xref:System.Data> 네임스페이스 내의 클래스를 사용하여 네트워크의 SQL Server와 같은 데이터베이스 서버에 대한 직접 연결을 설정할 수 있지만 보안 문제를 고려해야 합니다. HTTP 요청과 달리 데이터베이스 연결 요청은 부분 신뢰가 적용될 경우 기본적으로 항상 금지됩니다. CD-ROM에서 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션을 설치할 경우에만 해당 권한이 기본적으로 제공됩니다. 이렇게 하면 애플리케이션에 완전 신뢰가 제공됩니다. 특정 SQL Server 데이터베이스에 대한 액세스를 사용하려면 애플리케이션이 <xref:System.Data.SqlClient.SqlClientPermission> 을 요청해야 하고, SQL Server 이외의 데이터베이스에 대한 액세스를 사용하려면 <xref:System.Data.OleDb.OleDbPermission>을 요청해야 합니다.

 대부분은 데이터베이스에 직접 액세스할 필요가 없고 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 또는 XML Web service에서 작성된 웹 서버 애플리케이션을 통해 액세스합니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 애플리케이션이 웹 서버에서 배포될 경우 이 방식으로 데이터베이스에 액세스하는 것이 대부분 가장 적합한 방법입니다. 애플리케이션의 권한을 높이지 않고 서버를 부분 신뢰로 액세스할 수 있습니다.

## <a name="see-also"></a>추가 정보

- [방법: ClickOnce 응용 프로그램에 데이터 파일 포함](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)
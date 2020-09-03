---
title: 이벤트 처리기가 모델 외부에서 변경 내용을 전파 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a23a8d28f336728789fe9cbbe38f965cc56763d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74295514"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>이벤트 처리기로 모델 외부의 변경 내용 전파
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

시각화 및 모델링 SDK에서 저장소 외부의 리소스에 변경 내용을 전파 하는 저장소 이벤트 처리기를 정의할 수 있습니다 (예: 비 스토어 변수, 파일, 다른 저장소의 모델 또는 기타 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장). 트리거 이벤트가 발생 한 트랜잭션이 종료 된 후에도 저장소 이벤트 처리기가 실행 됩니다. 실행 취소 또는 다시 실행 작업 에서도 실행 됩니다. 따라서 저장소 규칙과 달리 저장소 이벤트는 저장소 외부에 있는 값을 업데이트 하는 데 가장 유용 합니다. .NET 이벤트와 달리 저장소 이벤트 처리기는 클래스를 수신 하도록 등록 됩니다. 각 인스턴스에 대해 별도의 처리기를 등록할 필요가 없습니다. 변경 사항을 처리 하는 다양 한 방법 중에서 선택 하는 방법에 대 한 자세한 내용은 [변경 내용에 대 한 응답 및 전파](../modeling/responding-to-and-propagating-changes.md)를 참조 하세요.

 그래픽 화면 및 기타 사용자 인터페이스 컨트롤은 저장소 이벤트에서 처리할 수 있는 외부 리소스의 예입니다.

### <a name="to-define-a-store-event"></a>저장소 이벤트를 정의 하려면

1. 모니터링할 이벤트 유형을 선택 합니다. 전체 목록은의 속성을 참조 <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> 하세요. 각 속성은 이벤트의 형식에 해당 합니다. 가장 자주 사용 되는 이벤트 유형은 다음과 같습니다.

   - `ElementAdded` – 모델 요소, 관계 링크, 셰이프 또는 연결선을 만들 때 트리거됩니다.

   - ElementPropertyChanged – `Normal` 도메인 속성 값이 변경 될 때 트리거됩니다. 이벤트는 새 값과 이전 값이 같지 않은 경우에만 트리거됩니다. 계산 된 저장소 속성 및 사용자 지정 저장소 속성에는 이벤트를 적용할 수 없습니다.

        관계 링크에 해당 하는 역할 속성에는 적용할 수 없습니다. 대신를 사용 `ElementAdded` 하 여 도메인 관계를 모니터링 합니다.

   - `ElementDeleted` – 모델 요소, 관계, 모양 또는 연결선을 삭제 한 후에 트리거됩니다. 요소의 속성 값에 계속 액세스할 수 있지만 다른 요소와의 관계는 없습니다.

2. **Dslpackage** 프로젝트의 별도 코드 파일에 _dsl_**docdata** 에 대 한 부분 클래스 정의를 추가 합니다.

3. 다음 예제와 같이 이벤트의 코드를 메서드로 작성 합니다. 에 액세스 하려는 경우가 아니면이는 일 수 있습니다 `static` `DocData` .

4. `OnDocumentLoaded()`처리기를 등록 하려면를 재정의 합니다. 둘 이상의 처리기가 있는 경우 모두 동일한 장소에 등록할 수 있습니다.

   등록 코드의 위치는 중요 하지 않습니다. `DocView.LoadView()` 는 대체 위치입니다.

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don’t forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }

}

```

## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>이벤트를 사용 하 여 저장소에서 취소할 수 있는 조정 만들기
 트랜잭션 커밋 후 이벤트 처리기가 실행 되기 때문에 저장소 이벤트는 일반적으로 저장소 내에서 변경 내용을 전파 하는 데 사용 되지 않습니다. 대신 저장소 규칙을 사용 합니다. 자세한 내용은 [모델 내에서 변경 내용 전파 규칙](../modeling/rules-propagate-changes-within-the-model.md)을 참조 하세요.

 그러나 사용자가 원래 이벤트와 별도로 추가 업데이트를 실행 취소할 수 있도록 하려면 이벤트 처리기를 사용 하 여 저장소에 대 한 추가 업데이트를 만들 수 있습니다. 예를 들어 낮은 케이스 문자가 앨범 제목의 일반적인 규칙 이라고 가정 합니다. 사용자가 대문자로 입력 한 후 소문자로 제목을 수정 하는 저장소 이벤트 처리기를 작성할 수 있습니다. 그러나 사용자는 실행 취소 명령을 사용 하 여 대/소문자를 복원 하는 수정 작업을 취소할 수 있습니다. 두 번째 실행 취소는 사용자의 변경 내용을 제거 합니다.

 이와 대조적으로 동일한 작업을 수행 하는 저장 규칙을 작성 한 경우 사용자가 변경 내용을 유지 하는 동시에 사용자가 원래 변경 내용을 잃지 않고 조정을 취소할 수 없게 됩니다.

```

partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}

```

 저장소를 업데이트 하는 이벤트를 작성 하는 경우:

- `store.InUndoRedoOrRollback`실행 취소의 모델 요소를 변경 하지 않으려면를 사용 합니다. 트랜잭션 관리자는 저장소의 모든 항목을 원래 상태로 다시 설정 합니다.

- `store.InSerializationTransaction`를 사용 하 여 모델을 파일에서 로드 하는 동안 변경 하지 않도록 합니다.

- 변경 내용으로 인해 추가 이벤트가 트리거됩니다. 무한 루프가 발생 하지 않도록 하십시오.

## <a name="store-event-types"></a>이벤트 유형 저장
 각 이벤트 형식은 EventManagerDirectory의 컬렉션에 해당 합니다. 언제 든 지 이벤트 처리기를 추가 하거나 제거할 수 있지만 문서가 로드 될 때 이러한 처리기를 추가 하는 것이 일반적입니다.

|`EventManagerDirectory` 속성 이름|실행 시간|
|-------------------------------------------|-------------------|
|ElementAdded 됨|도메인 클래스, 도메인 관계, 셰이프, 연결선 또는 다이어그램의 인스턴스가 만들어집니다.|
|ElementDeleted|모델 요소가 저장소의 요소 디렉터리에서 제거 되었으며 더 이상 관계의 소스 또는 대상이 아닙니다. 요소는 실제로 메모리에서 삭제 되지 않지만 이후 실행 취소의 경우 유지 됩니다.|
|ElementEventsBegun|외부 트랜잭션의 끝에서 호출 됩니다.|
|ElementEventsEnded|다른 모든 이벤트가 처리 될 때 호출 됩니다.|
|ElementMoved|하나의 저장소 파티션에서 다른 저장소 파티션으로 모델 요소가 이동 되었습니다.<br /><br /> 이는 다이어그램에서 셰이프의 위치와는 관련이 없습니다.|
|ElementPropertyChanged|도메인 속성의 값이 변경 되었습니다. 이전 값과 새 값이 같지 않은 경우에만 실행 됩니다.|
|RolePlayerChanged|관계의 두 역할 (end) 중 하나가 새 요소를 참조 합니다.|
|RolePlayerOrderChanged|복합성이 1 보다 큰 역할에서 링크 시퀀스는 변경 되었습니다.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>관련 항목
 [변경 내용에 대한 대응 및 전파](../modeling/responding-to-and-propagating-changes.md)

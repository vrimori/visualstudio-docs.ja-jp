---
title: イベント ハンドラーによって変更内容がモデル外に反映される
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 02cf41daa9bea74e62ceb96f7c6227982bfcad84
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967351"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>イベント ハンドラーによって変更内容がモデル外に反映される

Visualization and Modeling SDK では、ストア以外の変数、ファイル、その他のストア、またはその他の Visual Studio 拡張機能でのモデルなど、ストアの外部リソースへの変更を反映するストア イベント ハンドラーを定義できます。 ストア イベント ハンドラーは、トリガーを起動するイベントが発生したトランザクションの終了後に実行されます。 元に戻す/やり直し操作でも実行されます。 そのため、ストアの規則とは異なりストア イベントは、ストア外の値を更新するため、最も役に立つします。 クラスにリッスンするように .NET のイベントとは異なりストア イベント ハンドラーが登録されている: インスタンスごとに個別のハンドラーを登録する必要はありません。 変更を処理するさまざまな方法を選択する方法の詳細については、次を参照してください。[への対応および変更の反映](../modeling/responding-to-and-propagating-changes.md)します。

グラフィカル サーフェイスおよびその他のユーザー インターフェイス コントロールは、ストア イベントで処理できる外部のリソースの例を示します。

### <a name="to-define-a-store-event"></a>ストア イベントを定義するには

1.  監視するイベントの種類を選択します。 完全な一覧については、プロパティを確認<xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>します。 各プロパティは、イベントの種類に対応します。 最もイベントの種類は頻繁に使用します。

    -   `ElementAdded` -モデル要素のときにトリガーされると、リンクのリレーションシップ、図形またはコネクタが作成されます。

    -   ElementPropertyChanged - がトリガーされたときの値を`Normal`ドメイン プロパティを変更します。 イベントは、新旧の値が等しくない場合にのみトリガーされます。 イベントは、計算およびカスタム格納プロパティに適用できません。

         これは、リレーションシップ リンクに対応するロールのプロパティに適用できません。 代わりに、`ElementAdded`ドメインの関係を監視します。

    -   `ElementDeleted` -モデル要素の後にトリガーされると、リレーションシップ、図形またはコネクタが削除されました。 要素のプロパティ値に引き続きアクセスできますが、その他の要素へのリレーションシップはありません。

2.  部分クラス定義を追加_YourDsl_**DocData**で別のコード ファイルで、 **DslPackage**プロジェクト。

3.  次の例のように、メソッドとして、イベントのコードを記述します。 できます`static`にアクセスする場合を除き、`DocData`します。

4.  オーバーライド`OnDocumentLoaded()`ハンドラーを登録します。 1 つ以上のハンドラーがある場合は、すべて同じ場所に登録できます。

登録コードの場所は重要ではありません。 `DocView.LoadView()` 代替の場所です。

```csharp
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
      base.OnDocumentLoaded(); // Don't forget this.

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>イベントを使用して、ストアで取り消し可能な調整を行う

ストア イベントは通常使用されない、ストア内の変更を反映するため、トランザクションがコミットされた後にイベント ハンドラーが実行されるためです。 代わりに、ストアの規則を使用します。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)します。

ただし、ユーザーは、元のイベントから個別に追加の更新プログラムを元に戻すことができるようにする場合は、ストアに追加の更新プログラムを作成するイベント ハンドラーを使用できます。 たとえば、小文字の文字が、通常の規則のアルバム タイトルがあるとします。 ユーザーが大文字で入力が後に小文字にタイトルを修正するストア イベント ハンドラーを記述できます。 ユーザーが元に戻すコマンドを使用して、修正、大文字の文字の復元をキャンセルします。 2 番目の取り消しは、ユーザーの変更を削除します。

これに対し、同じことを行うストア ルールを記述した場合、ユーザーの変更と、修正はように内に、同じトランザクションでユーザーは、元の変更を失うことがなく調整を取り消されませんでした。

```csharp
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

イベントを記述する場合は、ストアを更新します。

-   使用`store.InUndoRedoOrRollback`元に戻すのモデル要素を変更するようにします。 トランザクション マネージャーの設定すべてストアを元の状態にします。

-   使用`store.InSerializationTransaction`モデルは、ファイルから読み込み中に変更しないようにします。

-   変更は、さらにトリガーされるようにイベントが発生されます。 無限ループを避けることを確認します。

## <a name="store-event-types"></a>ストア イベントの種類

各イベントの種類は、Store.EventManagerDirectory でコレクションに対応します。 追加または、いつでもイベント ハンドラーを削除することができますが、通常、ドキュメントが読み込まれるときに、それらを追加します。

|`EventManagerDirectory` プロパティ名|実行すると実行|
|-|-|
|ElementAdded|ドメイン クラス、ドメイン リレーションシップ、図形、コネクタまたはダイアグラムのインスタンスが作成されます。|
|ElementDeleted|モデル要素は、ストアの要素のディレクトリからが削除され、ソースまたはリレーションシップのターゲットは、不要になった。 要素は、実際には、メモリからは削除されませんが、将来の元に戻す場合は保持されます。|
|ElementEventsBegun|外側のトランザクションの最後に呼び出されます。|
|ElementEventsEnded|その他のすべてのイベントが処理されたときに呼び出されます。|
|ElementMoved|モデル要素は別に 1 つのストアのパーティションから移動されました。<br /><br /> ダイアグラムの図形の場所にこれは無関係です。|
|ElementPropertyChanged|ドメイン プロパティの値が変更されました。 これは、新旧の値が等しくない場合にのみ実行されます。|
|RolePlayerChanged|リレーションシップの 2 つのロール (端) の 1 つは、新しい要素を参照します。|
|RolePlayerOrderChanged|多重度が 1 より大きいロールでは、一連のリンクが変更されています。|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>関連項目

- [変更内容への対応および変更内容の反映](../modeling/responding-to-and-propagating-changes.md)
- [サンプル コード: 回路図](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
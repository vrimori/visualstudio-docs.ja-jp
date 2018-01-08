---
title: "イベント ハンドラーには、モデルの外部で変更が反映されるまで |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: b1ef5efcce853f55ad518f1cdba35d2363f5504e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>イベント ハンドラーによって変更内容がモデル外に反映される
Visualization and Modeling SDK がでは、ストア以外の変数、ファイル、その他のストア、またはその他のモデルなど、ストアの外部リソースへの変更を反映するストアのイベント ハンドラーを定義することができます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能です。 ストアのイベント ハンドラーは、トリガーを起動するイベントが発生したトランザクションの終了後に実行されます。 元に戻す/やり直し操作でも実行されます。 そのため、ストアの規則とは異なりストア イベントは、ストア以外の値を更新するため、最も役に立つです。 クラスにリッスンするように、.NET イベントとは異なりストア イベント ハンドラーが登録されている: インスタンスごとに個別のハンドラーを登録する必要はありません。 間の変更を処理するさまざまな方法を選択する方法の詳細については、次を参照してください。[への応答と変更を反映する](../modeling/responding-to-and-propagating-changes.md)です。  
  
 グラフィカル サーフェイスおよびその他のユーザー インターフェイス コントロールは、ストアのイベントを処理する外部のリソースの例を示します。  
  
### <a name="to-define-a-store-event"></a>ストアのイベントを定義するには  
  
1.  監視するイベントの種類を選択します。 プロパティの完全な一覧を調べて<xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>です。 各プロパティは、イベントの種類に対応します。 頻繁に使用するイベントの種類は。  
  
    -   `ElementAdded`モデル要素のときにトリガーされると、関係のリンク、図形またはコネクタを作成します。  
  
    -   ElementPropertyChanged - がトリガーされたときの値、`Normal`ドメイン プロパティが変更されました。 新旧の値が等しくない場合にのみ、イベントがトリガーされます。 イベントは、計算およびカスタムのストレージ プロパティに適用できません。  
  
         リレーションシップ リンクに対応するロールのプロパティを適用することはできません。 代わりに、`ElementAdded`ドメインの関係を監視します。  
  
    -   `ElementDeleted`-トリガーされると、モデル要素の後、リレーションシップ、図形またはコネクタが削除されます。 引き続き、要素のプロパティの値にアクセスできますが、その他の要素へのリレーションシップはありません。  
  
2.  部分クラス定義を追加*YourDsl***DocData**で別のコード ファイルで、 **DslPackage**プロジェクト。  
  
3.  次の例のように、メソッドとして、イベントのコードを記述します。 できます`static`にアクセスする場合を除き、`DocData`です。  
  
4.  オーバーライド`OnDocumentLoaded()`ハンドラーを登録します。 複数のハンドラーを使っている場合は、すべて同じ場所に登録できます。  
  
 登録コードの場所は重要ではありません。 `DocView.LoadView()`代替の場所です。  
  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>イベントを使用したストアで取り消し可能な調整を行う  
 ストアのイベントは通常使用されません、ストア内の変更を反映するため、トランザクションがコミットされた後に、イベント ハンドラーが実行されるため。 代わりに、ストアの規則を使用します。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)です。  
  
 ただし、ユーザーが元のイベントから個別に追加の更新プログラムを元に戻すことができるようにする場合は、追加の更新プログラムをストアにするのには、イベント ハンドラーを使用できます。 たとえば、小文字のみがアルバム タイトルの通常の規則であるとします。 ユーザーが入力で大文字に変換した後に小文字にタイトルを修正するストア イベント ハンドラーを記述することもできます。 ユーザーは大文字に変換する文字を復元する修正が終わったら、[キャンセル] を元に戻すコマンドを使用します。 2 番目の元に戻すよう、ユーザーの変更を削除します。  
  
 これに対し、同じ処理を実行する規則をストアを作成した場合、ユーザーの変更と、修正は、同じトランザクションでようにでユーザーで、元の変更を失うことがなくの調整を取り消すことができない可能性があります。  
  
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
  
 イベントを記述する場合、ストアを更新します。  
  
-   使用して`store.InUndoRedoOrRollback`元に戻すのモデル要素を変更するようにします。 トランザクション マネージャーはすべてストア内の設定を元の状態に戻す。  
  
-   使用して`store.InSerializationTransaction`ファイルからモデルを読み込み中は変更しないようにします。  
  
-   変更内容は、さらをトリガーするイベントが発生されます。 無限ループを避けることを確認します。  
  
## <a name="store-event-types"></a>イベントの種類を保存します。  
 各イベントの種類は、Store.EventManagerDirectory でコレクションに対応します。 追加するか、いつでもイベント ハンドラーを削除ですが、通常、ドキュメントが読み込まれるときに追加します。  
  
|`EventManagerDirectory`プロパティ名|実行すると実行|  
|-------------------------------------------|-------------------|  
|ElementAdded|ドメイン クラス、ドメインの関係、図形、コネクタまたはダイアグラムのインスタンスが作成されます。|  
|ElementDeleted|モデル要素が、ストアの要素のディレクトリから削除された、不要になったソースまたはリレーションシップのターゲット。 要素は、実際には、メモリからは削除されませんが、将来の取り消しが発生した場合に保持されます。|  
|ElementEventsBegun|外側のトランザクションの最後に呼び出されます。|  
|ElementEventsEnded|その他のすべてのイベントが処理されるときに呼び出されます。|  
|ElementMoved|モデル要素を別の 1 つのストア パーティションから移動されました。<br /><br /> ダイアグラムの図形の場所にこれは無関係です。|  
|ElementPropertyChanged|ドメイン プロパティの値が変更されました。 これは、新旧の値が等しくない場合にのみ実行されます。|  
|RolePlayerChanged|リレーションシップの 2 つのロール (端) の 1 つは、新しい要素を参照します。|  
|RolePlayerOrderChanged|多重度が 1 より大きいロールでは、リンクの順序が変更されました。|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>参照  
 [対応し、変更を反映します。](../modeling/responding-to-and-propagating-changes.md)   
 [サンプル コード: 回路図](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 

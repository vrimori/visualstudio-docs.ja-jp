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
caps.latest.revision: 18
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: af5fbd8973082e92f9609e335314a30eb22595fa
ms.lasthandoff: 02/22/2017

---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>イベント ハンドラーによって変更内容がモデル外に反映される
Visualization and Modeling SDK がでは、ストア以外の変数、ファイル、その他のストアまたはその他のモデルなど、ストア外のリソースに変更を反映するストア イベント ハンドラーを定義できます[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能です。 ストア イベント ハンドラーは、トリガーを起動するイベントが発生したトランザクションの終了後に実行されます。 元に戻す/やり直し操作でも実行します。 そのため、ストアの規則とは異なりストア イベントは、ストア以外の値を更新するため、最も役に立つです。 クラスにリッスンするように .NET イベントとは異なりストア イベント ハンドラーが登録されている: インスタンスごとに個別のハンドラーを登録する必要はありません。 変更を処理するさまざまな方法の選択方法の詳細については、次を参照してください。[に応答すると変更の伝達](../modeling/responding-to-and-propagating-changes.md)します。  
  
 グラフィカル サーフェイスおよびその他のユーザー インターフェイス コントロールは、ストア イベントを処理できる外部のリソースの例を示します。  
  
### <a name="to-define-a-store-event"></a>ストア イベントを定義するには  
  
1.  監視するイベントの種類を選択します。 完全な一覧については、 <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>。</xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>のプロパティを確認します。 各プロパティは、イベントの種類に対応します。 ほとんどは、イベントの種類はよく使用します。  
  
    -   `ElementAdded`– モデルの要素のときにトリガーされると、リレーションシップ リンク、図形またはコネクタを作成します。  
  
    -   ElementPropertyChanged – がトリガーされたときの値、`Normal`ドメイン プロパティを変更します。 新旧の値が等しくない場合にのみ、イベントが発生します。 イベントは、計算とカスタムの記憶域のプロパティには適用できません。  
  
         リレーションシップ リンクに対応するロールのプロパティに適用することはできません。 代わりに、`ElementAdded`ドメインの関係を監視します。  
  
    -   `ElementDeleted`– モデル要素の後にトリガーされると、リレーションシップ、図形またはコネクタが削除されました。 要素のプロパティ値にもアクセスできますが、その他の要素との関係はありません。  
  
2.  部分クラス定義を追加*YourDsl***DocData**で別のコード ファイルで、 **DslPackage**プロジェクトです。  
  
3.  次の例のように、メソッドとして、イベントのコードを記述します。 できます`static`にアクセスする場合を除き、`DocData`です。  
  
4.  オーバーライド`OnDocumentLoaded()`ハンドラーを登録します。 複数のハンドラーがある場合は、すべて同じ場所に登録できます。  
  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>イベントを使用した、ストアで取り消し可能な調整を行う  
 ストア イベントは通常使用されません、ストア内の変更を反映するため、トランザクションがコミットされた後に、イベント ハンドラーが実行されるためです。 代わりに、ストアのルールを使用します。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)します。  
  
 ただし、ユーザーが元のイベントから個別に追加の更新プログラムを元に戻すことができるようにする場合、ストアに追加の更新を行うイベント ハンドラーを使用する可能性があります。 たとえば、小文字のみがアルバム タイトルの通常の規則であるとします。 ユーザーが入力で大文字に変換した後に小文字にタイトルを修正するストア イベント ハンドラーを記述できます。 ユーザーは大文字に変換する文字を復元する、修正を取り消すために元に戻すコマンドを使用する可能性があります。 2 番目の復元は、ユーザーの変更を削除します。  
  
 これに対し、同じ変換にストア ルールを作成した場合、ユーザーの変更と、修正になります、同じトランザクションでユーザーで、元の変更を失うことがなくの調整を取り消すことができないことができるようにします。  
  
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
  
-   使用`store.InUndoRedoOrRollback`元に戻す内のモデル要素を変更するようにします。 トランザクション マネージャーによってすべての元の状態ストアに設定されます。  
  
-   使用`store.InSerializationTransaction`モデルは、ファイルから読み込み中に変更を作成しないようにします。  
  
-   変更内容は、さらをトリガーするイベントが発生されます。 無限ループを避けることを確認します。  
  
## <a name="store-event-types"></a>ストア イベントの種類  
 各イベントの種類は、Store.EventManagerDirectory 内のコレクションに対応します。 追加またはいつでもイベント ハンドラーを削除することができますは通常、ドキュメントの読み込み時に追加します。  
  
|`EventManagerDirectory`プロパティ名|実行すると実行|  
|-------------------------------------------|-------------------|  
|ElementAdded|ドメイン クラス、ドメイン リレーションシップ、図形、コネクタまたはダイアグラムのインスタンスが作成されます。|  
|ElementDeleted|モデル要素が、ストアの要素のディレクトリから削除されて、不要になったソースまたはリレーションシップのターゲットです。 要素は、実際には、メモリからは削除されませんが、将来の取り消しが発生した場合は保持されます。|  
|ElementEventsBegun|外側のトランザクションの最後に呼び出されます。|  
|ElementEventsEnded|その他のすべてのイベントが処理されると呼び出されます。|  
|ElementMoved|モデル要素は、別に、ストアが&1; つのパーティションから移動されました。<br /><br /> これは、図においてシェイプの場所には関係ありません。|  
|ElementPropertyChanged|ドメイン プロパティの値が変更されました。 これは、新旧の値が等しくない場合にのみ実行されます。|  
|RolePlayerChanged|リレーションシップの&2; つのロール (端) の&1; つは、新しい要素を参照します。|  
|RolePlayerOrderChanged|多重度が 1 より大きいロールでは、リンクの順序が変更されました。|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>関連項目  
 [対応し、変更の反映](../modeling/responding-to-and-propagating-changes.md)   
 [サンプル コード: 回路図](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 


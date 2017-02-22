---
title: "削除動作のカスタマイズ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.deletebehavior"
helpviewer_keywords: 
  - "ドメイン固有言語, 削除"
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: 23
caps.handback.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 削除動作のカスタマイズ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

通常、要素を削除すると、関連する要素も削除されます。  接続されたすべてのリレーションシップと子要素が削除されます。  この動作を*削除の伝達*といいます。  削除の伝達をカスタマイズできます。たとえば、追加の関連要素を削除することを準備できます。  プログラム コードを作成して、モデルの状態に応じた削除の伝達を実現できます。  削除に応じて他の変更を発生させることもできます。  
  
 ここでは、次の内容について説明します。  
  
-   [既定の削除動作](#default)  
  
-   [ロールの削除伝達の設定オプション](#property)  
  
-   [削除クロージャのオーバーライド](#closure) – 削除によって隣接する要素が削除される可能性がある場合にこの手法を使用します。  
  
-   [OnDeleting および OnDeleted の使用](#ondeleting) – 応答にストア内またはストア外のいずれかの値の更新など、他の操作が含まれる可能性がある場合に、これらのメソッドを使用します。  
  
-   [削除規則](#rules) – ある変更が別の変更につながる可能性がある場合、規則を使用して、ストア内の任意の種類の更新を伝達します。  
  
-   [削除イベント](#rules) – ストア イベントを使用して、たとえば他の [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ドキュメントなど、ストア外の更新を伝達します。  
  
-   [UnMerge](#unmerge) – UnMerge 操作を使用して、子要素を親にアタッチしたマージ操作を元に戻します。  
  
##  <a name="default"></a> 既定の削除動作  
 既定では、次の規則が削除の伝達を制御します。  
  
-   要素が削除された場合、埋め込まれたすべての要素も削除されます。  埋め込まれた要素は、この要素がソースである埋め込みリレーションシップのターゲットです。  たとえば、Album から Song への埋め込みリレーションシップがある場合、特定のアルバムが削除されると、そのすべてのソングが削除されます。  
  
     対照的に、ソングを削除してもアルバムは削除されません。  
  
-   既定では、削除は参照リレーションシップに沿って伝達されません。  Album から Artist への参照リレーションシップ ArtistPlaysOnAlbum がある場合、アルバムを削除しても関連するどのアーチストも削除されず、アーチストを削除してもどのアルバムも削除されません。  
  
     ただし、削除は一部の組み込みリレーションシップに沿って伝達されます。  たとえば、モデル要素が削除されると、その図形も図から削除されます。  要素を図形は `PresentationViewsSubject` 参照リレーションシップによって関連付けられています。  
  
-   ソース ロールまたはターゲット ロールのいずれかで要素に接続されたすべてのリレーションシップは削除されます。  反対のロールの要素のロール プロパティには削除された要素が含まれなくなります。  
  
##  <a name="property"></a> ロールの削除伝達の設定オプション  
 削除によって参照リレーションシップに沿った伝達または埋め込まれた子から親への伝達を発生させることができます。  
  
#### 削除の伝達を設定するには  
  
1.  DSL 定義図で、削除を伝達する*ロール*を選択します。  ロールはドメイン リレーションシップ ボックスの左側または右側の線で表されます。  
  
     たとえば、アルバムが削除された場合は常に関連するアーチストも削除されるように指定する場合、ドメイン クラス Artist に接続されたロールを選択します。  
  
2.  \[プロパティ\] ウィンドウで、**\[削除の伝達\]** プロパティを設定します。  
  
3.  F5 キーを押して、次のことを検証します。  
  
    -   このリレーションシップのインスタンスが削除されると、選択したロールの要素も削除されます。  
  
    -   反対のロールの要素が削除されると、このリレーションシップのインスタンスは削除され、このロールの関連要素は削除されます。  
  
 **\[DSL 詳細\]** ウィンドウの **\[削除の伝達\]** オプションでも確認できます。  ドメイン クラスを選択し、DSL 詳細ウィンドウで、ウィンドウの端のボタンをクリックして、**\[削除動作\]** ページを開きます。  各リレーションシップの反対のロールに対して **\[伝達\]** オプションが表示されます。  **\[削除スタイル\]** 列は **\[伝達\]** オプションが既定の設定かどうかを示しますが、個別の効果はありません。  
  
## プログラム コードを使用する削除の伝達  
 DSL 定義ファイル内のオプションにより選択できるのは、削除がすぐ隣に伝達するかどうかのみです。  より複雑な削除の伝達のしくみを実装するために、プログラム コードを作成できます。  
  
> [!NOTE]
>  DSL 定義にプログラム コードを追加するには、**Dsl** プロジェクト内に別個のコード ファイルを作成し、部分定義を作成して、Generated Code フォルダー内のクラスを強化します。  詳細については、「[ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)」を参照してください。  
  
##  <a name="closure"></a> 削除クロージャの定義  
 削除操作はクラス *YourModel***DeleteClosure** を使用して、削除する要素を決定し、初期選択を指定します。  これは `ShouldVisitRelationship()` および `ShouldVisitRolePlayer()` を繰り返し呼び出し、リレーションシップのグラフを検索します。  これらのメソッドをオーバーライドできます。  ShouldVisitRolePlayer はリンクの ID およびリンクのロールの一方における要素とともに提供されます。  次のいずれかの値を返す必要があります。  
  
-   **VisitorFilterResult.Yes**– 要素は削除され、ウォーカーは要素の他のリンクを試すために進みます。  
  
-   **VisitorFilterResult.DoNotCare** – 別のクエリが削除の必要があることを示す応答を返すのでない限り、要素は削除されません。  
  
-   **VisitorFilterResult.Never** – 別のクエリが **Yes** を返したとしても、要素は削除されません。また、ウォーカーは要素の他のリンクを試しません。  
  
```  
// When a musician is deleted, delete their albums with a low rating.  
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs  
partial class MusicLibDeleteClosure  
{  
  public override VisitorFilterResult ShouldVisitRolePlayer  
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,   
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)  
  {  
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;  
    if (link != null   
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)  
    {  
      // Count other unvisited links to the Album of this link.  
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)  
              .Where(linkAlbumArtist =>   
                     linkAlbumArtist != link &&  
                     !walker.Visited(linkAlbumArtist))  
              .Count() == 0)  
      {  
        // Should delete this role player:  
        return VisitorFilterResult.Yes;   
      }  
      else  
        // Don’t delete unless another relationship deletes it:  
        return VisitorFilterResult.DoNotCare;   
    }  
    else   
    {  
      // Test for and respond to other relationships and roles here.  
  
      // Not the relationship or role we’re interested in.  
      return base.ShouldVisitRolePlayer(walker, sourceElement,   
             elementLink, targetDomainRole, targetRolePlayer);  
    }  
  }  
}  
  
```  
  
 このクロージャ手法により、削除する要素をリンクのセットが削除が始まる前に決定されることを確実にします。  また、ウォーカーはクロージャの結果をモデルの他の部分からの結果と結合します。  
  
 ただし、この手法は削除がリレーションシップのグラフ内の隣にあるものにのみ影響することを仮定しています。この方法を使用してモデルの別の部分にある要素を削除することはできません。  削除に応じて要素を追加したり他の変更を実行したりする場合には使用できません。  
  
##  <a name="ondeleting"></a> OnDeleting と OnDeleted の使用  
 ドメイン クラスまたはドメイン リレーションシップのいずれかで、`OnDeleting()` または `OnDeleted()` をオーバーライドできます。  
  
1.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> は、要素が削除されようとしているときで、そのリレーションシップが切断されている前に呼び出されます。  まだ他の要素に対して移動可能で、`store.ElementDirectory` の中にあります。  
  
     同時にいくつかの要素が削除される場合、削除の実行前にそれらすべてに対して OnDeleting が呼び出されます。  
  
     `IsDeleting` は true です。  
  
2.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> は要素が削除されると呼び出されます。  CLR ヒープ内に留まるので、必要があれば Undo を実行できますが、他の要素からのリンクは解除され、`store.ElementDirectory` から削除されます。  リレーションシップについて、ロールは古いロール プレーヤーを参照したままです。`IsDeleted` は true です。  
  
3.  OnDeleting および OnDeleted は要素の作成後にユーザーが Undo を起動するとき、および以前の削除が Redo で繰り返されるときに呼び出されます。  これらの場合にストア要素の更新を回避するには `this.Store.InUndoRedoOrRollback` を使用します。  詳細については、「[方法: トランザクションを使用してモデルを更新する](../modeling/how-to-use-transactions-to-update-the-model.md)」を参照してください。  
  
 たとえば、次のコードでは、最後の子 Song が削除されると Album が削除されます。  
  
```  
  
// Delete the parent Album when the last Song is deleted.  
// Override methods in the embedding relationship between Album and Song:  
partial class AlbumHasSongs  
{  
  protected override void OnDeleted()  
  {  
    base.OnDeleted();  
    // Don't perform in-store actions in undo:  
    if (this.Store.InUndoRedoOrRollback) return;  
    // Relationship source and target still work:  
    // Don't bother if source is already on its way out:  
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)  
    {  
      if (this.Album.Songs.Count == 0)  
      {   
        this.Album.Delete();  
} } } }  
  
```  
  
 多くの場合、ロール要素よりもリレーションシップの削除からトリガーする方が有用です。なぜなら、要素の削除時とリレーションシップ自体の削除時の両方で機能するからです。  ただし、参照リレーションシップの場合、関連要素が削除された場合に削除が伝達され、リレーションシップ自体が削除された場合は伝達されないようにすることをお勧めします。  次の例では、最後の貢献 Artist が削除されると Album が削除されますが、リレーションシップが削除されても応答しません。  
  
```  
using System.Linq; ...  
// Assumes a many-many reference relationship   
// between Artist and Album.    
partial class Artist  
{  
  protected override void OnDeleting()  
  {  
    base.OnDeleting();  
    if (this.Store.InUndoRedoOrRollback) return;  
    List<Album> toDelete = new List<Album>();  
    foreach (Album album in this.Albums)  
    {  
      if (album.Artists.Where(artist => !artist.IsDeleting)  
                        .Count() == 0)  
      {  
        toDelete.Add(album);  
      }  
    }  
    foreach (Album album in toDelete)  
    {  
      album.Delete();  
} } }  
  
```  
  
 要素で <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> を実行すると、OnDeleting および OnDeleted が呼び出されます。  これらのメソッドは常にインラインで実行されます。つまり、実際の削除の直前および直後に実行されます。  作成するコードが複数の要素を削除する場合、それらのすべてで OnDeleting と OnDeleted が交互に呼び出されることになります。  
  
##  <a name="rules"></a> 削除規則と削除イベント  
 OnDelete ハンドラーの代わりに、削除規則と削除イベントを定義できます。  
  
1.  **Deleting** 規則および **Delete** 規則はトランザクション内でのみトリガーされ、Undo または Redo ではトリガーされません。  それらを設定して、削除が実行されるトランザクションの最後に実行されるようにキューに配置できます。  Deleting 規則は常に、キューに配置されているすべての Deleted 規則の前に実行されます。  
  
     規則を使用し、リレーションシップ、図要素、およびそれらのプロパティなど、ストア内の要素にのみ影響する変更を伝達します。  通常、Deleting 規則は削除を伝達するために使用され、Delete 規則は置換要素およびリレーションシップを作成するために使用されます。  
  
     詳細については、「[ルールには、モデル内の変更が反映されるまでください。](../modeling/rules-propagate-changes-within-the-model.md)」を参照してください。  
  
2.  **Deleted** ストア イベントは、トランザクションの最後に呼び出され、undo または redo の後で呼び出されます。  したがって、ファイル、データベース エントリ、または [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内の他のオブジェクトなど、ストア外のオブジェクトに削除を伝達するために使用されます。  
  
     詳細については、「[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)」を参照してください。  
  
    > [!WARNING]
    >  要素が削除された場合、そのドメイン プロパティ値にアクセスできますが、リレーションシップ リンクに移動できません。  ただし、リレーションシップに deleted イベントを設定した場合、ロール プレーヤーだった 2 つの要素にもアクセスできます。  したがって、モデル要素の削除に応答し、リンクされた要素にアクセスする場合、モデル要素のドメイン クラスの代わりにリレーションシップで delete イベントを設定します。  
  
### 削除規則の例  
  
```  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletingRule : DeletingRule  
{  
  public override void ElementDeleting(ElementDeletingEventArgs e)  
  {  
    base.ElementDeleting(e);  
    // ...perform tasks to propagate imminent deletion  
  }  
}  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletedRule : DeleteRule  
{  
  public override void ElementDeleted(ElementDeletedEventArgs e)  
  {  
    base.ElementDeleted(e);  
    // ...perform tasks such as creating new elements  
  }  
}  
  
// The rule must be registered:  
public partial class MusicLibDomainModel  
{  
  protected override Type[] GetCustomDomainModelTypes()  
  {  
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
    types.Add(typeof(AlbumDeletingRule));  
    types.Add(typeof(AlbumDeletedRule));  
    // If you add more rules, list them here.   
    return types.ToArray();  
  }  
}  
  
```  
  
### Deleted イベントの例  
  
```  
partial class NestedShapesSampleDocData  
{  
  protected override void OnDocumentLoaded(EventArgs e)  
  {  
    base.OnDocumentLoaded(e);  
    DomainRelationshipInfo commentRelationship =   
          this.Store.DomainDataDirectory  
          .FindDomainRelationship(typeof(CommentsReferenceComponents));  
  
    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,  
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));  
  }  
  
  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)  
  {  
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;  
    Comment comment = link.Comment;  
    Component component = link.Subject;  
    if (comment.IsDeleted)  
    {  
      // The link was deleted because the comment was deleted.  
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);  
    }  
    else  
    {  
      // It was just the link that was deleted - the comment itself remains.  
      System.Windows.Forms.MessageBox.Show("Removed comment link to "   
           + component.Name);  
    }  
  }  
}  
  
```  
  
##  <a name="unmerge"></a> UnMerge  
 子要素をその親にアタッチする操作を*マージ*といいます。  マージは、新しい要素または要素のグループがツールボックスから作成されたとき、またはモデルの別の部分から移動されたとき、またはクリップボードからコピーされたときに発生します。  マージ操作は親とその新しい子の間に埋め込みリレーションシップを作成するほか、追加のリレーションシップのセットアップ、補助的な要素の作成、および要素内のプロパティ値の設定も可能です。  マージ操作は要素マージ ディレクティブ \(EMD\) にカプセル化されています。  
  
 EMD は補完的な *unmerge* または `MergeDisconnect` 操作もカプセル化します。  マージにより構築された要素のクラスターがある場合、残りの要素を一貫した状態のままにするには、関連する unmerge を使用して、そこから要素を削除することをお勧めします。  通常、unmerge 操作は前のセクションで説明している手法を使用します。  
  
 詳細については、「[要素作成処理および要素移動処理のカスタマイズ](../modeling/customizing-element-creation-and-movement.md)」を参照してください。  
  
## 参照  
 [コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)   
 [要素作成処理および要素移動処理のカスタマイズ](../modeling/customizing-element-creation-and-movement.md)   
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)
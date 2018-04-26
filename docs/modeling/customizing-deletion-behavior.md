---
title: 削除動作のカスタマイズ
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9942d9903188785af1658a37515092c3ce1ad2dd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-deletion-behavior"></a>削除動作のカスタマイズ
通常、要素を削除すると、関連する要素も削除されます。 接続されたすべてのリレーションシップと子要素が削除されます。 この動作の名前は*伝達の削除*です。 削除の伝達をカスタマイズできます。たとえば、追加の関連要素を削除することを準備できます。 プログラム コードを作成して、モデルの状態に応じた削除の伝達を実現できます。 削除に応じて他の変更を発生させることもできます。

 このトピックには、次のセクションがあります。

-   [既定値の削除の動作](#default)

-   [ロールの削除を伝達する オプションを設定](#property)

-   [削除クロージャをオーバーライドする](#closure)-この手法を使用して、削除が隣接する要素の削除になる可能性があります。

-   [OnDeleting および OnDeleted を使用して](#ondeleting)-これらのメソッドを使用して、応答が内側または外側、ストアの値の更新などその他のアクションを含めることができます。

-   [削除ルール](#rules)-任意の種類の 1 つの変更が他のユーザーになる可能性があります、ストア内の更新を伝達する規則を使用します。

-   [削除イベント](#rules)-その他の例に、ストア以外の更新を伝達する使用ストア イベント[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ドキュメント。

-   [結合解除](#unmerge)の子要素をその親にアタッチされているマージ操作を元に戻す、結合解除操作を使用します。

##  <a name="default"></a> 既定値の削除の動作
 既定では、次の規則が削除の伝達を制御します。

-   要素が削除された場合、埋め込まれたすべての要素も削除されます。 埋め込まれた要素は、この要素がソースである埋め込みリレーションシップのターゲットです。 埋め込みリレーションシップがある場合など**アルバム**に**曲**のすべての曲が削除されますも特定のアルバムを削除するとします。

     対照的に、ソングを削除してもアルバムは削除されません。

-   既定では、削除は参照リレーションシップに沿って伝達されません。 参照リレーションシップがある場合**ArtistPlaysOnAlbum**から**アルバム**に**アーティスト**アルバムを削除しても、関連する、アーティストは削除されません、アーティストの削除ではありません任意のアルバムを削除します。

     ただし、削除は一部の組み込みリレーションシップに沿って伝達されます。 たとえば、モデル要素が削除されると、その図形も図から削除されます。 要素を図形は `PresentationViewsSubject` 参照リレーションシップによって関連付けられています。

-   ソース ロールまたはターゲット ロールのいずれかで要素に接続されたすべてのリレーションシップは削除されます。 反対のロールの要素のロール プロパティには削除された要素が含まれなくなります。

##  <a name="property"></a> ロールの削除を伝達する オプションを設定
 削除によって参照リレーションシップに沿った伝達または埋め込まれた子から親への伝達を発生させることができます。

#### <a name="to-set-delete-propagation"></a>削除の伝達を設定するには

1.  DSL 定義ダイアグラムで、選択、*ロール*伝達を削除します。 ロールはドメイン リレーションシップ ボックスの左側または右側の線で表されます。

     たとえば、アルバムが削除された場合は常に関連するアーチストも削除されるように指定する場合、ドメイン クラス Artist に接続されたロールを選択します。

2.  [プロパティ] ウィンドウで、設定、**伝達の削除**プロパティです。

3.  F5 キーを押して、次のことを検証します。

    -   このリレーションシップのインスタンスが削除されると、選択したロールの要素も削除されます。

    -   反対のロールの要素が削除されると、このリレーションシップのインスタンスは削除され、このロールの関連要素は削除されます。

 表示することも、**伝達の削除**オプション、 **DSL 詳細**ウィンドウです。 ドメイン クラスを選択し、[DSL 詳細] ウィンドウで開きます、**削除時の動作**ページで、ウィンドウの横にあるボタンをクリックします。 **Propagate**各リレーションシップの反対側のロールのオプションを表示します。 **スタイルを削除**列を示すかどうか、 **Propagate**オプションの既定の設定でがまったく別の影響がないです。

## <a name="delete-propagation-by-using-program-code"></a>プログラム コードを使用する削除の伝達
 DSL 定義ファイル内のオプションにより選択できるのは、削除がすぐ隣に伝達するかどうかのみです。 より複雑な削除の伝達のしくみを実装するために、プログラム コードを作成できます。

> [!NOTE]
>  DSL 定義には、プログラム コードを追加するにで個別のコード ファイルを作成、 **Dsl**プロジェクトし、生成されたコード フォルダー内のクラスを拡張するために部分定義を記述します。 詳細については、次を参照してください。[ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)です。

##  <a name="closure"></a> Delete クロージャを定義します。
 削除操作は、クラスを使用して *YourModel***DeleteClosure** 指定の初期選択を削除する要素を確認します。 これは `ShouldVisitRelationship()` および `ShouldVisitRolePlayer()` を繰り返し呼び出し、リレーションシップのグラフを検索します。 これらのメソッドをオーバーライドできます。 ShouldVisitRolePlayer は、リンクおよびリンクのロールのいずれかの位置にある要素の id で提供されます。 次のいずれかの値を返す必要があります。

-   **VisitorFilterResult.Yes**-、要素を削除する必要がありを試す、ウォーカーを続行する必要があります、要素の他のリンク。

-   **VisitorFilterResult.DoNotCare** -削除するか別のクエリが応答しない限り、要素を削除できません必要があります。

-   **VisitorFilterResult.Never** -要素削除しないでください、場合でも、別のクエリに応答**はい**、しないでください、ウォーカーと要素の他のリンク。

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
        // Don't delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we're interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}

```

 このクロージャ手法により、削除する要素をリンクのセットが削除が始まる前に決定されることを確実にします。 また、ウォーカーはクロージャの結果をモデルの他の部分からの結果と結合します。

 ただし、この手法は削除がリレーションシップのグラフ内の隣にあるものにのみ影響することを仮定しています。この方法を使用してモデルの別の部分にある要素を削除することはできません。 削除に応じて要素を追加したり他の変更を実行したりする場合には使用できません。

##  <a name="ondeleting"></a> OnDeleting および OnDeleted を使用してください。
 ドメイン クラスまたはドメイン リレーションシップのいずれかで、`OnDeleting()` または `OnDeleted()` をオーバーライドできます。

1.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> は、要素が削除されようとしているときで、そのリレーションシップが切断されている前に呼び出されます。 まだ他の要素に対して移動可能で、`store.ElementDirectory` の中にあります。

     同時にいくつかの要素が削除される場合、削除の実行前にそれらすべてに対して OnDeleting が呼び出されます。

     `IsDeleting` は true です。

2.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> は要素が削除されると呼び出されます。 CLR ヒープ内に留まるので、必要があれば Undo を実行できますが、他の要素からのリンクは解除され、`store.ElementDirectory` から削除されます。 ロールをリレーションシップでは、古いロール プレーヤーを参照しています。`IsDeleted` true です。

3.  OnDeleting および OnDeleted は要素の作成後にユーザーが Undo を起動するとき、および以前の削除が Redo で繰り返されるときに呼び出されます。 これらの場合にストア要素の更新を回避するには `this.Store.InUndoRedoOrRollback` を使用します。 詳細については、次を参照してください。[する方法: モデルを更新するトランザクションを使用して](../modeling/how-to-use-transactions-to-update-the-model.md)です。

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

 多くの場合、ロール要素よりもリレーションシップの削除からトリガーする方が有用です。なぜなら、要素の削除時とリレーションシップ自体の削除時の両方で機能するからです。 ただし、参照リレーションシップの場合、関連要素が削除された場合に削除が伝達され、リレーションシップ自体が削除された場合は伝達されないようにすることをお勧めします。 次の例では、最後の貢献 Artist が削除されると Album が削除されますが、リレーションシップが削除されても応答しません。

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

 要素で <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A> を実行すると、OnDeleting および OnDeleted が呼び出されます。 これらのメソッドは常に実行されるインラインでは、直前と直後に実際の削除です。 作成するコードが複数の要素を削除する場合、それらのすべてで OnDeleting と OnDeleted が交互に呼び出されることになります。

##  <a name="rules"></a> 削除ルールとイベント
 OnDelete ハンドラーの代わりに、削除規則と削除イベントを定義できます。

1.  **削除する**と**削除**および元に戻す/やり直しではなく、トランザクションにのみ、ルールがトリガーされます。 それらを設定して、削除が実行されるトランザクションの最後に実行されるようにキューに配置できます。 Deleting 規則は常に、キューに配置されているすべての Deleted 規則の前に実行されます。

     規則を使用し、リレーションシップ、図要素、およびそれらのプロパティなど、ストア内の要素にのみ影響する変更を伝達します。 通常、Deleting 規則は削除を伝達するために使用され、Delete 規則は置換要素およびリレーションシップを作成するために使用されます。

     詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)です。

2.  **削除**ストア イベントが、トランザクションの終了時に呼び出され、元に戻す/やり直しの後に呼び出されます。 したがって、ファイル、データベース エントリ、または [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内の他のオブジェクトなど、ストア外のオブジェクトに削除を伝達するために使用されます。

     詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)です。

    > [!WARNING]
    >  要素が削除された場合、そのドメイン プロパティ値にアクセスできますが、リレーションシップ リンクに移動できません。 ただし、リレーションシップに deleted イベントを設定した場合、ロール プレーヤーだった 2 つの要素にもアクセスできます。 したがって、モデル要素を削除する応答が、リンクされた要素にアクセスする場合は、モデル要素のドメイン クラスの代わりに、リレーションシップを削除イベントを設定します。

### <a name="example-deletion-rules"></a>削除規則の例

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

### <a name="example-deleted-event"></a>Deleted イベントの例

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

##  <a name="unmerge"></a> 結合
 子要素をその親にアタッチ操作が呼び出された*マージ*です。 マージは、新しい要素または要素のグループがツールボックスから作成されたとき、またはモデルの別の部分から移動されたとき、またはクリップボードからコピーされたときに発生します。 マージ操作は親とその新しい子の間に埋め込みリレーションシップを作成するほか、追加のリレーションシップのセットアップ、補助的な要素の作成、および要素内のプロパティ値の設定も可能です。 マージ操作は要素マージ ディレクティブ (EMD) にカプセル化されています。

 EMD をカプセル化し、補完的な*結合*または`MergeDisconnect`操作します。 マージにより構築された要素のクラスターがある場合、残りの要素を一貫した状態のままにするには、関連する unmerge を使用して、そこから要素を削除することをお勧めします。 通常、unmerge 操作は前のセクションで説明している手法を使用します。

 詳細については、次を参照してください。[をカスタマイズする要素の作成および移動](../modeling/customizing-element-creation-and-movement.md)です。

## <a name="see-also"></a>関連項目

- [コピー動作のカスタマイズ](../modeling/customizing-copy-behavior.md)
- [要素作成処理および要素移動処理のカスタマイズ](../modeling/customizing-element-creation-and-movement.md)
- [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)
---
title: '方法: ショートカット メニューにコマンドを追加 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: cd550399-05fc-4dbf-be4c-f5094bb752ce
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c8230b8d37e0a853b22ac58fe1701a98728e41d3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246902"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>方法: ショートカット メニューにコマンドを追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ドメイン固有言語 (DSL) にメニュー コマンドを追加すると、ユーザーが DSL に固有のタスクを実行できるようになります。 ユーザーが図を右クリックすると、コンテキスト (ショートカット) メニューにコマンドが表示されます。 特定の状況でのみメニューにコマンドが表示されるように、コマンドを定義できます。 たとえば、ユーザーが特定の型の要素または特定の状態の要素をクリックした場合にだけコマンドを表示するようにできます。  
  
 DslPackage プロジェクトで実行する手順の概要を以下に示します。  
  
1.  [Commands.vsct でコマンドを宣言します。](#VSCT)  
  
2.  [Package.tt でパッケージのバージョン番号を更新](#version)します。 Commands.vsct を変更するときには必ずこの操作を実行してください。  
  
3.  [CommandSet クラスにメソッドを記述](#CommandSet)コマンドを表示して、定義を実行するコマンドにします。  
  
 サンプルについては、次を参照してください。、 [Visualization and Modeling SDK の web サイト](http://go.microsoft.com/fwlink/?LinkID=185579)します。  
  
> [!NOTE]
>  [切り取り]、[貼り付け]、[すべて選択]、[印刷] など、既存の一部のコマンドの動作を変更することもできます。このためには、CommandSet.cs でメソッドをオーバーライドします。 詳細については、次を参照してください。[方法: 標準メニュー コマンドを変更](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)します。  
  
## <a name="defining-a-command-using-mef"></a>MEF を使用したコマンドの定義  
 Managed Extension Framework (MEF) には、図のメニューのメニュー コマンドを定義するもう 1つの方法があります。 これは、ユーザーまたは他のユーザーが DSL を拡張できるようにすることを目的としています。 ユーザーは、DSL だけをインストールするか、または DSL と拡張機能の両方をインストールすることができます。 ただし MEF では、DSL で MEF を使用可能にする初期作業の完了後には、ショートカット メニュー コマンドの定義作業が少なくなります。  
  
 このトピックで説明する手法は、次の場合に使用してください。  
  
1.  右クリックで表示されるショートカット メニュー以外のメニューにメニュー コマンドを定義する。  
  
2.  メニューに特定のコマンド グループを定義する。  
  
3.  他のユーザーが各自のコマンドを使用して DSL を拡張できないようにする。  
  
4.  コマンドを 1 つだけ定義する。  
  
 上記に該当しない場合は、MEF 手法を使用してコマンドを定義することを検討してください。 詳細については、次を参照してください。 [MEF による DSL の拡張](../modeling/extend-your-dsl-by-using-mef.md)します。  
  
##  <a name="VSCT"></a> Commands.Vsct でコマンドを宣言します。  
 メニュー コマンドは、DslPackage\Commands.vsct で宣言されます。 これらの定義では、メニュー項目のラベルと、メニューでのメニュー項目の表示位置が指定されます。  
  
 編集するファイル Commands.vsct は、ディレクトリ内にある複数の .h ファイルから定義をインポートする*Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc します。また、DSL 定義から生成される GeneratedVsct.vsct をインクルードします。  
  
 .Vsct ファイルの詳細については、次を参照してください。 [Visual Studio Command Table (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
#### <a name="to-add-the-command"></a>コマンドを追加するには  
  
1.  **ソリューション エクスプ ローラー**下で、 **DslPackage**プロジェクトで、Commands.vsct を開きます。  
  
2.  `Commands` 要素に 1 つ以上のボタンと 1 つのグループを定義します。 A*ボタン*はメニュー アイテムです。 A*グループ*メニュー セクションします。 これらの項目を定義するため、次の要素を追加します。  
  
    ```  
    <!-- Define a group - a section in the menu -->  
    <Groups>  
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">  
        <!-- These symbols are defined in GeneratedVSCT.vsct -->  
        <Parent guid="guidCmdSet" id="menuidContext" />  
      </Group>  
    </Groups>  
    <!-- Define a button - a menu item - inside the Group -->  
    <Buttons>  
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        priority="0x0100" type="Button">  
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>  
        <!-- If you do not want to place the command in your own Group,   
             use Parent guid="guidCmdSet" id="grpidContextMain".  
             These symbols are defined in GeneratedVSCT.vsct -->  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <Strings>  
          <ButtonText>My Context Menu Command</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
    ```  
  
    > [!NOTE]
    >  各ボタンとグループは、GUID と整数の ID によって識別されます。 同じ GUID を使用して複数のグループとボタンを作成できます。 ただし、それぞれに異なる ID が必要です。 GUID 名と ID 名は、実際の Guid と数値 Id に変換されます、`<Symbols>`ノード。  
  
3.  ドメイン固有言語のコンテキストでのみコマンドが読み込まれるようにするため、コマンドに表示制限を追加します。 詳細については、次を参照してください。 [VisibilityConstraints 要素](../extensibility/visibilityconstraints-element.md)します。  
  
     このためには、`CommandTable` 要素内で `Commands` 要素の後に以下の要素を追加します。  
  
    ```  
    <VisibilityConstraints>  
      <!-- Ensures the command is only loaded for this DSL -->  
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        context="guidEditor"/>  
    </VisibilityConstraints>  
    ```  
  
4.  GUID と ID に使用する名前を定義します。 このためには、`Symbols` 要素内で `CommandTable` 要素の後に `Commands` 要素を追加します。  
  
    ```  
    <Symbols>  
      <!-- Substitute a unique GUID for the placeholder: -->  
      <GuidSymbol name="guidCustomMenuCmdSet"  
        value="{00000000-0000-0000-0000-000000000000}" >  
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>  
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>  
      </GuidSymbol>  
    </Symbols>  
    ```  
  
5.  `{000...000}` を、グループとメニュー項目を識別する GUID に置き換えます。 新しい GUID を取得するには、使用、 **GUID の作成**ツールを**ツール**メニュー。  
  
    > [!NOTE]
    >  さらにグループやメニュー項目を追加するときには、同じ GUID を使用できます。 ただし、`IDSymbols` に新しい値を使用する必要があります。  
  
6.  この手順からコピーしたコード内の、次の文字列をすべて各自固有の文字列に置き換えます。  
  
    -   `grpidMyMenuGroup`  
  
    -   `cmdidMyContextMenuCommand`  
  
    -   `guidCustomMenuCmdSet`  
  
    -   `My Context Menu Command`  
  
##  <a name="version"></a> Package.tt でパッケージ バージョンを更新します。  
 コマンドを追加または変更するたびに、`version` の <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> パラメーターを更新します。これは、ドメイン固有言語の新しいバージョンをリリースする前にパッケージ クラスに適用されます。  
  
 生成されるファイルでパッケージ クラスが定義されているため、Package.cs ファイルを生成するテキスト テンプレート ファイルで属性を更新します。  
  
#### <a name="to-update-the-packagett-file"></a>Package.tt ファイルを更新するには  
  
1.  **ソリューション エクスプ ローラー**で、 **DslPackage**プロジェクトの**GeneratedCode**フォルダーにある Package.tt ファイルを開きます。  
  
2.  `ProvideMenuResource` 属性を探します。  
  
3.  この属性の `version` パラメーター (2 番目のパラメーター) の値を大きくします。 必要に応じて、パラメーターの目的を明確にするためパラメーター名を明示的に記述できます。 例えば:  
  
     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`  
  
##  <a name="CommandSet"></a> コマンドの動作を定義します。  
 DSL には、DslPackage\GeneratedCode\CommandSet.cs で宣言される一部のクラスで実装されているコマンドが既に存在しています。 新しいコマンドを追加するには、同じクラスの部分的な宣言を含む新しいファイルを作成して、このクラスを拡張する必要があります。 通常、クラスの名前は *\<YourDslName >*`CommandSet`します。 最初にクラスの名前を検証し、クラスの内容を調べておくと便利です。  
  
 コマンド セット クラスは、<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> から派生しています。  
  
#### <a name="to-extend-the-commandset-class"></a>CommandSet クラスを拡張するには  
  
1.  ソリューション エクスプローラーで、DslPackage プロジェクト内の GeneratedCode フォルダーを開き、CommandSet.tt の下で、生成されたファイル CommandSet.cs を開きます。 名前空間と、名前空間で定義されている最初のクラスの名前を書きとめます。 たとえば、次のように表示されることがあります。  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  **DslPackage**、という名前のフォルダーを作成する**カスタム コード**します。 このフォルダーの作成という名前の新しいクラス ファイル`CommandSet.cs`します。  
  
3.  新しいファイル内に、生成された部分クラスと同じ名前空間および名前を持つ部分宣言を記述します。 例えば:  
  
     `namespace Company.Language1 /* Make sure this is correct */`  
  
     `{ internal partial class Language1CommandSet { ...`  
  
     **注**クラス テンプレートを使用して、新しいファイルを作成した場合は、名前空間とクラス名の両方を修正する必要があります。  
  
### <a name="extend-the-command-set-class"></a>CommandSet クラスを拡張する  
 通常、コマンド セット コードは次の名前空間をインポートする必要があります。  
  
```  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Design;   
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Shell;  
```  
  
 生成される CommandSet.cs の名前空間とクラス名に対応するように、この名前空間とクラス名を調整します。  
  
```  
namespace Company.Language1 /* Make sure this is correct */  
{  
  // Same class as the generated class.  
  internal partial class Language1CommandSet   
  {  
```  
  
 コンテキスト メニューにコマンドが表示される状況を判別するメソッドと、コマンドを実行するメソッドの 2 つを定義する必要があります。 これらのメソッドはオーバーライドではありません。コマンド リストにこれらのメソッドを登録します。  
  
### <a name="define-when-the-command-will-be-visible"></a>コマンドを表示する状況を定義します。  
 コマンドごとに、コマンドをメニューに表示するかどうか、およびコマンドを使用可能または灰色表示にするかを判別する `OnStatus...` メソッドを定義します。次の例に示すように、`Visible` の `Enabled` プロパティと `MenuCommand` プロパティを設定します。 このメソッドは、ユーザーが図を右クリックするたびに、ショートカット メニューを作成するために呼び出されるので、迅速に実行する必要があります。  
  
 この例では、ユーザーが特定の種類の図形を選択した場合にのみコマンドが表示され、選択した要素の少なくとも 1 つが特定の状態にある場合にのみ、このコマンドは使用可能になります。 この例は、クラス ダイアグラム DSL テンプレートに基づいており、ClassShape と ModelClass はこの DSL で定義されている型です。  
  
```  
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)  
{  
  MenuCommand command = sender as MenuCommand;  
  command.Visible = command.Enabled = false;  
  foreach (object selectedObject in this.CurrentSelection)  
  {  
    ClassShape shape = selectedObject as ClassShape;  
    if (shape != null)  
    {  
      // Visibility depends on what is selected.  
      command.Visible = true;  
      ModelClass element = shape.ModelElement as ModelClass;  
      // Enabled depends on state of selection.  
      if (element != null && element.Comments.Count == 0)  
      {  
        command.Enabled = true;  
        return; // seen enough  
} } } }  
```  
  
 次のフラグメントは、多くの場合 OnStatus メソッドで有効です。  
  
-   `this.CurrentSelection`。 ユーザーが右クリックした図形は常にこのリストに追加されます。 ユーザーが図の空白部分をクリックした場合、このリストのメンバーは図のみになります。  
  
-   `this.IsDiagramSelected()` - `true` 場合は、ユーザーは、図の空白部分をクリックしました。  
  
-   `this.IsCurrentDiagramEmpty()`  
  
-   `this.IsSingleSelection()` - ユーザーは複数のオブジェクトを選択しませんでした。  
  
-   `this.SingleSelection` - ユーザーが右クリックした図形または図  
  
-   `shape.ModelElement as MyLanguageElement` - 図形により表されるモデル要素。  
  
 一般的なガイドラインとして、`Visible` プロパティは選択した内容に基づくようにし、`Enabled` プロパティは選択した要素の状態に基づくようにします。  
  
 OnStatus メソッドは Store の状態を変更してはなりません。  
  
### <a name="define-what-the-command-does"></a>コマンドが実行する処理を定義する  
 コマンドごとに、ユーザーがメニュー コマンドをクリックしたときに必要な操作を実行する `OnMenu...` メソッドを定義します。  
  
 モデル要素を変更する場合は、トランザクション内部で変更を行う必要があります。 詳細については、次を参照してください。[方法: 標準メニュー コマンドを変更](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)します。  
  
 この例の `ClassShape`、`ModelClass`、および `Comment` は、クラス ダイアグラム DSL テンプレートから派生した DSL で定義されている型です。  
  
```  
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)  
{  
  MenuCommand command = sender as MenuCommand;  
  Store store = this.CurrentDocData.Store;  
  // Changes to elements and shapes must be performed in a Transaction.  
  using (Transaction transaction =  
       store.TransactionManager.BeginTransaction("My command"))  
  {  
    foreach (object selectedObject in this.CurrentSelection)  
    {  
      // ClassShape is defined in my DSL.  
      ClassShape shape = selectedObject as ClassShape;  
      if (shape != null)  
      {  
        // ModelClass is defined in my DSL.  
        ModelClass element = shape.ModelElement as ModelClass;  
        if (element != null)  
        {  
          // Do required action here - for example:  
  
          // Create a new element. Comment is defined in my DSL.  
          Comment newComment = new Comment(element.Partition);  
          // Every element must be the target of an embedding link.  
          element.ModelRoot.Comments.Add(newComment);  
          // Set properties of new element.  
          newComment.Text = "This is a comment";  
          // Create a reference link to existing object.  
          element.Comments.Add(newComment);  
        }  
      }  
    }  
    transaction.Commit(); // Don't forget this!  
  }  
}  
```  
  
 モデルでは、オブジェクト間を移動する方法およびオブジェクトとリンクを作成する方法についての詳細については、次を参照してください。[方法: 標準メニュー コマンドを変更](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)します。  
  
### <a name="register-the-command"></a>コマンドを登録する  
 CommandSet.vsct の Symbols セクションで記述した GUID 値と ID 値の宣言を C# で繰り返します。  
  
```  
private Guid guidCustomMenuCmdSet =   
    new Guid("00000000-0000-0000-0000-000000000000");  
private const int grpidMyMenuGroup = 0x01001;  
private const int cmdidMyContextMenuCommand = 1;  
```  
  
 同じ GUID 値を使用して、挿入した**Commands.vsct**します。  
  
> [!NOTE]
>  VSCT ファイルの Symbols セクションを変更する場合は、これらの宣言も一致するように変更する必要があります。 Package.tt でバージョン番号を増加する必要もあります。  
  
 メニュー コマンドをこのコマンド セットの一部として登録します。 図が初期化されると、`GetMenuCommands()` が 1 回呼び出されます。  
  
```  
protected override IList<MenuCommand> GetMenuCommands()  
{  
  // Get the list of generated commands.  
  IList<MenuCommand> commands = base.GetMenuCommands();  
  // Add a custom command:  
  DynamicStatusMenuCommand myContextMenuCommand =  
    new DynamicStatusMenuCommand(  
      new EventHandler(OnStatusMyContextMenuCommand),  
      new EventHandler(OnMenuMyContextMenuCommand),  
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));  
  commands.Add(myContextMenuCommand);  
  // Add more commands here.  
  return commands;  
}   
```  
  
## <a name="test-the-command"></a>コマンドをテストする  
 Visual Studio の実験用インスタンスで DSL をビルドして実行します。 指定した状況でこのコマンドがショートカット メニューに表示されるはずです。  
  
#### <a name="to-exercise-the-command"></a>コマンドを実行するには  
  
1.  **ソリューション エクスプ ローラー**ツールバーで、をクリックして**すべてのテンプレートの変換**します。  
  
2.  キーを押して**F5**をソリューションをリビルドし、実験用ビルドでドメイン固有言語のデバッグを開始します。  
  
3.  実験用ビルドでサンプルの図を開きます。  
  
4.  図の中のさまざまな項目を右クリックして、選択した項目に基づいてコマンドが正しく有効または無効になること、適切に表示または非表示になることを確認します。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 **コマンドは、メニューは表示されません。**  
  
-   DSL パッケージをインストールするまでは、コマンドは Visual Studio のデバッグ インスタンスでのみ表示されます。 詳細については、次を参照してください。[ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)します。  
  
-   実験用サンプルに、この DSL の正しいファイル名拡張子が含まれていることを確認します。 ファイル名拡張子を確認するには、Visual Studio のメイン インスタンスで DslDefinition.dsl を開きます。 DSL エクスプローラーで [エディター] プロジェクト ノードを右クリックし、[プロパティ] をクリックします。 [プロパティ] ウィンドウで、FileExtension プロパティを調べます。  
  
-   作成した[パッケージのバージョン番号をインクリメント](#version)でしょうか。  
  
-   OnStatus メソッドの開始時にブレークポイントを設定します。 このブレークポイントは、図の任意の部分を右クリックしたときにブレークする必要があります。  
  
     **OnStatus メソッドは呼び出されません**:  
  
    -   CommandSet コードの GUID と ID が Commands.vsct の Symbols セクションの GUID と ID に一致することを確認します。  
  
    -   Commands.vsct ですべての親ノードの GUID と ID が正しい親グループを識別していることを確認します。  
  
    -   Visual Studio コマンド プロンプトで devenv /rootsuffix exp /setup と入力します。 Visual Studio のデバッグ インスタンスを再起動します。  
  
-   OnStatus メソッドをステップ実行し、command.Visible と command.Enabled が true に設定されていることを確認します。  
  
 **誤ったメニュー テキストが表示されたら、または間違った場所にコマンドが表示される**:  
  
-   GUID と ID の組み合わせがこのコマンドに固有であることを確認します。  
  
-   パッケージの古いバージョンがアンインストールされていることを確認します。  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [方法: 標準メニュー コマンドを修正](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)   
 [ドメイン固有言語ソリューションの配置](../modeling/deploying-domain-specific-language-solutions.md)   
 [サンプル コード: 回路図](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)




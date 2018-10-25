---
title: '方法: ドメイン固有言語における標準のメニュー コマンドの変更 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3d29a501ef6f55c835efd68e474bc39a847f745d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837567"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>方法: ドメイン固有言語における標準のメニュー コマンドを修正する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL で自動的に定義される標準コマンドのいくつかの動作を変更できます。 たとえば、変更する可能性があります**切り取り**機密情報を除外することです。 そのためには、コマンド セット クラス内でメソッドをオーバーライドします。 これらのクラスは DslPackage プロジェクト内の CommandSet.cs ファイルで定義され、<xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> から派生します。  
  
 要約すると、コマンドを変更するには以下の操作を実行します。  
  
1. [コマンドを変更することを検出](#what)します。  
  
2. [適切なコマンド セット クラスの部分宣言を作成](#extend)です。  
  
3. [ProcessOnStatus および ProcessOnMenu メソッドをオーバーライド](#override)コマンド。  
  
   このトピックではこの手順を説明します。  
  
> [!NOTE]
>  独自のメニュー コマンドを作成する場合を参照してください。[方法: ショートカット メニューにコマンドを追加](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)します。  
  
##  <a name="what"></a> どのようなコマンドを変更できますか。  
  
#### <a name="to-discover-what-commands-you-can-modify"></a>変更可能なコマンドを見つけるには  
  
1.  `DslPackage`プロジェクトを開き、`GeneratedCode\CommandSet.cs`します。 この c# ファイルは、の従属としてソリューション エクスプ ローラーで見つかんだことができます`CommandSet.tt`します。  
  
2.  このファイルにクラスを見つけることで名前の末尾が"`CommandSet`"、たとえば`Language1CommandSet`と`Language1ClipboardCommandSet`。  
  
3.  各コマンド セット クラスで、"`override`" とその後に続けて空白文字を 1 つ入力します。 IntelliSense ではオーバーライド可能なメソッドの一覧が表示されます。 各コマンドには名前が "`ProcessOnStatus`" および "`ProcessOnMenu`" で始まるメソッドのペアが含まれます。  
  
4.  変更するコマンドを含むコマンド セット クラスをメモします。  
  
5.  編集内容を保存せずにファイルを閉じます。  
  
    > [!NOTE]
    >  通常、生成されたファイルを編集できません。 次回ファイルが生成されたときに編集内容は失われます。  
  
##  <a name="extend"></a> 適切なコマンド セット クラスを拡張します。  
 コマンド セット クラスの部分宣言を含む新しいファイルを作成します。  
  
#### <a name="to-extend-the-command-set-class"></a>コマンド セット クラスを拡張するには  
  
1.  ソリューション エクスプローラーで、DslPackage プロジェクト内の GeneratedCode フォルダーを開き、CommandSet.tt の下で、生成されたファイル CommandSet.cs を開きます。 名前空間と、名前空間で定義されている最初のクラスの名前を書きとめます。 たとえば、次のように表示されることがあります。  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  **DslPackage**、という名前のフォルダーを作成する**カスタム コード**します。 このフォルダーの作成という名前の新しいクラス ファイル`CommandSet.cs`します。  
  
3.  新しいファイル内に、生成された部分クラスと同じ名前空間および名前を持つ部分宣言を記述します。 例えば:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Design;  
    namespace Company.Language1 /* Make sure this is correct */  
    { internal partial class Language1CommandSet { ...  
    ```  
  
     **注**クラス ファイル テンプレートを使用して、新しいファイルを作成した場合は、名前空間とクラス名の両方を修正する必要があります。  
  
##  <a name="override"></a> コマンド メソッドをオーバーライドします。  
 ほとんどのコマンドは、2 つの関連付けられているメソッドを持つ: などの名前を持つメソッド`ProcessOnStatus`... コマンドを表示して有効にするかどうかを決定します。 このメソッドはユーザーが図を右クリックするたびに呼び出され、すばやく実行し、何の変更も生じません。 `ProcessOnMenu`... ユーザーが、コマンドをクリックし、コマンドの関数を実行するときに呼び出されます。 これらのメソッドの一方または両方をオーバーライドする場合があります。  
  
### <a name="to-change-when-the-command-appears-on-a-menu"></a>メニュー上にコマンドが表示されるタイミングを変更するには  
 Processonstatus. メソッド。 このメソッドは、パラメーター MenuCommand の Visible プロパティおよび Enabled プロパティを設定します。 通常、コマンドは this.CurrentSelection を見て、コマンドが選択された要素に適用されるかどうかを判断し、それらのプロパティを見て、コマンドが現在の状態で適用可能かどうかを判断します。  
  
 一般的なガイドとして、Visible プロパティは選択される要素により判断する必要があります。 Enabled プロパティは、コマンドがメニュー上に黒で表示されるかグレーで表示されるかを決め、現在の選択状態に依存します。  
  
 以下の例では、ユーザーが複数の図形を選択している場合、[削除] メニュー項目が無効になります。  
  
> [!NOTE]
>  このメソッドはコマンドがキーストロークにより使用可能かどうかに影響しません。 たとえば、[削除] メニュー項目を無効化しても、コマンドが Delete キーから呼び出されるのを妨げません。  
  
```  
/// <summary>  
/// Called when user right-clicks on the diagram or clicks the Edit menu.  
/// </summary>  
/// <param name="command">Set Visible and Enabled properties.</param>  
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)  
{  
  // Default settings from the base method.  
  base.ProcessOnStatusDeleteCommand(command);  
  if (this.CurrentSelection.Count > 1)  
  {  
    // If user has selected more than one item, Delete is greyed out.  
    command.Enabled = false;  
  }  
}  
```  
  
 最初に基本的なメソッドを呼び出し、関係のないケースおよび設定のすべてに対処することを推奨します。  
  
 ProcessOnStatus メソッドは、ストア内の要素の作成、削除、または更新を実行しません。  
  
### <a name="to-change-the-behavior-of-the-command"></a>コマンドの動作を変更するには  
 Processonmenu. メソッド。 以下の例では、Delete キーを使用しても、ユーザーは一度に複数の要素を削除できません。  
  
```  
/// <summary>  
/// Called when user presses Delete key   
/// or clicks the Delete command on a menu.  
/// </summary>  
protected override void ProcessOnMenuDeleteCommand()  
{  
  // Allow users to delete only one thing at a time.  
  if (this.CurrentSelection.Count <= 1)  
  {  
    base.ProcessOnMenuDeleteCommand();  
  }  
}  
```  
  
 要素またはリンクの作成、削除、または更新など、コードがストアに対して変更を加える場合、トランザクション内でそれを実行する必要があります。 詳細については、次を参照してください。[モデル要素を作成し、更新する方法](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)します。  
  
### <a name="writing-the-code-of-the-methods"></a>メソッドのコードの記述  
 次のコード片はこれらのメソッド内で頻繁に役立ちます。  
  
- `this.CurrentSelection`。 ユーザーが右クリックした図形は常にこの図形およびコネクタの一覧に含まれます。 ユーザーが図の空白部分をクリックした場合、このリストのメンバーは図のみになります。  
  
- `this.IsDiagramSelected()` - `true` 場合は、ユーザーは、図の空白部分をクリックしました。  
  
- `this.IsCurrentDiagramEmpty()`  
  
- `this.IsSingleSelection()` - ユーザーは複数の図形を選択しませんでした  
  
- `this.SingleSelection` - ユーザーが右クリックした図形または図  
  
- `shape.ModelElement as MyLanguageElement` - 図形により表されるモデル要素。  
  
  要素間を移動する方法およびオブジェクトとリンクを作成する方法についての詳細については、次を参照してください。[を移動すると、プログラム コードでのモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.Design.MenuCommand>   
 [ドメイン固有言語をカスタマイズするコードの記述](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [方法: ショートカット メニューにコマンドを追加](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)   
 [チュートリアル: 選択されたリンクからの情報の取得](../misc/walkthrough-getting-information-from-a-selected-link.md)   
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../extensibility/vsct-xml-schema-reference.md)   
 [VMSDK – 回路図のサンプルです。広範な DSL のカスタマイズ](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)   
 [サンプル コード: 回路図](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)




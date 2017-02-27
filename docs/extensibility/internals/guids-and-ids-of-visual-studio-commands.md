---
title: "Guid と、Visual Studio コマンドの Id | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンド"
  - "ID"
  - "コマンドの配置"
  - "visual studio コマンド"
  - "guid"
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Guid と、Visual Studio コマンドの Id
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 統合開発環境に含まれる Visual Studio SDK の一部としてインストール \(IDE\) .vsct ファイルでコマンドの GUID と ID の値が定義されます。  詳細については、「[IDE 定義コマンド、メニューのおよびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)」を参照してください。  
  
 .vsct ファイルで定義されている IDE オブジェクトを使用する方法の詳細については[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md) を参照してください。  
  
## コマンド定義を見つけます  
 Visual Studio は千以上のコマンドを定義するためすべてを次に示します。現実的ではありません。  代わりにコマンドの定義を検索するには次の手順に従います。  
  
#### コマンドを定義するには  
  
1.  Visual Studio で*Visual Studio SDK インストール パス* \\ VisualStudioIntegration \\ Common \\ フォルダーは次のファイルを開きます : SharedCmdDef.vsctShellCmdDef.vsctVsDbgCmdUsed.vsctVenusmenu.vsct。  
  
     Visual Studio のほとんどのコマンドは SharedCmdDef.vsct と ShellCmdDef.vsct で定義されます。  VsDbgCmdUsed.vsct はデバッガーに関連するVenusmenu.vsct はWeb 開発に固有のコマンドを定義するコマンドを定義します。  
  
2.  コマンドがメニュー項目メニュー項目の内容を正確にメモします。  コマンドをツール バー ボタンプロパティを置いたときに表示されるツール ヒント テキストが表示されます。  
  
3.  \[ENT1ENT\] ダイアログ ボックスを表示するにはCtrl キーを押します。  
  
4.  \[入力\] ENT0ENT ボックスので手順 2. で確認したテキストを入力します。  
  
5.  **すべての開かれているドキュメント**  が ENT1ENT \[入力\] のボックスに表示されることを確認します。  
  
6.  テキストが [Button 要素](../../extensibility/button-element.md) の `<Strings>` のセクションで選択されるまで ENT0ENT \[入力\] ボタンをクリックします。  
  
     コマンドが表示される `<Button>` の要素がコマンド定義です。  
  
 コマンド定義を検索したり別のメニューまたはツール バーに [CommandPlacement 要素](../../extensibility/commandplacement-element.md) のコマンドと同じ `id` の `guid` と値を含むを作成してコマンドのコピーを配置できます。  詳細については、「[ボタンの再利用可能なグループを作成します。](../../extensibility/creating-reusable-groups-of-buttons.md)」を参照してください。  
  
### 特殊なケース  
 次の場合メニューのテキストまたはツール ヒント テキストはの内容をコマンド シグネチャと一致しない場合があります。  
  
-   P が下線付き ENT3ENT \[入力\] メニューの  **印刷**  のコマンドなどの下線付きの文字を含むメニュー項目。  
  
     "  メニュー項目の名前の文字が前に付いた文字は下線付きで表示されます。  ただし.vsct ファイルは特殊文字を示すために "  文字を使用しディスプレイアンパサンド必要がある XML で記述され"  綴られなければ必要があります。  したがって.vsct ファイルで印刷コマンドは "  として表示されます。  
  
-   動的テキスト **保存**  *現在のファイル名*  など動的に生成されたメニュー項目がある \[入力\] ENT1ENT リスト内の項目などコマンド。  
  
     動的テキストを検索する信頼性の高い方法はありません。  代わりに[Guid と Visual Studio のメニューの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) または [Guid と Visual Studio ツールバーの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md) の参照でホストされそのグループ ID の検索を目的のコマンド グループを検索します。  コマンド定義に [Parent 要素](../../extensibility/parent-element.md) としてコマンド グループの親を設定する `<CommandPlacement>` の要素のデバッガー コマンドの検索 SharedCmdPlace.vsct と ShellCmdPlace.vsct \(または\) VsDbgCmdPlace.vsct があります。  SharedCmdPlace.vsctShellCmdPlace.vsctandVsDbgCmdPlace.vsct は *Visual Studio SDK インストール パス* \\ VisualStudioIntegration \\ Common は\\ フォルダーにあります。  
  
## 参照  
 [MenuCommand と  OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)
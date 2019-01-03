---
title: Visual Studio のコマンドの Guid および Id |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1440eb7da0299b79aa063d999d581cc159a88e50
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898295"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>コマンドの Guid と Visual Studio の Id
Visual Studio 統合開発環境 (IDE) で含まれているコマンドの GUID と ID の値は、Visual Studio SDK の一部としてインストールされている .vsct ファイルで定義されます。 詳細については、次を参照してください。 [IDE 定義コマンド、メニュー、およびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)します。  
  
 定義されている IDE オブジェクトを操作する方法の詳細についての *.vsct*ファイルを参照してください[メニューとコマンドの拡張](../../extensibility/extending-menus-and-commands.md)します。  
  
## <a name="find-a-command-definition"></a>コマンドの定義が見つかりません  
 Visual Studio では、1000 台以上のコマンドを定義するためすべてここに列挙するは実用的ではありません。 代わりに、以下の手順を実行するコマンドの定義を探します。  
  
### <a name="to-locate-a-command-definition"></a>コマンド定義を検索するには  
  
1. Visual Studio で、次のファイルを開く、 *< Visual Studio SDK インストール パス\>\VisualStudioIntegration\Common\Inc\\* フォルダー。*SharedCmdDef.vsct*、 *ShellCmdDef.vsct*、 *VsDbgCmdUsed.vsct*、 *Venusmenu.vsct*します。  
  
    ほとんどの Visual Studio のコマンドがで定義されている*SharedCmdDef.vsct*と*ShellCmdDef.vsct*します。 *VsDbgCmdUsed.vsct* 、デバッガーに関連するコマンドを定義し、 *Venusmenu.vsct* Web 開発に固有のコマンドを定義します。  
  
2. コマンドがメニュー項目の場合は、メニュー項目の内容を正確に注意してください。 コマンドがツールバーのボタンの場合は、それを一時停止するときに表示されるツールヒント テキストを注意してください。  
  
3. キーを押して**Ctrl**+**F**を開く、**検索** ダイアログ ボックス。  
  
4. **検索**ボックスに、手順 2. でメモしたテキストを入力します。  
  
5. いることを確認**すべての開いているドキュメント**に表示される、**ファイルの場所**ボックス。  
  
6. をクリックして、**次を検索**で、テキストが選択されるまで、`<Strings>`のセクションを[ボタン要素](../../extensibility/button-element.md)します。  
  
    `<Button>`コマンドが含まれている要素がコマンド定義。  
  
   コマンドの定義が見つかったら、別のメニューまたはツールバーのコマンドのコピーを配置を作成して、 [CommandPlacement 要素](../../extensibility/commandplacement-element.md)を持つ同じ`guid`と`id`コマンドと値。 詳細については、次を参照してください。[ボタンの再利用可能なグループ作成](../../extensibility/creating-reusable-groups-of-buttons.md)です。  
  
### <a name="special-cases"></a>特殊なケース  
 次の場合、メニュー テキストまたはツールヒントのテキストが一致しない一致コマンド定義でです。  
  
-   など、下線付きの文字を含むメニュー項目、**印刷**コマンドを**ファイル**をメニュー、 *P*下線が引かれます。  
  
     前にアンパサンド文字 (&) メニュー項目名の文字を表示、下線が引かれました。 ただし、 *.vsct*ファイルはアンパサンド (&) を使用して、特殊文字を指定し、として表示するには、アンパサンドをスペルする必要があることが必要ですが XML で記述された *&amp;amp;* します。 そのため、 *.vsct*ファイル、**印刷**としてコマンドが表示される *&amp;amp;印刷*します。  
  
-   コマンドのテキストを動的をなどが含まれない**保存**\<現在のファイル名\>で項目などのメニュー項目を動的に生成されると、**最近使ったファイル**一覧。  
  
     動的テキストを検索する確実な方法はありません。 代わりを参照して目的のコマンドをホストするグループを検索[Guid と Visual Studio の Id のメニュー](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)または[Guid と Visual Studio の Id のツールバー](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)、およびそのグループの ID で検索します。 コマンドの定義としてグループを持たないかどうか、[親要素](../../extensibility/parent-element.md)、検索*SharedCmdPlace.vsct*と*ShellCmdPlace.vsct* (または*VsDbgCmdPlace.vsct*のデバッガー コマンド) を`<CommandPlacement>`コマンドの親を設定する要素。 *SharedCmdPlace.vsct*、 *ShellCmdPlace.vsct*、および*VsDbgCmdPlace.vsct*では、 *\<Visual Studio SDK インストール パス\>\VisualStudioIntegration\Common\Inc\\*フォルダー。  
  
## <a name="see-also"></a>関連項目  
 [Menucommand とOleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio コマンド テーブル (.vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)

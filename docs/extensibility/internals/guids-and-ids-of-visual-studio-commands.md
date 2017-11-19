---
title: "Visual Studio のコマンドの Guid と Id |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ce546f36ed93f0f42bfd548c64f2a25669e162b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio のコマンドの Guid と Id
Visual Studio 統合開発環境 (IDE) に含まれるコマンドの GUID と ID の値は、Visual Studio SDK の一部としてインストールされている .vsct ファイルで定義されます。 詳細については、次を参照してください。 [IDE-Defined コマンド、メニュー、およびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)です。  
  
 .Vsct ファイルで定義されている IDE オブジェクトを操作する方法の詳細については、次を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)です。  
  
## <a name="finding-a-command-definition"></a>コマンド定義を検索します。  
 Visual Studio では、1,000 を超えるコマンドを定義するため、ここに一覧にすべて実用的ではありません。 代わりに、次の手順のコマンドの定義を見つけます。  
  
#### <a name="to-locate-a-command-definition"></a>コマンド定義を検索するには  
  
1.  Visual Studio での次のファイルを開き、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc\ フォルダー: SharedCmdDef.vsct、ShellCmdDef.vsct、VsDbgCmdUsed.vsct、Venusmenu.vsct です。  
  
     Visual Studio のほとんどのコマンドは、SharedCmdDef.vsct と ShellCmdDef.vsct で定義されます。 VsDbgCmdUsed.vsct が、デバッガーに関連するコマンドを定義し、Venusmenu.vsct を Web 開発に固有のコマンドを定義します。  
  
2.  コマンドがメニュー項目の場合は、メニュー項目の内容を正確に注意してください。 コマンドは、ツールバーのボタンは場合、は、それを一時停止するときに表示されるツールヒント テキストをメモします。  
  
3.  開くには ctrl キーを押しながら F キーを押して、**検索** ダイアログ ボックス。  
  
4.  **検索**ボックスに、手順 2. でメモしたテキストを入力します。  
  
5.  いることを確認**すべての開いているドキュメント**に表示される、**ファイルの場所**ボックス。  
  
6.  クリックして、**次を検索**で、テキストが選択されるまで、`<Strings>`のセクション、[ボタン要素](../../extensibility/button-element.md)です。  
  
     `<Button>`コマンドが含まれている要素は、コマンドが定義されます。  
  
 コマンドの定義が見つかったら、別のメニューまたはツールバーのコマンドのコピーする配置を作成して、 [CommandPlacement 要素](../../extensibility/commandplacement-element.md)を持つ同じ`guid`と`id`コマンドとして値。 詳細については、次を参照してください。[ボタンの再利用可能なグループの作成](../../extensibility/creating-reusable-groups-of-buttons.md)です。  
  
### <a name="special-cases"></a>特殊なケース  
 次の場合、メニュー テキストやツールヒント テキスト可能性があります完全に一致しないコマンド定義には、新機能です。  
  
-   メニュー項目など、下線付き文字が含まれている、**印刷**コマンドを**ファイル**] メニューの [、P が下線が表示されます。  
  
     メニュー項目名に '&' 文字に続く文字が表示される、下線付きです。 ただし、.vsct ファイルは、XML では、特殊文字を示すために '&' 文字を使用し表示するのには、アンパサンドを綴る必要がありますが必要です。 で記述された '&amp;' です。 したがって、.vsct ファイルで、 **P**rint コマンドとして表示されます '&amp;印刷' です。  
  
-   などを持つ動的テキストは、コマンド**保存***現在のファイル名*で、項目などのメニュー項目を動的に生成されると、**最近使ったファイル** ボックスの一覧です。  
  
     動的なテキストを検索する確実な方法はありません。 コンサルティングで目的のコマンドをホストするグループを検索する代わりに、 [Guid と Visual Studio メニューの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)または[Guid と Visual Studio ツールバーの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)、そのグループの ID で検索しています。 かどうか、コマンドの定義はありません、グループとしてその[親要素](../../extensibility/parent-element.md)、SharedCmdPlace.vsct ShellCmdPlace.vsct (またはデバッガー コマンドを VsDbgCmdPlace.vsct) 検索、`<CommandPlacement>`の親を設定する要素のコマンド。 SharedCmdPlace.vsct、ShellCmdPlace.vsct、andVsDbgCmdPlace.vsct はでは、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc\ フォルダーです。  
  
## <a name="see-also"></a>関連項目  
 [MenuCommand と OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)
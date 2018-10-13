---
title: Visual Studio のコマンドの Guid および Id |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93efc7bfec5f4ba3e545dec7fff57f73e49260d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302446"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio コマンドの GUID および ID
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 統合開発環境 (IDE) で含まれているコマンドの GUID と ID の値は、Visual Studio SDK の一部としてインストールされている .vsct ファイルで定義されます。 詳細については、次を参照してください。 [IDE-Defined コマンド、メニュー、およびグループ](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)します。  
  
 .Vsct ファイルで定義されている IDE オブジェクトを操作する方法の詳細については、次を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
## <a name="finding-a-command-definition"></a>コマンド定義の検索  
 Visual Studio では、1,000 を超えるコマンドを定義するためすべてここに列挙するは実用的ではありません。 代わりに、以下の手順を実行するコマンドの定義を探します。  
  
#### <a name="to-locate-a-command-definition"></a>コマンド定義を検索するには  
  
1.  Visual Studio で、次のファイルを開く、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc\ フォルダー: SharedCmdDef.vsct、ShellCmdDef.vsct、VsDbgCmdUsed.vsct、Venusmenu.vsct します。  
  
     ほとんどの Visual Studio のコマンドは、SharedCmdDef.vsct と ShellCmdDef.vsct で定義されます。 VsDbgCmdUsed.vsct がデバッガーに関連するコマンドを定義し、Venusmenu.vsct Web 開発に固有のコマンドを定義します。  
  
2.  コマンドがメニュー項目の場合は、メニュー項目の内容を正確に注意してください。 コマンドがツールバーのボタンの場合は、それを一時停止するときに表示されるツールヒント テキストを注意してください。  
  
3.  開くには、CTRL + F キーを押して、**検索** ダイアログ ボックス。  
  
4.  **検索**ボックスに、手順 2. でメモしたテキストを入力します。  
  
5.  いることを確認**すべての開いているドキュメント**に表示される、**ファイルの場所**ボックス。  
  
6.  をクリックして、**次を検索**で、テキストが選択されるまで、`<Strings>`のセクションを[ボタン要素](../../extensibility/button-element.md)します。  
  
     `<Button>`コマンドが含まれている要素がコマンド定義。  
  
 コマンドの定義が見つかったら、別のメニューまたはツールバーのコマンドのコピーを配置を作成して、 [CommandPlacement 要素](../../extensibility/commandplacement-element.md)を持つ同じ`guid`と`id`コマンドと値。 詳細については、次を参照してください。[ボタンの再利用可能なグループの作成](../../extensibility/creating-reusable-groups-of-buttons.md)です。  
  
### <a name="special-cases"></a>特殊なケース  
 次の場合、メニュー テキストまたはツールヒントのテキストが一致しない一致コマンド定義でです。  
  
-   など、下線付きの文字を含むメニュー項目、**印刷**コマンドを**ファイル**] メニューの [、P に下線が付いています。  
  
     メニュー項目の名前で '&' 文字が付いている文字が表示されます、下線が引かれました。 ただし、.vsct ファイルが XML では、特殊文字を示すために '&' 文字を使用し、表示するのには、アンパサンドを綴る必要がありますが必要、で記述 '&amp;'。 そのため、.vsct ファイルで、 **P**として rint コマンドが表示されます '&amp;印刷 '。  
  
-   コマンドのテキストを動的をなどが含まれない**保存***現在のファイル名*で項目などのメニュー項目を動的に生成されると、**最近使ったファイル**一覧。  
  
     動的テキストを検索する確実な方法はありません。 代わりを参照して目的のコマンドをホストするグループを検索[Guid と Visual Studio メニューの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)または[Guid と Visual Studio ツールバーの Id の](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)とそのグループの ID を検索します。 コマンドの定義としてグループを持たないかどうか、[親要素](../../extensibility/parent-element.md)、SharedCmdPlace.vsct と ShellCmdPlace.vsct (または VsDbgCmdPlace.vsct のデバッガー コマンド) を検索、`<CommandPlacement>`の親を設定する要素、コマンド。 SharedCmdPlace.vsct、ShellCmdPlace.vsct、andVsDbgCmdPlace.vsct はでは、 *Visual Studio SDK インストール パス*\VisualStudioIntegration\Common\Inc\ フォルダー。  
  
## <a name="see-also"></a>関連項目  
 [MenuCommand と OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)


---
title: "[オプション] ダイアログ ボックス (Visual Studio) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 19
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 127a28e735b72d836c1a98044b3e8b95e13f5c54
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# [オプション] ダイアログ ボックス (Visual Studio)
<a id="options-dialog-box-visual-studio" class="xliff"></a>
**[オプション]** ダイアログ ボックスでは、必要に応じて統合開発環境 (IDE) を構成することができます。 たとえば、プロジェクトの既定の保存場所の確立、ウィンドウの既定の外観や動作の変更、よく使用されるコマンドのショートカットの作成などを行うことができます。 開発言語やプラットフォームに固有のオプションもあります。 **[オプション]** には **[ツール]** メニューからアクセスできます。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ダイアログ ボックスで使用可能なオプションや、メニュー コマンドの名前や位置がヘルプに記載されている内容と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## [オプション] ダイアログ ボックスのレイアウト
<a id="layout-of-the-options-dialog-box" class="xliff"></a>  
 **[オプション]** ダイアログ ボックスは 2 つの部分 (左側のナビゲーション ウィンドウと右側の表示領域) に分かれています。 ナビゲーション ウィンドウのツリー コントロールには、[環境]、[テキスト エディター]、[プロジェクトおよびソリューション]、および [ソース管理] などのフォルダー ノードが含まれています。 任意のフォルダー ノードを展開すると、その中に含まれるオプションのページがリストされます。 特定のページのノードを選択すると、表示領域にそのオプションが表示されます。  
  
 IDE 機能のオプションは、この機能がメモリに読み込まれるまでは、ナビゲーション ウィンドウには表示されません。 したがって、前のセッションを終了したときに表示されていたオプションが、新規セッションを開始した時点では表示されない場合があります。 プロジェクトを作成するか、特定のアプリケーションを使用するコマンドを実行すると、関連するオプションのノードが [オプション] ダイアログ ボックスに追加されます。 追加されたこれらのオプションは、IDE 機能がメモリにある限り有効です。  
  
> [!NOTE]
>  一部の設定コレクションでは、[オプション] ダイアログ ボックスのナビゲーション ウィンドウに表示されるページ数のスコープが設定されます。 **[すべての設定を表示]** を選択すると、使用可能なすべてのページを表示できます。  
  
## オプションの適用方法
<a id="how-options-are-applied" class="xliff"></a>  
 **[オプション]** ダイアログ ボックスで [OK] をクリックすると、すべてのページのすべての設定が保存されます。 任意のページで [キャンセル] をクリックすると、他の **[オプション]** ページで行ったものを含め、すべての変更要求がキャンセルされます。 [[フォントおよび色] ([オプション] ダイアログ ボックス - [環境])](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md) での変更など、オプション設定に加えた一部の変更は、Visual Studio を閉じて再度開いたときに初めて有効になります。  
  
### すべての設定を表示
<a id="show-all-settings" class="xliff"></a>  
 **[すべての設定を表示]** のオンまたはオフの操作は、**[OK]** をクリックしていなくても、**[オプション]** ダイアログ ボックスで行ったすべての変更に適用されます。  
  
## 関連項目
<a id="see-also" class="xliff"></a>  
 [エディターのカスタマイズ](../../ide/customizing-the-editor.md)

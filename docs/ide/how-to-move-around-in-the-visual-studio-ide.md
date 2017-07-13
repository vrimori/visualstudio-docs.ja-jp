---
title: "方法: Visual Studio IDE 内で移動する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
caps.latest.revision: 25
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
ms.openlocfilehash: 9ca6b957f3ebc2770bed91e5ca27ec3f95715aa9
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# 方法: Visual Studio IDE 内で移動する
<a id="how-to-move-around-in-the-visual-studio-ide" class="xliff"></a>
統合開発環境 (IDE) は、ユーザー設定やプロジェクトの要件に応じて、いくつかの異なる方法で、ウィンドウからウィンドウへ、またはファイルからファイルへ移動できるように設計されています。 エディターで開いているファイルを順番に表示することも、IDE 内でアクティブなすべてのツール ウィンドウを順番に表示することもできます。 また、最後にアクセスした順序に関係なく、エディターで開いている任意のファイルに直接切り替えることもできます。 これらの機能は、IDE で作業するときの生産性を向上するのに役立ちます。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ダイアログ ボックスで使用可能なオプションや、メニュー コマンドの名前や位置がヘルプに記載されている内容と異なる場合があります。 このヘルプ ページは、**全般的な開発設定**を考慮して記述されています。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## ショートカット キー
<a id="keyboard-shortcuts" class="xliff"></a>  
 Visual Studio のほぼすべてのメニュー コマンドにはショートカット キーがあります。 独自のカスタム ショートカットを作成することもできます。 詳細については、「[Visual Studio でのキーボード ショートカットの識別とカスタマイズ](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)」をご覧ください。  
  
## エディターでファイル間を移動する
<a id="navigating-among-files-in-the-editor" class="xliff"></a>  
 エディターで開いているファイル間を移動する方法はいくつかあります。 アクセス順に基づいてファイル間を移動する、IDE Navigator を使用して現在開いている任意のファイルをすばやく見つける、あるいはお気に入りのファイルをタブにピン留めして常に表示されているようにする、などです。  
  
 [戻る] と [次に進む] を使うと、Microsoft Internet Explorer で [戻る] と [進む] で履歴を表示するのと同じように、開いているファイルをアクセスした順番に基づいて切り替えることができます。  
  
#### 使用順に開いているファイル内を移動するには
<a id="to-move-through-open-files-in-order-of-use" class="xliff"></a>  
  
-   最も最近使用した順序で開いているドキュメントを表示するには、Ctrl キーを押しながらマイナス記号キーを押します。  
  
-   逆の順序で開いているドキュメントを表示するには、Ctrl キーと Shift キーを押しながらマイナス記号キーを押します。  
  
    > [!NOTE]
    >  **[戻る]** と **[次に進む]** は **[表示]** メニューにもあります。  
  
 また、ファイルを最後にアクセスしたときに関係なく、**IDE Navigator**、エディターの **[アクティブなファイル]** リスト、または **[Windows]** ダイアログ ボックスを使って、エディターで開いている特定のファイルを切り替えることができます。  
  
 **IDE Navigator** は、Windows アプリケーションのスイッチャーのように動作します。 メニューからは利用できず、ショートカット キーを使用してのみアクセスできます。 2 つのコマンドのいずれかを使って **IDE Navigator** にアクセスし (下記参照)、表示したい順番でファイルを切り替えることができます。  
  
 ![Visual Studio IDE Navigator](../ide/media/vs2015_ide_navigator.png "VS2015_IDE_Navigator")  
  
 `Window.PreviousDocumentWindowNav` では最後にアクセスしたファイルに移動することができ、`Window.NextDocumentWindowNav` では逆の順序で移動することができます。 [全般的な開発設定] では、Ctrl + Shift + Tab キーが `Window.PreviousDocumentWindowNav` に、Ctrl + Tab キーが `Window.NextDocumentWindowNav` に割り当てられてています。  
  
> [!NOTE]
>  使っている設定の組み合わせの中に、このコマンドに割り当てられているショートカット キーの組み合わせがない場合は、**[オプション]** ダイアログ ボックスの **[キーボード]** ページを使って、独自のカスタム コマンドを割り当てることができます。 詳細については、「[Visual Studio でのキーボード ショートカットの識別とカスタマイズ](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)」をご覧ください。  
  
#### エディターで特定のファイルに切り替えるには
<a id="to-switch-to-specific-files-in-the-editor" class="xliff"></a>  
  
-   Ctrl + Tab キーを押して、**IDE Navigator** を表示します。 切り替える対象のファイルが選択されるまで、Ctrl キーを押さえたまま繰り返し Tab キーを押します。  
  
    > [!TIP]
    >  **[アクティブなファイル]** リストの順番を逆に切り替えるには、Ctrl キーと Shift キーを押さえたまま Tab キーを押します。  
  
     \- または  
  
-   エディターの右上隅で、**[アクティブなファイル]** ボタンを選び、切り替え先のファイルをリストから選びます。  
  
     \- または  
  
-   メニュー バーで、**[ウィンドウ]**、**[ウィンドウ]** の順に選びます。  
  
-   一覧で表示するファイルを選び、**[開く]** を選びます。  
  
## IDE のツール ウィンドウ間を移動する
<a id="navigating-among-tool-windows-in-the-ide" class="xliff"></a>  
 **IDE Navigator** では、IDE で開いているツール ウィンドウを順番に表示することもできます。 2 つのコマンドのいずれかを使って **IDE Navigator** にアクセスし、表示したい順番でツール ウィンドウを切り替えることができます。 `Window.PreviousToolWindowNav` では最後にアクセスしたファイルに移動することができ、`Window.NextToolWindowNav` では逆の順序で移動することができます。 [全般的な開発設定] では、Shift + Alt + F7 が `Window.PreviousDocumentWindowNav` に、Alt + F7 が `Window.NextDocumentWindowNav` に割り当てられています。  
  
> [!NOTE]
>  使っている設定の組み合わせの中に、このコマンドに割り当てられているショートカット キーの組み合わせがない場合は、**[オプション]** ダイアログ ボックスの **[キーボード]** ページを使って、独自のカスタム コマンドを割り当てることができます。 詳細については、「[Visual Studio でのキーボード ショートカットの識別とカスタマイズ](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)」をご覧ください。  
  
#### IDE で特定のツール ウィンドウに切り替えるには
<a id="to-switch-to-a-specific-tool-window-in-the-ide" class="xliff"></a>  
  
-   Alt + F7 キーを押して、**IDE Navigator** を表示します。 切り替える対象のウィンドウが選択されるまで、Alt キーを押したまま繰り返し F7 キーを押します。  
  
    > [!TIP]
    >  **[アクティブなツール ウィンドウ]** リストの順番を逆に切り替えるには、Shift キーと Alt キーを押したまま F7 キーを押します。  
  
## 関連項目
<a id="see-also" class="xliff"></a>  
 [ウィンドウ レイアウトをカスタマイズする](../ide/customizing-window-layouts-in-visual-studio.md)   
 [既定のキーボード ショートカット](../ide/default-keyboard-shortcuts-in-visual-studio.md)

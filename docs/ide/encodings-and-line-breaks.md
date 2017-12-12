---
title: "Visual Studio のエンコーディングと改行文字 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b6afbc9ca8f93dcb0313c70a9d1e41579a6bf31f
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2017
---
# <a name="encodings-and-line-breaks"></a>エンコーディングと改行
Visual Studio では、次の文字が改行として解釈されます。  
  
-   CR LF: キャリッジ リターン文字とライン フィード文字 (Unicode 文字では 000D + 000A)  
  
-   LF: ライン フィード文字 (Unicode 文字では 000A)  
  
-   NEL: 次行記号 (Unicode 文字では 0085)  
  
-   LS: 行区切り記号 (Unicode 文字では 2028)  
  
-   PS: 段落区切り記号 (Unicode 文字では 2029)  
  
他のアプリケーションからコピーされたテキストでは、元のエンコーディングと改行文字が保持されます。 たとえば、メモ帳からテキストをコピーし、Visual Studio でテキスト ファイルに貼り付けた場合、貼り付けたテキストの設定は、メモ帳で使用していた設定と同じになります。  
  
改行文字が異なるファイルを開くと、一致しない改行文字を正規化するかどうか、また、どの種類の改行を使用するかを確認するダイアログ ボックスが表示される場合があります。

**[ファイル]** メニューの **[保存オプションの詳細設定]** ダイアログ ボックスを使用して、必要な改行の種類を決定できます。 また、同じ設定でファイルのエンコーディングを変更することもできます。

![[保存オプションの詳細設定] ダイアログ ボックス](media/line_endings.png)
  
> [!NOTE]
>  **[ファイル]** メニューに **[保存オプションの詳細設定]** が表示されない場合は、追加することができます。 **[ツール]**、**[カスタマイズ]** の順に選択し、**[コマンド]** タブを選択します。**メニュー バー**のドロップダウン リストで、**[ファイル]** を選択し、**[コマンドの追加...]** ボタンを選択します。 **[コマンドの追加]** ダイアログ ボックスの **[カテゴリ]** の下で、**[ファイル]** を選択してから、**[コマンド]** 一覧で **[保存オプションの詳細設定]** を選択します。**[OK]** を選択し、**[下へ移動]** ボタンを選び、コマンドをメニュー内の任意の場所に移動します。 **[閉じる]** を選び、**[カスタマイズ]** ダイアログ ボックスを閉じます。 詳細については、「[メニューまたはツール バーのカスタマイズ](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md#customizing_menu)」を参照してください。

または、**[ファイル]**、**[\<ファイル名\> に名前を付けて保存]** を選択して**[保存オプションの詳細設定]** ダイアログ ボックスにアクセスできます。**[名前を付けてファイルを保存]** ダイアログ ボックスで、**[保存]** ボタンの横にあるドロップダウンの三角形を選択し、**[エンコード付きで保存]** を選択します。

## <a name="see-also"></a>関連項目
[コード エディターでのコードの作成](../ide/writing-code-in-the-code-and-text-editor.md)
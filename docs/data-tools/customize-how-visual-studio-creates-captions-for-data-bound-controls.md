---
title: "Visual Studio でのデータ バインド コントロールのキャプションを作成する方法をカスタマイズする |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 86f0e451fe81875868db0d6ddcd9cead790800d3
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio でのデータ バインド コントロールのキャプションを作成する方法をカスタマイズします。
項目をドラッグすると、[データ ソース ウィンドウ](add-new-data-sources.md)デザイナーでは、上に、特別な配慮: いるキャプション ラベルの列名は 2 つより読みやすい文字列に再設定または複数の単語として検出されました。連結されます。 設定によって、これらのラベルを作成、方法をカスタマイズすることができます、 **SmartCaptionExpression**、 **SmartCaptionReplacement**、および**SmartCaptionSuffix**値**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data デザイナー**レジストリ キー。  
  
> [!NOTE]
> このレジストリ キーは、作成するまでには存在しません。  
  
値に入力された正規表現によって制御されるスマート キャプション、 **SmartCaptionExpression**値。 追加する、**データ デザイナー**レジストリ キーがキャプション ラベルを制御する既定の正規表現をオーバーライドします。 正規表現の詳細については、次を参照してください。 [Visual Studio での正規表現の使用](../ide/using-regular-expressions-in-visual-studio.md)です。  
  
次の表では、キャプション ラベルを制御するレジストリ値について説明します。  
  
|[レジストリ] 項目|説明|  
|-------------------|-----------------|  
|**SmartCaptionExpression**|正規表現のパターンに一致するために使用します。|  
|**SmartCaptionReplacement**|一致するすべてのグループを表示する形式、 **SmartCaptionExpression**です。|  
|**SmartCaptionSuffix**|キャプションの末尾に追加する省略可能な文字列。|  
  
次の表は、これらのレジストリ値の内部の既定の設定を一覧表示します。  
  
|[レジストリ] 項目|既定値|説明|  
|-------------------|-------------------|-----------------|  
|**SmartCaptionExpression**|(\\\p{Ll}) (\\\p{Lu}) (& a) #124; _ +|大文字の文字またはアンダー スコアを続けて小文字の文字と一致します。|  
|**SmartCaptionReplacement**|$1 $2|$1 は、式の最初のかっこ内の文字列表現を表し、$2 は 2 つ目のかっこ内に一致する任意の文字を表します。 置換は、最初の一致、スペース、および 2 番目の一致です。|  
|**SmartCaptionSuffix**|:|返される文字列に追加する文字を表します。 たとえば、キャプションが`Company Name`サフィックスになります`Company Name:`|  
  
> [!CAUTION]
> レジストリ エディターで操作する際は十分に注意してください。 編集する前に、レジストリをバックアップします。 レジストリ エディターを誤って使用する場合は、オペレーティング システムを再インストールする必要があります深刻な問題が発生することができます。 Microsoft では、レジストリ エディターの使用によって発生した問題を解決できることは保証されません。 レジストリ エディターは、ご自身の責任において使用してください。  
>   
>  次のサポート技術情報の記事には、バックアップ、編集、およびレジストリを復元するための手順が含まれています: [Microsoft Windows レジストリの説明](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)(http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)  
  
### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>データ ソース ウィンドウのスマート キャプションの動作を変更するには  
  
1.  クリックして、コマンド ウィンドウを開く**開始**し**実行**です。  
  
2.  型`regedit`で、**実行** ダイアログ ボックスをクリック**OK**です。  
  
3.  展開して、 **HKEY_CURRENT_USER**、**ソフトウェア*、 **Microsoft**、 **VisualStudio**ノード。  
  
7.  右クリックし、 **15.0**ノード、され、新しい作成**キー**という`Data Designers`です。  
  
8.  右クリックし、**データ デザイナー**ノード、し、次の 3 つの新しい文字列値を作成します。

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. 右クリックし、 **SmartCaptionExpression**値に設定して、選択**変更**です。  
  
12. 必要な正規表現を入力、**データ ソース**を使用するウィンドウです。  
  
13. 右クリックし、 **SmartCaptionReplacement**値に設定して、選択**変更**です。  
  
14. 置換を入力文字列を正規表現に一致するパターンを表示する方法で書式設定します。  
  
15. 右クリックし、 **SmartCaptionSuffix**値に設定して、選択**変更**です。  
  
16. キャプションの最後に表示する任意の文字を入力します。  
  
    項目をドラッグして、次回、**データソース**ウィンドウで、キャプション ラベルを使用して作成、新しいレジストリ値を提供します。  
  
### <a name="to-turn-off-the-smart-captioning-feature"></a>スマート キャプション機能をオフにするには  
  
1.  クリックして、コマンド ウィンドウを開く**開始**し**実行**です。  
  
2.  型`regedit`で、**実行** ダイアログ ボックスをクリック**OK**です。  
  
3.  展開して、 **HKEY_CURRENT_USER**、**ソフトウェア**、 **Microsoft**、 **VisualStudio**ノード。  
  
7.  右クリックし、 **15.0**ノード、され、新しい作成**キー**という`Data Designers`です。  
  
8.  右クリックし、**データ デザイナー**ノード、し、次の 3 つの新しい文字列値を作成します。

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`
  
11. 右クリックし、 **SmartCaptionExpression**項目、および選択**変更**です。  
  
12. 入力`(.*)`値。 文字列全体が照合されます。  
  
13. 右クリックし、 **SmartCaptionReplacement**項目、および選択**変更**です。  
  
14. 入力`$1`値。 これにより、文字列が文字列全体をできるように、これは変更されませんが、一致した値に置き換えられます。  
  
    項目をドラッグして、次回、**データソース**ウィンドウで、キャプション ラベルは変更されずに作成されます。  
  
## <a name="see-also"></a>関連項目  
[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)
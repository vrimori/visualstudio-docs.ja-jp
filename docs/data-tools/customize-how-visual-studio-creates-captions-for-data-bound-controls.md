---
title: Visual Studio がデータ バインド コントロールのキャプションを作成する方法をカスタマイズする
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 69e97efe6db8b06f476b7dc004e3b52a77701cb0
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758421"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Visual Studio がデータ バインド コントロールのキャプションを作成する方法をカスタマイズする

項目をドラッグすると、[データ ソース ウィンドウ](add-new-data-sources.md)デザイナーに、特別な配慮: キャプション ラベル内の列名は 2 つの読みやすい文字列に再設定、または複数の単語が見つかった連結して 1 つ。 設定によって、これらのラベルを作成、方法をカスタマイズすることができます、 **SmartCaptionExpression**、 **SmartCaptionReplacement**、および**SmartCaptionSuffix**値**HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Data デザイナー**レジストリ キー。

> [!NOTE]
> このレジストリ キーは、作成するまでには存在しません。

スマート キャプションは、正規表現の値に入力によって制御されます、 **SmartCaptionExpression**値。 追加、**データ デザイナー**レジストリ キーには、ラベルのキャプションを制御する既定の正規表現がよりも優先されます。 正規表現の詳細については、次を参照してください。 [Visual Studio で正規表現を使用して](../ide/using-regular-expressions-in-visual-studio.md)します。

次の表では、図表番号のラベルを制御するレジストリ値について説明します。

|レジストリ項目|説明|
|-------------------|-----------------|
|**SmartCaptionExpression**|正規表現のパターンに一致するように使用します。|
|**SmartCaptionReplacement**|すべてのグループ単位で一致を表示する形式、 **SmartCaptionExpression**します。|
|**SmartCaptionSuffix**|キャプションの末尾に追加する省略可能な文字列。|

次の表は、これらのレジストリ値の内部の既定の設定を一覧表示します。

|レジストリ項目|既定値|説明|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|**(\\\p{Ll}) (\\\p{Lu})&#124;_ +**|小文字の後に大文字の文字またはアンダー スコア文字と一致します。|
|**SmartCaptionReplacement**|**$1 円 2**|**$1** 、式の最初のかっこ内の文字列表現を表す、 **$2** 2 つ目のかっこ内の文字列表現を表します。 置換は、最初に一致する、スペース、および 2 番目の一致。|
|**SmartCaptionSuffix**|**:**|返される文字列に追加する文字を表します。 たとえば、キャプションが`Company Name`サフィックスになります `Company Name:`|

> [!CAUTION]
> レジストリ エディターで操作する際は十分に注意する必要があります。 編集する前に、レジストリをバックアップします。 レジストリ エディターを正しく使用する場合、オペレーティング システムを再インストールする必要があります深刻な問題が発生することができます。 Microsoft では、レジストリ エディターの使用によって発生した問題を解決できることは保証されません。 レジストリ エディターは、ご自身の責任において使用してください。
>
> 次のサポート技術情報記事にはバックアップを作成、編集、およびレジストリを復元するための手順が含まれています: [Microsoft Windows レジストリの説明](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986)(http://support.microsoft.com/default.aspx?scid=kb; en-ご; 256986)

## <a name="modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>データ ソース ウィンドウのスマート キャプションの動作を変更します。

1.  コマンド ウィンドウを開きます**開始**し**実行**します。

2.  型`regedit`で、**実行** ダイアログ ボックスをクリックします**OK**します。

3.  展開、 **HKEY_CURRENT_USER** > **ソフトウェア** > **Microsoft** > **VisualStudio**ノード。

7.  右クリックし、 **15.0**ノード、され、新しい作成**キー**という`Data Designers`します。

8.  右クリックし、**データ デザイナー**ノード、3 つの新しい文字列値を作成。

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. 右クリックし、 **SmartCaptionExpression**値、および選択**変更**します。

12. 必要な正規表現を入力、**データ ソース**に使用するウィンドウ。

13. 右クリックし、 **SmartCaptionReplacement**値、および選択**変更**します。

14. 置換を入力します。 正規表現に一致するパターンを表示する方法は、書式設定された文字列。

15. 右クリックし、 **SmartCaptionSuffix**値、および選択**変更**します。

16. キャプションの最後に表示する任意の文字を入力します。

    項目をドラッグする、次回、**データソース**ウィンドウ キャプション ラベルは作成に提供される新しいレジストリ値を使用します。

## <a name="turn-off-the-smart-captioning-feature"></a>スマート キャプション機能を無効にします。

1.  コマンド ウィンドウを開きます**開始**し**実行**します。

2.  型`regedit`で、**実行** ダイアログ ボックスをクリックします**OK**します。

3.  展開、 **HKEY_CURRENT_USER** > **ソフトウェア** > **Microsoft** > **VisualStudio**ノード。

7.  右クリックし、 **15.0**ノード、され、新しい作成**キー**という`Data Designers`します。

8.  右クリックし、**データ デザイナー**ノード、3 つの新しい文字列値を作成。

    - `SmartCaptionExpression`
    - `SmartCaptionReplacement`
    - `SmartCaptionSuffix`

11. 右クリックし、 **SmartCaptionExpression** 、アイテムを選択します**変更**します。

12. 入力`(.*)`値。 文字列全体が照合されます。

13. 右クリックし、 **SmartCaptionReplacement** 、アイテムを選択します**変更**します。

14. 入力`$1`値。 これにより、文字列が文字列全体をできるように、これは変更されませんが、一致した値に置き換えられます。

    項目をドラッグする、次回、**データソース**ウィンドウで、変更されずに、図表番号のラベルが作成されます。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)
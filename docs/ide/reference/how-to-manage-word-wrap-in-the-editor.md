---
title: '方法 : エディターのワード ラップを管理する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36945273c58211865eccf464d810fb276598b665
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2018
ms.locfileid: "34448000"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>方法 : エディターのワード ラップを管理する

**[右端で折り返す]** オプションを設定および解除できます。 このオプションを設定すると、コード エディター ウィンドウの現在の幅からはみ出した長い行の部分は次の行に表示されます。 たとえば行番号の使用を容易にするためにこのオプションをオフにすると、右にスクロールして長い行の末尾を表示できます。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、**ヘルプ**の説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="procedure"></a>プロシージャ

### <a name="to-set-word-wrap-preferences"></a>ワード ラップ オプションを設定するには

1.  **[ツール]** メニューの **[オプション]** を選択します。

2.  **[テキスト エディター]** フォルダーで、**[すべての言語]** サブフォルダーの **[全般]** オプションを選択して、このオプションをグローバルに設定します。

     または

     プログラミングしている言語のサブフォルダーの **[全般]** オプションを選択します。

3.  **[設定]** で、**[右端で折り返す]** オプションをオンまたはオフにします。

     **[右端で折り返す]** オプションをオンにすると、**[右端の折り返しの記号を表示する]** オプションが有効になります。

4.  長い行が 2 行目に折り返される場合に改行インジケーターを表示するには、**[折り返しの記号を表示する]** オプションをオンにします。 このオプションをオフにすると、インジケーターは表示されません。

    > [!NOTE]
    >  改行インジケーターはコードには追加されません。表示専用です。

## <a name="see-also"></a>関連項目

- [エディターのカスタマイズ](../../ide/customizing-the-editor.md)
- [[テキスト エディター] ([オプション] ダイアログ ボックス)](../../ide/reference/text-editor-options-dialog-box.md)
- [コード エディターの機能](../../ide/writing-code-in-the-code-and-text-editor.md)
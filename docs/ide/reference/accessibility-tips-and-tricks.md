---
title: "Visual Studio のアクセシビリティのヒントとテクニック | Microsoft Docs"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4cfc07cb77e1db595d1b381b1097dcfcba0abdab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>Visual Studio のアクセシビリティのヒントとテクニック
> [!TIP]
> 最近実施されたアクセシビリティの更新の詳細については、ブログ投稿の「[Accessibility improvements in Visual Studio 2017 version 15.3 (Visual Studio 2017 バージョン 15.3 でのアクセシビリティの機能強化)](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/)」をご覧ください。

Visual Studio には、スクリーン リーダーやその他の支援テクノロジと互換性を持つユーザー補助機能が組み込まれています。 このトピックでは、キーボードのみを使用してタスクを実行するためによく使用されるショートカット キーの組み合わせを一覧すると共に、見やすさを改善するためのハイ コントラストのテーマの使用に関する情報を提供します。 さらに、注釈を使用してコードに関する有用な情報を表示する方法と、ビルドおよびブレークポイントのイベントに対してサウンド キューを設定する方法についても説明します。

## <a name="save-your-ide-settings"></a>IDE 設定を保存する  
 ウィンドウのレイアウト、キーボード マップ スキーム、およびその他の設定を保存することにより、IDE エクスペリエンスをカスタマイズできます。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  

## <a name="modify-your-ide-for-high-contrast-viewing"></a>ハイ コントラスト表示のための IDE の変更
一部の人たちには、見えにくい色があります。 コードを書くときにコントラストを強くしたいが一般的な "ハイ コントラスト" テーマは使用したくないという場合は、"青 (エクストラ コントラスト)" テーマをお勧めします。

  ![青のテーマと青 (エクストラ コントラスト) テーマの比較](media/blue-extra-contrast-theme.png "青のテーマと青 (エクストラ コントラスト) テーマの違いを確認してください")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>注釈を使用してコードに関する有用な情報を表示する

Visual Studio エディターには多くのテキスト "表示要素" が含まれています。これにより、電球、エラーおよび警告の "波線" 、ブックマークなど、コード行の特定のポイントで、特性や機能について知ることができます。 “行注釈の表示” コマンド セットを使用すると、これらの表示要素の検出およびこれらの表示要素間の移動が簡単になります。

  ![“行注釈の表示” コマンド セットを使用する](media/show-line-annotations-command-set.png "“行注釈の表示” コマンド セットの設定方法を表示する")

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>ショートカット キーの組み合わせを使用してツールバーにアクセスする
Visual Studio IDE には、多くのツール ウィンドウと同様に機能するツールバーがあります。 次のショートカット キーの組み合わせを使用すると、それらのツールバーに容易にアクセスできます。

|機能|説明|キーの組み合わせ|  
|-------------|-----------------|---------------------|  
|IDE ツール バー|標準ツール バーの最初のボタンを選択します。|**ALT**、**CTRL** + **TAB**|  
|ツール ウィンドウのツール バー|ツール ウィンドウのツール バーにフォーカスを移動します。 <br> <br> **注:** この操作はほとんどのツール ウィンドウで可能です。ただし、フォーカスがツール ウィンドウ内になければなりません。 また、Shift キーを押してから、Alt キーを押す必要があります。 チーム エクスプローラーなど、一部のツール ウィンドウでは、Shift キーをしばらく押したままにしてから、Alt キーを押す必要があります。|**Shift** + **Alt**|
|ツールバー|次のツールバーの最初の項目に移動します (特定のツールバーにフォーカスが置かれている場合)。|**CTRL** + **TAB**|

### <a name="other-useful-shortcut-key-combinations"></a>その他の便利なショートカット キーの組み合わせ  
他にも便利なショートカット キーの組み合わせがあります。

|機能|説明|キーの組み合わせ|  
|-------------|-----------------|---------------------|  
|IDE|ハイ コントラストのオンとオフを切り替えます。 <br> <br> **注:** Windows の標準的なショートカット|**左 Alt + 左 Shift + Print Screen**|  
|ダイアログ ボックス|ダイアログ ボックスのチェック ボックス オプションをオンまたはオフにします。 <br> <br> **注:** Windows の標準的なショートカット|**Space キー**|  
|コンテキスト メニュー|(右クリックして) コンテキスト メニューを開きます。 <br> <br> **注:** Windows の標準的なショートカット|**SHIFT** + **F10**|
|メニュー|アクセラレータ キーを使用して、メニュー項目にすばやくアクセスします。 **Alt** キーを押してからメニュー内の下線付きの文字を選択して、コマンドをアクティブにします。 たとえば、Visual Studio の [プロジェクトを開く] ダイアログ ボックスを表示するには、**ALT** + **F** + **O** + **P** キーを押します。  <br><br> **注:** Windows の標準的なショートカット|**ALT** + **[文字]**|
|[ツールボックス] ウィンドウ|[ツールボックス] のタブ間を移動します。|**Ctrl** + **↑**<br /><br /> と、呼び出し<br /><br /> **Ctrl** + **↓**|  
|[ツールボックス] ウィンドウ|[ツールボックス] からフォームまたはデザイナーにコントロールを追加します。|**Enter**|  
|[キーボード]\([オプション] ダイアログ ボックス - [環境])|**[ショートカット キー]** オプションに入力されたキーの組み合わせを削除します。|**Backspace**|  

> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  


## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>サウンド アプレットを使用してビルドおよびブレークポイントのキューを設定する
Windows のサウンド アプレットを使用して、Visual Studio プログラム イベントにサウンドを割り当てることができます。 具体的には、次のプログラム イベントにサウンドを割り当てることができます。

 * ブレークポイントのヒット
 * ビルドが取り消されました
 * ビルドに失敗しました
 * ビルドに成功しました

ここではその方法を説明します。

1. Windows 10 を実行しているコンピューター上の**検索**ボックスに「**システムが出す音の変更**」と入力します。

  ![Windows 10 の検索ボックス](media/type-here-to-search.png "Windows 10 を実行しているコンピューターの検索ボックスに「サウンド」と入力する")

  (あるいは、Cortana が有効になっている場合は、「コルタナさん」と言ってから、「システムが出す音の変更」と言います。)

2. **[システムが出す音の変更]** をダブルクリックします。

  ![Windows 10 での検索結果](media/change-system-sounds.png "検索結果の [システムが出す音の変更] をダブルクリックする")

3. **[サウンド]** ダイアログ ボックスで、**[サウンド]** タブをクリックします。 <br><br>
 次に、**[プログラム イベント]** で、**[Microsoft Visual Studio]** にスクロールし、選択したイベントに適用するサウンドを選択します。

  ![Windows 10 のサウンド アプレットの [サウンド] タブ](media/sound-applet.png "検索結果の [システムが出す音の変更] をダブルクリックする")

4. **[OK]**をクリックします。



## <a name="see-also"></a>関連項目  
* [Visual Studio のユーザー補助機能](../../ide/reference/accessibility-features-of-visual-studio.md)
  * [方法: Visual Studio でメニューおよびツール バーをカスタマイズする](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)
* [Microsoft ユーザー補助機能](https://www.microsoft.com/Accessibility)

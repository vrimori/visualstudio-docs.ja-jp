---
title: "アクセシビリティのヒントとテクニック | Microsoft Docs"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 17defdd0b96ec1c3273fc6b845af844b031a4a17
ms.openlocfilehash: 906e8c70df502245001f87795cab9f5efe808c83
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="accessibility-tips-and-tricks"></a>アクセシビリティのヒントとテクニック
> [!TIP]
> 最近実施されたアクセシビリティの更新の詳細については、ブログ投稿の「[Accessibility improvements in Visual Studio 2017 version 15.3 (Visual Studio 2017 バージョン 15.3 でのアクセシビリティの機能強化)](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/)」をご覧ください。

Visual Studio にはアクセシビリティ機能が組み込まれているため、簡単にキーボードで作業したり、スクリーン リーダーやその他の支援技術デバイスを使用したりすることができます。 ここでは、便利なショートカット キーのいくつかの組み合わせのほか、Visual Studio のアクセシビリティを向上するために最適化する場合の推奨事項についてもいくつか示します。 ショートカット キーを組み合わせて使用すると、キーボードで Visual Studio のタスクを実行できます。

## <a name="save-your-ide-settings"></a>IDE 設定を保存する  
 ウィンドウのレイアウト、キーボード マップ スキーム、およびその他の設定を保存することにより、IDE エクスペリエンスをカスタマイズできます。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  

## <a name="accessing-toolbars"></a>ツールバーへのアクセス
Visual Studio IDE には、多くのツール ウィンドウと同様に機能するツールバーがあります。 次のショートカット キーの組み合わせを使用すると、それらのツールバーに容易にアクセスできます。

|機能|説明|キーの組み合わせ|  
|-------------|-----------------|---------------------|  
|IDE ツール バー|標準ツール バーの最初のボタンを選択します。|**ALT**、**CTRL** + **TAB**|  
|ツール ウィンドウのツール バー|ツール ウィンドウのツール バーにフォーカスを移動します。 <br> <br> **注:** この操作はほとんどのツール ウィンドウで可能です。ただし、フォーカスがツール ウィンドウ内になければなりません。 また、Shift キーを押してから、Alt キーを押す必要があります。 チーム エクスプローラーなど、一部のツール ウィンドウでは、Shift キーをしばらく押したままにしてから、Alt キーを押す必要があります。|**Shift** + **Alt**|
|ツールバー|次のツールバーの最初の項目に移動します (特定のツールバーにフォーカスが置かれている場合)。|**CTRL** + **TAB**|

## <a name="other-useful-shortcut-key-combinations"></a>その他の便利なショートカット キーの組み合わせ  
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

## <a name="see-also"></a>関連項目  
 [Visual Studio のユーザー補助機能](../../ide/reference/accessibility-features-of-visual-studio.md)

 [方法: Visual Studio でメニューおよびツール バーをカスタマイズする](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)

 [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)


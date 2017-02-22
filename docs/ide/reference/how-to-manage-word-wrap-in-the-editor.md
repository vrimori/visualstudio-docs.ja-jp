---
title: "方法 : エディターのワード ラップを管理する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード エディター, ワード ラップ"
  - "エディター, テキストの表示"
  - "ワード ラップ"
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法 : エディターのワード ラップを管理する
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**\[右端で折り返す\]** オプションの設定と解除を行うことができます。  このオプションを設定すると、コード エディター ウィンドウの現在の幅を超える長さの行で、はみ出す部分が次の行に表示されます。  たとえば行番号の機能を生かすために、このオプションをオフにした場合は、右にスクロールすると、行の端まで参照できます。  
  
 詳細については、「[How to: Set General Editor Options](http://msdn.microsoft.com/ja-jp/704e4a7b-2162-4bed-8a47-f4f6ffec98c2)」を参照してください。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、**\[ヘルプ\]** の記載と異なるダイアログ ボックスやメニュー コマンドが表示される場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 手順  
  
#### ワード ラップ オプションを設定するには  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  このオプションをグローバルに設定する場合は、**\[テキスト エディター\]** フォルダーで、**\[すべての言語\]** サブフォルダーにある **\[全般\]** オプションをクリックします。  
  
     または  
  
     プログラミングしている言語のサブフォルダーにある **\[全般\]** オプションをクリックします。  
  
3.  **\[設定\]** の **\[右端で折り返す\]** オプションをオンまたはオフにします。  
  
     **\[右端で折り返す\]** オプションをオンにすると、**\[右端の折り返しの記号を表示する\]** オプションが選択可能になります。  
  
4.  長い行を 2 行目に折り返したことを改行矢印で示す場合は **\[右端の折り返しの記号を表示する\]** オプションをオンにします。  インジケーター矢印を表示しない場合は、このオプションをオフにします。  
  
    > [!NOTE]
    >  これら注意を促すための矢印は、参照用に表示されるのみであり、コードに追加されるわけではありません。  
  
## 参照  
 [エディターのカスタマイズ](../../ide/customizing-the-editor.md)   
 [\[テキスト エディター\] \(\[オプション\] ダイアログ ボックス\)](../Topic/Text%20Editor%20Options%20Dialog%20Box.md)   
 [コードの作成](../../ide/writing-code-in-the-code-and-text-editor.md)
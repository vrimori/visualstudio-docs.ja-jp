---
title: "方法 : 停止した場合に MFC を呼び出した関数に戻る | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.mfc"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "[中断] コマンド"
  - "デバッグ [MFC], 関数"
  - "デバッグ [MFC], 戻る (呼び出し元の関数に)"
  - "関数呼び出し, 戻る (呼び出し元の関数に)"
  - "関数 [C++], デバッグ"
  - "関数 [デバッガー]"
  - "プログラム, 中断"
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# 方法 : 停止した場合に MFC を呼び出した関数に戻る
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、\[ツール\] メニューの \[設定のインポートとエクスポート\] をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 **\[デバッグ\]** メニューの **\[中断\]** コマンドでプログラムを中断した場合に MFC 内で実行が停止されたとします。そのとき、問題が自分自身で作成したコードにあることが明らかな場合は、\[呼び出し履歴\] ウィンドウを使用することにより、呼び出し元の関数に戻ることができます。  詳細については、「[方法 : \[呼び出し履歴\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)」を参照してください。  
  
 コードがメッセージ ポンプ内で中断する場合があります。  この場合、呼び出し履歴にユーザー コードは存在しません。  この問題を回避するには、**\[中断\]** コマンドではなく、ブレークポイントを使用する必要があります。適宜、条件とヒット カウントを組み合わせて使用します。  詳細については、「[Breakpoints and Tracepoints](http://msdn.microsoft.com/ja-jp/fe4eedc1-71aa-4928-962f-0912c334d583)」を参照してください。  
  
### MFC の呼び出し元の関数を参照するには  
  
-   **\[呼び出し履歴\]** ウィンドウを使用します。  
  
## 参照  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)
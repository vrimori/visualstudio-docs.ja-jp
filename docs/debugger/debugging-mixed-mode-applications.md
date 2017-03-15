---
title: "方法 : 混合モード アプリケーションをデバッグする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "[呼び出し履歴] ウィンドウ"
  - "[呼び出し履歴] ウィンドウ, 混合モードのデバッグ"
  - "デバッグ [Visual Studio], 混合モード"
  - "デバッグ (マネージ コードの), 混合コード"
  - "混合モードのデバッグ"
  - "混合モードのデバッグ, 呼び出し履歴"
  - "混合モードのデバッグ, プロパティの評価"
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# 方法 : 混合モード アプリケーションをデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

混合モード アプリケーションとは、ネイティブ コード \(C\+\+\) とマネージ コード \(共通言語ランタイムで動作する Visual Basic、Visual C\#、C\+\+ など\) の組み合わせから成るアプリケーションです。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] での混合モード アプリケーションのデバッグはきわめて透過的です。つまり、単一モードのアプリケーションをデバッグする場合とほとんど同じです。  ただし、特殊な注意事項があります。  
  
## 混合モードのデバッグでの C\+\+ のエディット コンティニュの有効化  
  
-   Visual Studio 2013 で C\+\+ に対してエディット コンティニュを使用するには、従来のデバッグ エンジンに戻る必要があります。  詳細については、Microsoft アプリケーション ライフサイクル管理ブログにある「[Switching to Managed Compatibility Mode in Visual Studio 2013 \(Visual Studio 2013 でマネージ互換モードに切り替える\)](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx)」を参照してください。  
  
## 混合モード アプリケーションでのプロパティ評価  
 混合モード アプリケーションでは、デバッガーを使用してプロパティを評価すると、負荷の高い操作になります。  そのため、ステップ実行などのデバッグ操作の処理速度が低下する場合があります。  詳細については、「[ステップ実行](http://msdn.microsoft.com/ja-jp/8791dac9-64d1-4bb9-b59e-8d59af1833f9)」を参照してください。  混合モードのデバッグでパフォーマンスが低下するような場合は、デバッガー ウィンドウのプロパティ評価をオフにできます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
#### プロパティ評価をオフにするには  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  **\[オプション\]** ダイアログ ボックスで、**\[デバッグ\]** フォルダーを開き、**\[全般\]** カテゴリを選択します。  
  
3.  **\[プロパティの評価とその他の暗黙的な関数の呼び出しを常に有効にする\]** チェック ボックスをオフにします。  
  
 ネイティブな呼び出し履歴とマネージ呼び出し履歴は異なるため、デバッガーでは、混合コードに対して常に完全な呼び出し履歴を表示できるとは限りません。  ネイティブ コードがマネージ コードを呼び出したときに、不一致が生じていることがわかります。  詳細については、「[&#91;呼び出し履歴&#93; ウィンドウの混合コードと不足情報](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)」を参照してください。  
  
## 参照  
 [マネージ コードのデバッグ](../debugger/debugging-managed-code.md)
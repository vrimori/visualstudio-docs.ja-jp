---
title: "方法 : ActiveX コントロールをデバッグする | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ActiveX コントロール コンテナーのデバッグ [Visual Studio]"
  - "ActiveX コントロール, デバッグ"
  - "コンテナー, 指定 (デバッグ セッション用に)"
  - "データ バインド コントロール, ActiveX"
  - "デバッグ (ActiveX コントロールの)"
  - "テスト コンテナー"
  - "テスト [Visual Studio], ActiveX コントロール"
  - "テスト [Visual Studio], テスト コンテナー"
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 方法 : ActiveX コントロールをデバッグする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、\[ツール\] メニューの \[設定のインポートとエクスポート\] をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 ActiveX コントロールをデバッグするには、そのコントロールが実行されるコンテナー \(実行可能ファイル\) を指定する必要があります。  
  
### デバッグ セッションのコンテナーを指定するには  
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
2.  **\[表示\]** メニューの **\[プロパティ ページ\]** をクリックします。  
  
3.  **\[\<プロジェクト名\> プロパティ ページ\]** ダイアログ ボックスで、**\[構成プロパティ\]** フォルダーを開き、**\[デバッグ\]** を選択します。  
  
4.  **\[デバッグ\]** カテゴリの **\[コマンド\]** プロパティを探します。  
  
5.  コンテナーのパス名を指定します。  たとえば、「C:\\Program Files\\Internet Explorer\\IEXPLORE.EXE」のように指定します。  
  
6.  Internet Explorer をコンテナーとして指定した場合で、かつ、アクティブ デスクトップを使用している場合は、**\[コマンド引数\]** ボックスに「`/new` 」と入力します。  
  
7.  **\[OK\]** をクリックします。  
  
     **\[\<プロジェクト名\> プロパティ ページ\]** ダイアログ ボックスでコンテナーを指定しなかった場合でも、デバッグを開始するときにコンテナーを指定できます。  実行コマンドを選択してデバッグを開始するときに、[&#91;デバッグ セッションで実行可能&#93; ダイアログ ボックス](../debugger/executable-for-debugging-session-dialog-box.md)が表示されます。  ダイアログ ボックスにコンテナーのパス名を指定します。  
  
## 参照  
 [ActiveX コントロール](/visual-cpp/mfc/activex-controls)   
 [テスト コンテナーでのプロパティとイベントのテスト](/visual-cpp/mfc/testing-properties-and-events-with-test-container)   
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)   
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)
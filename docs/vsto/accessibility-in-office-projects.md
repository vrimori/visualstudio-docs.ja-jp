---
title: "Office プロジェクトのユーザー補助機能"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "アクセシビリティ [Visual Studio での Office 開発]"
  - "Visual Studio での Office 開発, アクセシビリティ"
  - "リボン [Visual Studio での Office 開発], ショートカット キー"
  - "ショートカット キー [Visual Studio での Office 開発]"
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Office プロジェクトのユーザー補助機能
  Microsoft Visual Studio および Microsoft Office には、多数のユーザー補助機能が用意されており、標準的なユーザー補助要件を満たすカスタム ソリューションを作成できます。  Microsoft では、ユーザー補助に関するガイドラインを Web 上で公開しています。  詳細については、[マイクロソフト アクセシビリティ ホーム](http://go.microsoft.com/fwlink/?LinkID=37113)を参照してください。  
  
 ほとんどの場合、Visual Studio の Office プロジェクトは標準的なユーザー補助要件を満たしているか、ソリューションをユーザー補助対応にするプロパティを公開しています。  ただし、ユーザー補助に関して制限のある機能がいくつかあります。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## デザイン時のユーザー補助  
  
### ドキュメント レベルのプロジェクトでのショートカット キーの使用  
 Visual Studio 内で Microsoft Office Word 文書または Microsoft Office Excel ブックを開いた場合、一度に 1 つのアプリケーションだけがショートカット キー コマンドを受け付けます。  既定では Visual Studio がすべてのショートカット キー コマンドを受け取りますが、**\[オプション\]** ダイアログ ボックスの**キーボード設定**ページで **\[ダイナミック キーボード スキーム\]** を選択すると、文書またはブックにフォーカスがあるときに Word または Excel でショートカット キー コマンドを受け取ることができます。  詳細については、「[&#91;Microsoft Office Word Keyboard&#93; &#40;&#91;オプション&#93; ダイアログ ボックス - &#91;Microsoft Office Keyboard 設定&#93;&#41;](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)」および「[&#91;Microsoft Office Excel Keyboard&#93; &#40;&#91;オプション&#93; ダイアログ ボックス - &#91;Microsoft Office Keyboard 設定&#93;&#41;](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)」を参照してください。  
  
### ドキュメント レベルのプロジェクトでのリボンに対応するショートカット キーの表示  
 Visual Studio 内で Word 文書または Excel ブックを開いた場合、Alt キーを押してリボン上のタブやコントロールに対応するショートカット キーを表示することはできません。  デザイナーで文書またはブックを開いた状態でショートカット キーを表示するには、次の手順を実行します。  
  
##### デザイナーでリボンのタブおよびコントロールに対応するショートカット キーを表示するには  
  
1.  Visual Studio で、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  **\[Office ツール\]** ノードを展開し、開いているアプリケーションに応じて **\[Microsoft Office Excel Keyboard\]** と **\[Microsoft Office Word Keyboard\]** のいずれかを選択します。  
  
3.  **\[ダイナミック キーボード スキーム\]** を選択します。  
  
     変更を有効にするために Visual Studio の再起動が必要であることを示すメッセージが表示されます。  
  
4.  **\[OK\]** をクリックします。  
  
5.  Visual Studio を再起動し、再度プロジェクトを開きます。  
  
6.  プロジェクトの文書またはブックのデザイナーを開きます。  
  
7.  F6 キーを押してリボンのショートカット キーを表示します。  
  
## 実行時のユーザー補助  
  
### Office ドキュメントの Windows フォーム コントロール  
 Windows フォーム コントロールは、ユーザー補助関連プロパティを公開しており、スクリーン リーダーなどのユーザー補助機能を制御するための情報を提供しています。  ドキュメント レベルのカスタマイズの Office 文書に Windows フォーム コントロールがある場合は、それらのユーザー補助関連プロパティを利用できます。  詳細については、「[Windows フォーム上のコントロールのユーザー補助情報の提供](../Topic/Providing%20Accessibility%20Information%20for%20Controls%20on%20a%20Windows%20Form.md)」を参照してください。  
  
 ただし、Windows フォーム コントロールが Excel ブックまたは Word 文書でホストされている場合、実行時のユーザー補助機能に次のような制限が加えられます。  
  
-   コントロール間をタブ移動できません。  
  
-   ドキュメント上のコントロールは、ドキュメントのズーム設定を 100% 以外に変更すると使用不可になります。  
  
 ドキュメント上の Windows フォーム コントロールの制限事項については、「[Office ドキュメントでの Windows フォーム コントロールの制限事項](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)」を参照してください。  
  
### 操作ウィンドウとカスタム作業ウィンドウ  
 操作ウィドウまたはカスタム作業ウィンドウにフォーカスがある場合、Windows フォーム アプリケーション上のコントロールと同じようにコントロールを使用できます。  操作ウィンドウとドキュメントの間でカーソルを移動するには、**F6** キーを押します。  
  
 操作ウィドウとカスタム作業ウィンドウの詳細については、「[操作ウィンドウの概要](../vsto/actions-pane-overview.md)」および「[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)」を参照してください。  
  
### 表示モード  
 Visual Studio の表示モードには、以下の制限事項があります。  
  
-   Word 文書または Excel ワークシート上のコントロールは、ドキュメントのズーム設定を 100% 以外に変更すると使用不可になります。  
  
-   ユーザーがコンピューターのユーザー補助のオプションで **\[ハイコントラストを使う\]** を設定すると、**\[新しいプロジェクト\]** ダイアログ ボックスにコントロールが正しく表示されません。  
  
 拡大鏡を使用すると、これらの制限を回避できます。  拡大鏡は、Windows の表示ユーティリティで、画面の一部を拡大表示する独立したウィンドウが表示されます。  
  
## 参照  
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [Office ドキュメントのコントロール](../vsto/controls-on-office-documents.md)   
 [障碍があるユーザーのための機能](../ide/reference/accessibility-for-people-with-disabilities.md)   
 [Visual Studio のユーザー補助機能](../ide/reference/accessibility-features-of-visual-studio.md)  
  
  
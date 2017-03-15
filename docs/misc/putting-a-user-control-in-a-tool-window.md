---
title: "ツール ウィンドウにユーザー コントロールを配置する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ツール ウィンドウ、ユーザー コントロールの追加"
  - "ユーザー コントロール [Visual Studio SDK]、ツール ウィンドウに追加"
  - "ユーザー コントロール [Visual Studio SDK]"
ms.assetid: 869f3195-e152-4e61-802c-51d6b7ba3e36
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# ツール ウィンドウにユーザー コントロールを配置する
このチュートリアルでは、ツール ウィンドウにユーザー コントロールを追加する方法を示します。  
  
 ユーザー コントロールは、複数の Windows コントロールを 1 つのコントロールに結びつけた、Windows コントロールのコレクションです。 ツール ウィンドウにユーザー コントロールを追加するために、実際に行う必要がある作業は、**\[ツールボックス\]** に表示するユーザー コントロールを作成することだけです。 このチュートリアルで使用するユーザー コントロールは、「[チュートリアル : Visual C\# による複合コントロールの作成](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)」で開発した時計コントロールです。  
  
## 必須コンポーネント  
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## ユーザー コントロールの作成  
  
1.  「[チュートリアル : Visual C\# による複合コントロールの作成](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)」の手順に従って、時計コントロールを作成します。 アラームの時計コントロールは作成しないでください。  
  
> [!NOTE]
>  次の手順では、時計コントロールに `ctlClock` という名前が付いていることを前提にしています。  
  
## ツール ウィンドウの拡張機能の作成  
  
1.  `MyToolWindowPackageUC` という名前の VSIX プロジェクトを作成します。このプロジェクトには、`MyToolWindow` という名前のツール ウィンドウがあります。 この作業の説明が必要な場合は、「[ツール ウィンドウで、拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)」を参照してください。  
  
## ユーザー コントロールの追加  
  
1.  **ソリューション エクスプローラー**でソリューション **MyToolWindowPackageUC** を右クリックし、**\[追加\]** をポイントして、**\[既存のプロジェクト\]** をクリックします。  
  
2.  **\[既存プロジェクトの追加\]** ダイアログ ボックスで ctlClockLib プロジェクトを開き、ctlClock.lib.csproj プロジェクト ファイルを選択します。**\[OK\]** をクリックします。 これで、ユーザー コントロールをデザイナーで使用できます。  
  
3.  **ソリューション エクスプローラー**で MyToolWindowControl.cs を右クリックし、**\[デザイナーの表示\]** をクリックします。 これでフォーム デザイナーが開き、ツール ウィンドウ用に生成されたコントロールが表示されます。  
  
4.  **\[ツールボックス\]** を開いて **ctlClockLib Components** というラベルの付いたセクションを検索します。そのセクションの **ctlClock** コントロールをダブルクリックして、コントロールをフォームに追加します。**\[ツールボックス\]** を非表示にすると、すぐに表示時間がツール ウィンドウのフォームに表示されます。  
  
5.  デザイナーで、追加した時計コントロールを選択して、**\[アンカー\]** プロパティを **\[上\]** に変更します。  
  
6.  **ソリューション エクスプローラー**で ctlClockLib プロジェクト ノードを右クリックし、**\[プロパティ\]** をクリックします。  
  
7.  **\[署名\]** タブで、**\[アセンブリの署名\]** をオンにします。**\[厳密な名前のキー ファイルを選択してください\]** ボックスで **\<参照\>** をクリックし、**MyToolWindowPackageUC** プロジェクト フォルダーの key.snk ファイルに移動します。  
  
8.  プログラムをコンパイルして、エラーがないかどうかを確認します。 この手順は VSPackage とツール ウィンドウを Visual Studio に登録します。  
  
9. F5 キーを押して、実験的なハイブで Visual Studio のインスタンスを開きます。  
  
10. 実験用の Visual Studio の **\[表示\]** メニューで **\[その他のウィンドウ\]** をポイントし、**MyToolWindow** をクリックします。 これで、時間表示が動作しているツール ウィンドウが表示されます。  
  
## 参照  
 [チュートリアル : Visual C\# による複合コントロールの作成](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)
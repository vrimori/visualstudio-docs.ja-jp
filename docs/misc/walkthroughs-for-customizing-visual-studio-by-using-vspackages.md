---
title: "VSPackage を使用して Visual Studio をカスタマイズするためのチュートリアル | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage"
  - "チュートリアル"
  - "Visual Studio のカスタマイズ"
  - "VS IDE"
  - "Visual Studio IDE"
ms.assetid: 7d10e376-74de-4402-9c10-ee9c9aa33c98
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# VSPackage を使用して Visual Studio をカスタマイズするためのチュートリアル
Visual Studio を拡張するには、VSPackage を作成します。 これらは、Visual Studio 自体を構成するソフトウェア モジュールです。 ツール ウィンドウ、エディター、サービス、およびプロジェクト タイプはすべて VSPackage です。 Visual Studio SDK を使用して、独自の VSPackage を作成できます。  
  
 このセクションのチュートリアルでは、VSPackage を作成して機能を持たせ、Visual Studio に統合して、他のユーザーに配布する方法について説明します。 VSPackage とその機能の詳細については、「[Visual Studio SDK 内](../extensibility/internals/inside-the-visual-studio-sdk.md)」を参照してください。  
  
## このセクションの内容  
 [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)  
 Visual Studio のメニューにコマンドを追加する VSPackage を作成する方法と、コマンドへのキーボード ショートカットを追加する方法を示します。 また、パッケージに関する情報を Visual Studio の **\[バージョン情報\]** ダイアログ ボックスやスプラッシュ スクリーンに追加する方法についても説明します。  
  
 [ツール ウィンドウを追加します。](../extensibility/adding-a-tool-window.md)  
 Visual Studio でツール ウィンドウを作成する方法、および、そのウィンドウにコントロールを埋め込む方法とコマンド バーを追加する方法を示します。 また、Visual Studio でのツール ウィンドウの配置を登録する方法も示します。  
  
 [プロパティ、タスク一覧、出力、およびオプションの Windows の拡張](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)  
 ユーザーが Visual Studio の **\[タスク一覧\]** と **\[出力\]** ウィンドウにタスクを追加できるようにする基本的なタスク マネージャーを作成する方法を示します。 追加したタスクは、Visual Studio の **\[プロパティ\]** ウィンドウで編集できます。 また、**\[オプション\]** ダイアログ ボックスにページを追加する方法についても説明します。  
  
## 関連項目  
 [Visual Studio SDK の概要](../Topic/Introducing%20the%20Visual%20Studio%20SDK.md)  
 Visual Studio SDK に含まれている機能およびツールの概要を示し、それらを使用して Visual Studio を拡張する方法を示します。  
  
 [Visual Studio SDK 内](../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Visual Studio IDE のさまざまな要素をカスタマイズする方法について説明します。
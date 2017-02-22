---
title: "拡張メニューとコマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メニュー、一般的なタスク"
  - "Vspackages にある、[menu タスク"
  - ".vsct ファイル] メニューの一般的なタスク"
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
caps.handback.revision: 49
ms.author: "gregvanl"
manager: "ghogen"
---
# 拡張メニューとコマンド
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

コマンドは、アクションとプロセスを Visual Studio に追加する方法です。 ほとんどの場合は、コマンドはメニューやツールバーに表示されます。 VSPackage プロジェクト テンプレートは、非常に基本的なコマンドを実装する方法を示します。 少々 長くなりますが、まだ基本的な実装では、次を参照してください。 [メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
 Visual Studio コマンド、メニューおよびツールバーの詳細については、次を参照してください。 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
 コマンド、メニューのおよびツールバーは、VSPackage プロジェクトの一部である .vsct ファイルで定義されます。 Visual Studio IDE およびに .vsct ファイルに関する情報を検索する [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)です。  
  
 次のトピックでは、さまざまな種類のコマンド、メニューのおよびツールバーを追加する方法について説明します。  
  
## このセクションの内容  
 [Visual Studio のメニュー バーにメニューを追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Visual Studio のメニュー バーの上部にメニューを追加する方法について説明します。  
  
 [メニュー項目にバインドのキーボード ショートカット](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 メニュー項目を \(CTRL \+ 3\) などのキーボード ショートカットを追加する方法について説明します。  
  
 [メニューのサブメニューの追加](../extensibility/adding-a-submenu-to-a-menu.md)  
 上部のメニューのサブメニューを追加する方法について説明します。  
  
 [サブメニューにリストを使用する最近のほとんどを追加します。](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 最近使用した一覧に追加する方法をについて説明します。  
  
 [ボタンの再利用可能なグループを作成します。](../extensibility/creating-reusable-groups-of-buttons.md)  
 複数のメニューで、含めることのできるように、コマンド項目をグループ化する方法について説明します。  
  
 [メニュー コマンドにアイコンを追加します。](../extensibility/adding-icons-to-menu-commands.md)  
 ツールバーとメニューの両方でコマンドにアイコンを追加する方法について説明します。  
  
 [メニュー コマンドのテキストを変更します。](../extensibility/changing-the-text-of-a-menu-command.md)  
 使用方法について説明します `TextChanges` を動的に変更するメニュー項目を有効にするフラグ。  
  
 [コマンドの外観を変更します。](../extensibility/changing-the-appearance-of-a-command.md)  
 動的に有効にする、またはコマンドを無効にする方法について説明します。  
  
 [ユーザー インターフェイスの更新](../extensibility/updating-the-user-interface.md)  
 最近の変更を反映するように、ユーザー インターフェイスの更新を強制する方法について説明します。  
  
 [メニュー コマンドのローカライズ](../extensibility/localizing-menu-commands.md)  
 メニュー コマンドをローカライズする方法について説明します。  
  
## 関連項目
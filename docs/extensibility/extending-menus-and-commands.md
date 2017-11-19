---
title: "メニューとコマンドを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: "49"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c53f836b6384968bf812ae9ae559a281fda6f13
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="extending-menus-and-commands"></a>拡張メニューとコマンド
コマンドは、アクションとプロセスを Visual Studio に追加する方法です。 ほとんどの場合は、コマンドがメニューやツールバーに表示されます。 VSPackage プロジェクト テンプレートは、非常に基本的なコマンドを実装する方法を示します。 少し長くなりますが、まだ基本的な実装では、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
 Visual Studio コマンド、メニューおよびツールバーの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)です。  
  
 コマンド、メニューのおよびツールバーは、VSPackage プロジェクトの一部である .vsct ファイルで定義されます。 Visual Studio IDE との .vsct ファイルに関する情報を見つけることができます[方法 VSPackages に追加のユーザー インターフェイス要素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)です。  
  
 次のトピックでは、さまざまな種類のコマンド、メニューのおよびツールバーを追加する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Studio のメニュー バーへのメニューの追加](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Visual Studio のメニュー バーの上部にメニューを追加する方法について説明します。  
  
 [キーボード ショートカットのメニュー項目へのバインド](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 メニュー項目を (CTRL + 3) などのキーボード ショートカットを追加する方法について説明します。  
  
 [サブメニューのメニューへの追加](../extensibility/adding-a-submenu-to-a-menu.md)  
 上部のメニューにサブメニューを追加する方法について説明します。  
  
 [最近使用した一覧のサブメニューへの追加](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 最近使用した一覧に追加する方法をについて説明します。  
  
 [再利用可能なボタンのグループの作成](../extensibility/creating-reusable-groups-of-buttons.md)  
 複数のメニューには追加するようにコマンド項目をグループ化する方法について説明します。  
  
 [メニュー コマンドへのアイコンの追加](../extensibility/adding-icons-to-menu-commands.md)  
 ツールバーとメニューの両方でのコマンドにアイコンを追加する方法について説明します。  
  
 [メニュー コマンドのテキストの変更](../extensibility/changing-the-text-of-a-menu-command.md)  
 使用方法について説明、`TextChanges`を動的に変更するメニュー項目を有効にするフラグ。  
  
 [コマンドの外観の変更](../extensibility/changing-the-appearance-of-a-command.md)  
 動的に有効にするにまたはコマンドを無効にする方法について説明します。  
  
 [ユーザー インターフェイスの更新](../extensibility/updating-the-user-interface.md)  
 最近の変更を反映するように、ユーザー インターフェイスの更新を強制する方法について説明します。  
  
 [メニュー コマンドのローカライズ](../extensibility/localizing-menu-commands.md)  
 メニュー コマンドをローカライズする方法について説明します。  
  
## <a name="related-sections"></a>関連項目
---
title: メニューとコマンドの拡張 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 50
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 158759d2511b6ba1209a045a898969fce774e0a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536447"
---
# <a name="extending-menus-and-commands"></a>メニューとコマンドの拡張
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[拡張メニューとコマンド](https://docs.microsoft.com/visualstudio/extensibility/extending-menus-and-commands)します。  
  
コマンドは、アクションとプロセスを Visual Studio に追加する方法です。 ほとんどの場合は、コマンドがメニューやツールバーに表示されます。 VSPackage プロジェクト テンプレートは、非常に基本的なコマンドを実装する方法を示します。 若干時間ですがまだ基本的な実装では、次を参照してください。[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
 Visual Studio コマンド、メニューおよびツールバーの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
 コマンド、メニューのおよびツールバーは、VSPackage プロジェクトの一部である .vsct ファイルで定義されます。 Visual Studio IDE およびで .vsct ファイルに関する情報を検索する[方法 VSPackages に追加のユーザー インターフェイス要素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)します。  
  
 次のトピックでは、さまざまな種類のコマンド、メニューのおよびツールバーを追加する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Studio のメニュー バーへのメニューの追加](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Visual Studio のメニュー バーの上部にメニューを追加する方法について説明します。  
  
 [キーボード ショートカットのメニュー項目へのバインド](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 (CTRL + 3) などのキーボード ショートカットをメニュー項目を追加する方法について説明します。  
  
 [サブメニューのメニューへの追加](../extensibility/adding-a-submenu-to-a-menu.md)  
 上部のメニューにサブメニューを追加する方法について説明します。  
  
 [最近使用した一覧のサブメニューへの追加](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 最近使用した一覧に追加する方法をについて説明します。  
  
 [再利用可能なボタンのグループの作成](../extensibility/creating-reusable-groups-of-buttons.md)  
 複数のメニューに含めることができますようにコマンド項目をグループ化する方法について説明します。  
  
 [メニュー コマンドへのアイコンの追加](../extensibility/adding-icons-to-menu-commands.md)  
 ツールバーとメニューの両方でのコマンドにアイコンを追加する方法について説明します。  
  
 [メニュー コマンドのテキストの変更](../extensibility/changing-the-text-of-a-menu-command.md)  
 使用について説明します、`TextChanges`動的に変更するメニュー項目を有効にするフラグ。  
  
 [コマンドの外観の変更](../extensibility/changing-the-appearance-of-a-command.md)  
 動的に有効または、コマンドを無効にする方法について説明します。  
  
 [ユーザー インターフェイスの更新](../extensibility/updating-the-user-interface.md)  
 最近の変更を反映するように、ユーザー インターフェイスの更新を強制する方法について説明します。  
  
 [メニュー コマンドのローカライズ](../extensibility/localizing-menu-commands.md)  
 メニュー コマンドをローカライズする方法について説明します。  
  
## <a name="related-sections"></a>関連項目


---
title: メニューとコマンドの拡張 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, common tasks
- VSPackages, menu tasks
- .vsct files, common menu tasks
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e6f5cd78709c9a4843588188494b4a70f7268742
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639751"
---
# <a name="extend-menus-and-commands"></a>メニューとコマンドを拡張します。
コマンドは、アクションとプロセスを Visual Studio に追加する方法です。 ほとんどの場合は、コマンドがメニューやツールバーに表示されます。 VSPackage プロジェクト テンプレートは、非常に基本的なコマンドを実装する方法を示します。 若干時間ですがまだ基本的な実装では、次を参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
 Visual Studio コマンド、メニューおよびツールバーの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
 コマンド、メニューのおよびツールバーがで定義されている、 *.vsct*されているファイルと VSPackage プロジェクトの一部です。 Visual Studio IDE についての情報を見つけることができます、 *.vsct*ファイル[Vspackage ではどのように追加のユーザー インターフェイス要素](../extensibility/internals/how-vspackages-add-user-interface-elements.md)します。  
  
 次のトピックでは、さまざまな種類のコマンド、メニューのおよびツールバーを追加する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Visual Studio のメニュー バー メニューに追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Visual Studio のメニュー バーの上部にメニューを追加する方法について説明します。  
  
 [キーボード ショートカットをメニュー項目にバインドします。](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 (CTRL + 3) などのキーボード ショートカットをメニュー項目を追加する方法について説明します。  
  
 [メニューにサブメニューを追加します。](../extensibility/adding-a-submenu-to-a-menu.md)  
 上部のメニューにサブメニューを追加する方法について説明します。  
  
 [最近使用した一覧のサブメニューへの追加します。](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 最近使用した一覧に追加する方法をについて説明します。  
  
 [ボタンの再利用可能なグループを作成します。](../extensibility/creating-reusable-groups-of-buttons.md)  
 複数のメニューに含めることができますようにコマンド項目をグループ化する方法について説明します。  
  
 [メニュー コマンドにアイコンを追加します。](../extensibility/adding-icons-to-menu-commands.md)  
 ツールバーとメニューの両方でのコマンドにアイコンを追加する方法について説明します。  
  
 [メニュー コマンドのテキストを変更します。](../extensibility/changing-the-text-of-a-menu-command.md)  
 使用について説明します、`TextChanges`動的に変更するメニュー項目を有効にするフラグ。  
  
 [コマンドの外観を変更します。](../extensibility/changing-the-appearance-of-a-command.md)  
 動的に有効または、コマンドを無効にする方法について説明します。  
  
 [ユーザー インターフェイスを更新します。](../extensibility/updating-the-user-interface.md)  
 最近の変更を反映するように、ユーザー インターフェイスの更新を強制する方法について説明します。  
  
 [メニュー コマンドをローカライズします。](../extensibility/localizing-menu-commands.md)  
 メニュー コマンドをローカライズする方法について説明します。  
---
title: 'ワークフロー デザイナー - 方法: ワークフロー プロジェクト (レガシ) に新しい項目を追加'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflows, adding to workflow projects
- workflows, adding new items
- state machine workflows, adding to workflow projects
- activities, adding to workflow projects
ms.assetid: 130cd83d-942d-437b-bbb5-8088ec0a6d79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d6e9607f4924057568849fd7eabd4567130dc2f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974236"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project-legacy"></a>方法: ワークフロー プロジェクトに新しい項目を追加する (レガシ)

従来の Windows ワークフロー デザイナーが Visual Studio 2010 で提供されるをターゲットと .NET Framework バージョン 3.5 または、WinFX のいずれかを使用して、ワークフロー プロジェクトを作成した後は、Windows Workflow Foundation (WF) の項目とその他の使い慣れた Visual Studio を追加することができます。項目をプロジェクト。

次の表は、ワークフロー プロジェクトに追加できる Windows Workflow Foundation 項目の一覧です。

|アイテム|説明|
|----------|-----------------|
|アクティビティ|デザイナー コード ファイル内にアクティビティ定義が含まれ、別のコード ファイル内にユーザー コードが含まれるアクティビティ。|
|アクティビティ (コード分離付き)|ワークフロー マークアップとして表記されたアクティビティ定義と、別のコード ファイル内のユーザー コード。|
|シーケンシャル ワークフロー (コード)|デザイナー コード ファイル内にワークフロー定義が含まれ、別のコード ファイル内にユーザー コードが含まれるシーケンシャル ワークフロー。|
|シーケンシャル ワークフロー (コード分離付き)|ワークフロー定義がワークフロー マークアップとして表記され、別のコード ファイル内にユーザー コードが含まれるシーケンシャル ワークフロー。|
|ステート マシンのワークフロー (コード)|デザイナー コード ファイル内にワークフロー定義が含まれ、別のコード ファイル内にユーザー コードが含まれるステート マシン ワークフロー。|
|ステート マシンのワークフロー (コード分離付き)|ワークフロー定義がワークフロー マークアップとして表記され、別のコード ファイル内にユーザー コードが含まれるステート マシン ワークフロー。|

## <a name="to-add-a-new-item-to-a-workflow-project"></a>ワークフロー プロジェクトに新しい項目を追加するには

1.  **プロジェクト** メニューのをクリックして**新しい項目の追加**です。

     **新しい項目の追加** ダイアログ ボックスが表示されます。

2.  項目を選択します。

     選択可能な Windows Workflow Foundation 項目の一覧が、上記の表に示されています。

3.  をクリックして**追加**ワークフロー プロジェクトに、項目を追加します。

## <a name="see-also"></a>関連項目

- [従来のワークフロー プロジェクトの作成](../workflow-designer/creating-legacy-workflow-projects.md)